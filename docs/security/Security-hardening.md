> If you've found this useful please consider [supporting me](https://tuxerrante.github.io/knowledge/#support-my-work)!

# Work management

* Legal responsibilities?
	* [CISO]([What Is A CISO? Their Role and Responsibilities Clearly Explained | UpGuard](https://www.upguard.com/blog/what-is-a-ciso))
	* [ISO 27001]([ISO/IEC 27001:2022 - Information security management systems](https://www.iso.org/standard/27001))
* Still Kanban style or FiFo (high risk new vulnerabilities going again on the top)?

# Dev Teams

* [Repository Mandatory Pre commit hooks](https://pre-commit.com/)
	* Static code analysis
	* Security-linter
	* Signed commits
* Platform security standard enforcement ([kyverno](https://kyverno.io/))
* Docker container scanning at build time ([Grype](https://github.com/anchore/grype)/[Trivy](https://trivy.dev/)) and runtime (Anchore)
* Runtime dependencies + licenses scan ([Dependency Track]([Dependency-Track | Software Bill of Materials (SBOM) Analysis | OWASP (dependencytrack.org)](https://dependencytrack.org/)))
* Automated dependencies updates ([Renovate]([renovatebot/renovate: Home of the Renovate CLI: Cross-platform Dependency Automation by Mend.io (github.com)](https://github.com/renovatebot/renovate)))
* Automated leaking secret scanning ([Gitleaks]([gitleaks/gitleaks: Protect and discover secrets using Gitleaks 🔑 (github.com)](https://github.com/gitleaks/gitleaks)) / [Trufflehog](https://github.com/trufflesecurity/trufflehog))
* 🔏 Only private docker images in all services

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
	* Https everywhere
	* [Spiffe]([SPIRE | CNCF](https://www.cncf.io/projects/spire/)) / Spire

## Advanced topics

* Honeypots
	* [2021 Honeypot Introduction (Cyber Security Series) (youtube.com)](https://www.youtube.com/watch?v=p1j55J2ditY&ab_channel=ElitheComputerGuy)
