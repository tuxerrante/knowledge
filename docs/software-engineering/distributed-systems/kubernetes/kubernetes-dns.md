Not headless Services are assigned DNS A and/or AAAA records, depending on the IP family or families of the Service, with a name of the form my-svc.my-namespace.svc.cluster-domain.example. This resolves to the cluster IP of the Service. 

If the <cluster-ip> is an IPv4 address, an A record of the following form must exist 

`<service>.<ns>.svc.<zone>. <ttl> IN A <cluster-ip> `

[Records for External Name Services](https://github.com/kubernetes/dns/blob/master/docs/specification.md#25---records-for-external-name-services)

Given a Service named <service> in Namespace <ns> with ExternalName `<extname>`, a CNAME record named `<service>.<ns>.svc.<zone>` pointing to `<extname>` must exist. 

Record Format: 
`<service>.<ns>.svc.<zone>. <ttl> IN CNAME <extname>` 

By default AKS uses CoreDNS for tcp and udp internal DNS resolution. This configuration is easily editable through a configmap 

These resolution policies are specified in the dnsPolicy field of a Pod Spec. 

- "Default": The Pod inherits the name resolution configuration from the node that the Pods run on. See [related discussion](https://kubernetes.io/docs/tasks/administer-cluster/dns-custom-nameservers/) for more details. 
    
- "ClusterFirst": Any DNS query that does not match the configured cluster domain suffix is forwarded to an upstream nameserver by the DNS server. See [related discussion](https://kubernetes.io/docs/tasks/administer-cluster/dns-custom-nameservers/) for details on how DNS queries are handled in those cases. 
    

➜ kubectl describe configmaps --namespace=kube-system coredns 

```bash
.:53 {                          # Listen on port 53 for all zones (.)
    errors                      # Enable error logging
    ready                       # Enable readiness probe
    health {                    # Enable health checks
      lameduck 5s # Delay shutdown by 5 seconds to allow in-flight requests to complete
    }
    kubernetes cluster.local in-addr.arpa ip6.arpa {  # Kubernetes plugin for service discovery in the cluster
      pods insecure             # Use insecure mode for pod DNS names
      fallthrough in-addr.arpa ip6.arpa  # Continue to the next plugin if no match is found
      ttl 30                    # Set the DNS record TTL to 30 seconds
    }
    prometheus :9153            # Enable Prometheus metrics on port 9153
    forward . /etc/resolv.conf  # Forward all other DNS queries to the nameservers in /etc/resolv.conf
}
```

## What is CoreDNS? 

CoreDNS is a modern, flexible, and extensible DNS server designed to provide DNS and service discovery functionalities. [It is built with a modular architecture, allowing it to be easily extended with plugins to support various use cases](https://kubernetes.io/docs/tasks/administer-cluster/coredns/).  

CoreDNS can serve as a DNS server for traditional DNS records, as well as for service discovery in cloud-native environments like Kubernetes. 

CoreDNS operates by listening for DNS queries on specified ports and resolving these queries based on its configuration. It can act as both a resolver and a forwarder: 

- Resolver: CoreDNS can resolve DNS queries using its internal database of DNS records. 
    
- Forwarder: If CoreDNS does not have the answer to a query, it can forward the query to upstream DNS servers and return the response to the client. 
    

CoreDNS uses a configuration file called Corefile to define its behavior. This file specifies the plugins to be used and their configurations. Plugins can handle various tasks such as caching, load balancing, health checks, and more. 

In Kubernetes, CoreDNS is the default DNS service starting from version 1.13. It replaces the older kube-dns service and provides DNS resolution for services and pods within the cluster.  

Here’s how CoreDNS integrates with Kubernetes: 

1. Deployment: CoreDNS is deployed as a Kubernetes Deployment with multiple replicas for high availability. [It runs in the kube-system namespace and is exposed via a Kubernetes Service named kube-dns](https://kubernetes.io/docs/tasks/administer-cluster/coredns/). 
    
2. Service Discovery: When a pod in the Kubernetes cluster needs to communicate with another service, it sends a DNS query to CoreDNS. CoreDNS resolves the query by mapping the service name to the corresponding IP address using its internal records. 
    
3. Configuration: The CoreDNS configuration in Kubernetes is managed through a ConfigMap. This ConfigMap contains the Corefile, which defines how CoreDNS should handle DNS queries. The kubernetes plugin in the Corefile is specifically designed to handle DNS queries for Kubernetes services and pods. 
    
4. Performance and Monitoring: CoreDNS can be configured to collect metrics using plugins like Prometheus. These metrics can help monitor DNS performance, such as query latency, cache hit rates, and resource usage [[using-coredns-effectively-kubernetes]](https://www.infracloud.io/blogs/using-coredns-effectively-kubernetes/). 
    
5. Scalability: CoreDNS is designed to scale with the Kubernetes cluster. It can handle a large number of DNS queries efficiently and can be tuned to optimize resource usage. 
    

More info on the [CoreDNS kubernetes plugin here](https://coredns.io/plugins/kubernetes/). 

Looking inside the CoreDNS deployment we can see it is mounted there  

```yaml
# kubectl --namespace=kube-system describe deploy coredns
Name:                   coredns
Namespace:              kube-system
Labels:                 addonmanager.kubernetes.io/mode=Reconcile
                        k8s-app=kube-dns
                        kubernetes.azure.com/managedby=aks
                        kubernetes.io/cluster-service=true
                        kubernetes.io/name=CoreDNS
                        version=v20
Selector:  k8s-app=kube-dns,version=v20
Replicas:  4 desired | 4 updated | 4 total | 4 available | 0 unavailable
Pod Template:
    Labels:
	  k8s-app=kube-dns
	  kubernetes.azure.com/managedby=aks
	  kubernetes.io/cluster-service=true
  Service-Account:  coredns
  Containers:
   coredns:
    Image:       mcr.microsoft.com/oss/kubernetes/coredns:v1.9.4-hotfix.20240704
    Ports:       53/UDP, 53/TCP, 9153/TCP
    Host Ports:  0/UDP, 0/TCP, 0/TCP
    Args:
      -conf
      /etc/coredns/Corefile
...      
    Mounts:
      /etc/coredns from config-volume (ro)
      /etc/coredns/custom from custom-config-volume (ro)
      /tmp from tmp (rw)
  Volumes:
   config-volume:
    Type:      ConfigMap (a volume populated by a ConfigMap)
    Name:      coredns
    Optional:  false
```

So any of the DNS resolving requests targeted on port 53 will be solved by coredns server itself if the target was in the same cluster zone (eg: [data.test.svc.cluster.local](https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/))  while the rest will be redirected to the host [resolv.conf](https://www.man7.org/linux/man-pages/man5/resolv.conf.5.html) which is not much used today. 

## Differences Between kube-dns, CoreDNS, and kube-proxy 

- Function: kube-dns is the traditional DNS service used in Kubernetes for service discovery. 
    
- Components: It typically includes a DNS server (dnsmasq), a DNS caching layer, and a health check. 
    
- Usage: kube-dns resolves DNS names for services and pods within the cluster. 
    

```yaml
spec: 
  ports: 
    - name: dns 
      protocol: UDP 
      port: 53 
      targetPort: 53 
    - name: dns-tcp 
      protocol: TCP 
      port: 53
      targetPort: 53 
  selector: 
    k8s-app: kube-dns 
  clusterIP: 10.X.Y.Z
```

CoreDNS Deployment 

- Function: CoreDNS is a more flexible and extensible DNS server that can replace kube-dns. 
    
- Components: CoreDNS uses a configuration file (Corefile) to define its behavior, including plugins for various functionalities. 
    
- Usage: CoreDNS can handle DNS-based service discovery, metrics, health checks, and more. It is the default DNS server in newer Kubernetes versions due to its modularity and performance. 
    

kube-proxy DaemonSet 

- Function: kube-proxy is responsible for maintaining network rules on nodes to allow communication to services. 
    
- Components: It runs as a daemonset on each node and uses iptables or IPVS to manage routing rules. 
    
- Usage: kube-proxy routes traffic to the appropriate backend pods for a given service, ensuring that requests reach the correct destination. 
    

## Inspecting DNS records with [agnhost](https://github.com/kubernetes/kubernetes/tree/master/test/images/agnhost)
 ```bash
 kubectl run agnhost --namespace dev-testing --image=registry.k8s.io/e2e-test-images/agnhost:2.40 --overrides='{"spec":{"containers":[{"name":"agnhost","image":"registry.k8s.io/e2e-test-images/agnhost:2.40","command":["sleep","3600"],"securityContext":{"privileged":true},"volumeMounts":[{"name":"host-volume","mountPath":"/host","readOnly":true}]}],"volumes":[{"name":"host-volume","hostPath":{"path":"/"}}],"restartPolicy":"Never"}}'

# It will output the host's configured DNS servers, separated by commas
❯ kubectl exec -n dev-testing agnhost -- /agnhost dns-server-list
10.X.Y.Z  (NDR: kube-dns service IP)

❯ kubectl exec -n dev-testing agnhost -- nslookup mapim.dev-mapim.svc.cluster.local
Server:         10.X.Y.Z
Address:        10.X.Y.Z#53
Name:   mapim.dev-mapim.svc.cluster.local
Address: 10.A.B.C

➜ kubectl exec -n dev-testing agnhost -- /agnhost dns-suffix
dev-testing.svc.cluster.local,svc.cluster.local,cluster.local,paxg3pivipuujon3aq5cuajlnb.ax.internal.cloudapp.net

➜ kubectl exec -n dev-testing agnhost -- /agnhost etc-hosts
# Kubernetes-managed hosts file.
127.0.0.1       localhost
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
fe00::0 ip6-mcastprefix
fe00::1 ip6-allnodes
fe00::2 ip6-allrouters

10.0.12.59      agnhost-pod
 ```

# AKS Peering 
Here’s a short guide on setting up network peering between two Azure Kubernetes Service (AKS) clusters

### Setting Up Network Peering Between Two AKS Clusters
#### Step 1: Create Two AKS Clusters

1. **Create Resource Groups**:
    
    ```bash
    az group create --name ResourceGroup1 --location eastus
    az group create --name ResourceGroup2 --location westus
    ```
    
2. **Create AKS Clusters**:
    
    ```bash
    az aks create --resource-group ResourceGroup1 --name AKSCluster1 --node-count 1 --enable-addons monitoring --generate-ssh-keys
    az aks create --resource-group ResourceGroup2 --name AKSCluster2 --node-count 1 --enable-addons monitoring --generate-ssh-keys
    ```
    

#### Step 2: Set Up Virtual Network Peering

1. **Get Virtual Network IDs**:
    
    ```bash
    VNET1_ID=$(az network vnet show --resource-group MC_ResourceGroup1_AKSCluster1_eastus --name aks-vnet-123456 --query id --output tsv)
    VNET2_ID=$(az network vnet show --resource-group MC_ResourceGroup2_AKSCluster2_westus --name aks-vnet-654321 --query id --output tsv)
    ```
    
2. **Create Peering from VNet1 to VNet2**:
    
    ```bash
    az network vnet peering create --name VNet1ToVNet2 --resource-group MC_ResourceGroup1_AKSCluster1_eastus --vnet-name aks-vnet-123456 --remote-vnet $VNET2_ID --allow-vnet-access
    ```
    
3. **Create Peering from VNet2 to VNet1**:
    
    ```bash
    az network vnet peering create --name VNet2ToVNet1 --resource-group MC_ResourceGroup2_AKSCluster2_westus --vnet-name aks-vnet-654321 --remote-vnet $VNET1_ID --allow-vnet-access
    ```
    

#### Step 3: Configure ExternalName Kubernetes Services

1. **Create ExternalName Service in AKSCluster1**:
    
    ```yaml
    apiVersion: v1
    kind: Service
    metadata:
      name: externalname-service
    spec:
      type: ExternalName
      externalName: myservice.example.com
    ```
    
    Apply the configuration:
    
    ```bash
    kubectl apply -f externalname-service.yaml
    ```
    

#### Step 4: Assign Roles for Service Principal
TODO


# REFERENCES: 

- [Customize CoreDNS for Azure Kubernetes Service (AKS) - Azure Kubernetes Service | Microsoft Learn](https://learn.microsoft.com/en-us/azure/aks/coredns-custom) 
    
- [https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/](https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/) 
    
- [dns/docs/specification.md at master · kubernetes/dns · GitHub](https://github.com/kubernetes/dns/blob/master/docs/specification.md) 
    
- [Debugging DNS Resolution | Kubernetes](https://kubernetes.io/docs/tasks/administer-cluster/dns-debugging-resolution/) 
    
- [https://github.com/kubernetes/kubernetes/tree/master/test/images/agnhost](https://github.com/kubernetes/kubernetes/tree/master/test/images/agnhost)