> If you've found this useful please consider [supporting me](https://tuxerrante.github.io/knowledge/#support-my-work)!

These notes are intended for a cloud native friendly, enterprise company.
# Work management

* Legal responsibilities?
	* [CISO]([What Is A CISO? Their Role and Responsibilities Clearly Explained | UpGuard](https://www.upguard.com/blog/what-is-a-ciso))
	* [ISO 27001]([ISO/IEC 27001:2022 - Information security management systems](https://www.iso.org/standard/27001))

- Kanban style or FiFo (high risk new vulnerabilities going again on the top)?

[Cloud Native Security Whitepaper | CNCF TAG Security](https://tag-security.cncf.io/community/resources/security-whitepaper/v2/cloud-native-security-whitepaper/)

# Dev Teams

* [Repository Mandatory Pre commit hooks](https://pre-commit.com/)
	* Static code analysis
	* Security-linter
	* Signed commits
* Docker container scanning at build time ([Grype](https://github.com/anchore/grype)/[Trivy](https://trivy.dev/)) and runtime (Anchore)
* Automated dependencies updates ([Renovate]([renovatebot/renovate: Home of the Renovate CLI: Cross-platform Dependency Automation by Mend.io (github.com)](https://github.com/renovatebot/renovate)))
* Automated leaking secret scanning ([Gitleaks]([gitleaks/gitleaks: Protect and discover secrets using Gitleaks 🔑 (github.com)](https://github.com/gitleaks/gitleaks)) / [Trufflehog](https://github.com/trufflesecurity/trufflehog))
* 🔏 Only private docker images in all services based on multi-stage images configured from scratch or Alpine
* [OWASP API Security Top 10 Overview & Best Practices | F5](https://www.f5.com/glossary/owasp-api-security-top-10)


# People

Devices:
	- Automatic updates
	- Certified in EU,
	- No apps from outside marketplace,
	- Enforce certificates with 2FA

Management & VP:
- periodical smartphone and laptop reset
- Management: physical access key to login to VPN
- Social networks
	- No public profiles
	- No apps from non democratic countries

# Processes

* Automated penetration test pipelines
* Weekly [Cis Benchmark]([CIS Benchmarks (cisecurity.org)](https://www.cisecurity.org/cis-benchmarks))
* Quarterly [Well architected Framework]([Azure Well-Architected Framework review for Azure Kubernetes Service (AKS) - Microsoft Azure Well-Architected Framework | Microsoft Learn](https://learn.microsoft.com/en-us/azure/well-architected/service-guides/azure-kubernetes-service)) review
* Continuous Chaos engineering ([Litmus]([LitmusChaos - Open Source Chaos Engineering Platform](https://litmuschaos.io/)))
* Zero trust architecture
	* [Seven zero trust rules for Kubernetes | CNCF](https://www.cncf.io/blog/2022/11/04/seven-zero-trust-rules-for-kubernetes/)
	* Https everywhere
	* [Spiffe]([SPIRE | CNCF](https://www.cncf.io/projects/spire/)) / Spire

# Ops

**Dashboard**:
- **Grafana** is an open-source analytics and monitoring platform. It integrates seamlessly with Prometheus to visualize metrics. You can create dashboards to monitor the health and performance of your AKS clusters.
- Kibana

**Logs**:
- **OpenTelemetry**: a unified approach to collecting metrics, logs, and traces. It’s an observability framework that supports multiple backends, including Prometheus and Jaeger ([logz](https://logz.io/blog/open-source-monitoring-tools/)).
- **Fluentd**: For log aggregation, Fluentd can be used to collect and forward logs to various destinations, including Elasticsearch and [Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/containers/monitor-kubernetes).

**Metrics**:
- **Prometheus** is a powerful open-source monitoring and alerting toolkit. It can scrape metrics from your AKS clusters and store them in a time-series database. You can set up Prometheus to monitor various metrics from your Kubernetes environment.

**Traces**:
- [Jaeger](https://www.jaegertracing.io/) is an open-source tool for tracing and monitoring microservices. It helps you understand the performance of your microservices by providing end-to-end distributed tracing. You can deploy Jaeger in your AKS cluster to collect and visualize traces.

**Alerts**:
- Site 24x7
- Alertmanager works with Prometheus to handle alerts. It can route alerts to different receivers like email, Slack, MS Teams, or other notification systems. You can configure Alertmanager to manage and silence alerts based on your requirements.
	- [prometheus-msteams/prometheus-msteams: Forward Prometheus Alert Manager notifications to Microsoft Teams. (github.com)](https://github.com/prometheus-msteams/prometheus-msteams)

- Platform security standard enforcement ([kyverno](https://kyverno.io/))
- Runtime dependencies + licenses scan ([Dependency Track]([Dependency-Track | Software Bill of Materials (SBOM) Analysis | OWASP (dependencytrack.org)](https://dependencytrack.org/)))
## Kubernetes specific configurations:
- External Secrets Operator
	- [Introduction - External Secrets Operator (external-secrets.io)](https://external-secrets.io/latest/)
- [K8S Network policies]([Network Policies | Kubernetes](https://kubernetes.io/docs/concepts/services-networking/network-policies/))
- [RBAC based service accounts bound to AD users]([Use Microsoft Entra ID and Kubernetes RBAC for clusters - Azure Kubernetes Service | Microsoft Learn](https://learn.microsoft.com/en-us/azure/aks/azure-ad-rbac?tabs=portal))
- 
## Advanced topics

* Honeypots
	* [2021 Honeypot Introduction (Cyber Security Series) (youtube.com)](https://www.youtube.com/watch?v=p1j55J2ditY&ab_channel=ElitheComputerGuy)

# IT
- VPN
- Firewalls
- VNet
- ...