
[Kubernetes-API in Kubernetes | ANOTE.DEV](https://anote.dev/api-groups-in-kubernetes/)  
[The Kubernetes API | Kubernetes](https://kubernetes.io/docs/concepts/overview/kubernetes-api/)  
[Kubernetes API Reference Docs](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.27/)

kubectl get \--raw /apis/discovery.k8s.io/v1 |jq '.' |less  
kubectl get \--raw /apis/apps/v1 |jq '.resources' |less  
kubectl get \--raw /apis/apps/v1/deployments |jq '.items\[\]' |less

kubectl get \--raw /api/v1/nodes |jq '.items' |less  
kubectl get \--raw /api/v1/namespaces |jq '.items\[\].metadata.name' |less

kubectl api-versions

2018 [Introducing client-go version 6 | Kubernetes](https://kubernetes.io/blog/2018/01/introducing-client-go-version-6/)

[Understanding the Kubernetes Resource Model and Controller Pattern](https://www.youtube.com/watch?v=J0n4n2RtbGs)  
[Writing a Kubernetes Controller | Rawkode Live \- YouTube](https://www.youtube.com/watch?v=RLpzsAQtZ7M\&ab\_channel=RawkodeAcademy)

[**Tutorial: Building CronJob \- The Kubebuilder Book**](https://book.kubebuilder.io/cronjob-tutorial/cronjob-tutorial.html)

[Dynamic Admission Control | Kubernetes](https://kubernetes.io/docs/reference/access-authn-authz/extensible-admission-controllers/\#admission-webhooks)

## Code PKG

[clientgo](https://pkg.go.dev/k8s.io/client-go\#section-readme)

- [Scheme](https://pkg.go.dev/k8s.io/client-go@v0.27.1/kubernetes/scheme\#pkg-overview)  a registry to map (serialize) go type from apis (Group Version Kind)   
- [Informers](https://pkg.go.dev/k8s.io/client-go@v0.27.1/informers) in memory cache store syncing every 30 s  
  You get a Resource from a shared informer as a read only cache entry, so you need to map it (deepCopy) to an Object before modification  
  - listers  
  - watchers  
- [workqueue package \- k8s.io/client-go/util/workqueue \- Go Packages](https://pkg.go.dev/k8s.io/client-go/util/workqueue)

Runtime Object [runtime package \- k8s.io/apimachinery/pkg/runtime \- Go Packages](https://pkg.go.dev/k8s.io/apimachinery/pkg/runtime\#Object)  
encode the type of an API to a Schema

RestMapping [meta package \- k8s.io/apimachinery/pkg/api/meta \- Go Packages](https://pkg.go.dev/k8s.io/apimachinery/pkg/api/meta\#RESTMapping)

[OpenAPI-Specification/3.1.0.md at main · OAI/OpenAPI-Specification (github.com)](https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.1.0.md\#infoObject)

[kubernetes/sample-apiserver: Reference implementation of an apiserver for a custom Kubernetes API. (github.com)](https://github.com/kubernetes/sample-apiserver)

Controller  
[Kubernetes Deep Dive: Code Generation for CustomResources (redhat.com)](https://cloud.redhat.com/blog/kubernetes-deep-dive-code-generation-customresources)  
[kubernetes/sample-controller: Repository for sample controller. Complements sample-apiserver (github.com)](https://github.com/kubernetes/sample-controller)

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[**KUBEBUILDER**](https://book.kubebuilder.io/quick-start.html)

\- batch instead of batch.tutorial..?  
[https://github.com/kubernetes-sigs/kubebuilder/blob/master/docs/book/src/cronjob-tutorial/testdata/project/internal/controller/cronjob\_controller.go\#L79](https://github.com/kubernetes-sigs/kubebuilder/blob/master/docs/book/src/cronjob-tutorial/testdata/project/internal/controller/cronjob\_controller.go\#L79)

\- Why to import multiple loggers?  
controller: "sigs.k8s.io/controller-runtime/pkg/log"  
main: "sigs.k8s.io/controller-runtime/pkg/log/zap"

zap is used to customize and flag the logging interface provided by logr, so you'll need to import both libraries in main, while zap or klog should be enough in a project module  
[https://sdk.operatorframework.io/docs/building-operators/golang/references/logging/](https://sdk.operatorframework.io/docs/building-operators/golang/references/logging/)

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

## SIG meetings

[SIG API Machinery Meetings \- YouTube](https://www.youtube.com/playlist?list=PL69nYSiGNLP21oW3hbLyjjj4XhrwKxH2R)

## Real implementations

[MongoDB Community Kubernetes Operator](https://github.com/mongodb/mongodb-kubernetes-operator)  
[Go Operator Tutorial | Operator SDK (operatorframework.io)](https://sdk.operatorframework.io/docs/building-operators/golang/tutorial/\#create-a-new-api-and-controller)

Questions  
Why /api/v1 and /apis/apps/v1   
