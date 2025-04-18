## Bell-LaPadula
Confidentiality focused.
- *no reads up*
- no write down
- not designed to handle file-sharing.

## Biba
Integrity
- "no read down": a higher integrity subject should not read from a lower integrity subject
- “no write up”: a lower integrity subject should not write to a higher integrity object.

## Clark-Wilson 
- **Constrained Data Item (CDI)**: data type whose integrity we want to preserve.
- **Unconstrained Data Item (UDI)**


## Goguen-Meseguer
[Goguen-Meseguer ](https://www.cs.purdue.edu/homes/ninghui/readings/AccessControl/goguen_meseguer_82.pdf) distinguish between a security **policy**, which defines the security requirements for a given system, and the system itself, which may be represented by a model.

also known as the Noninterference model, is a strict multilevel security policy model designed to ensure that actions at one security level do not interfere with or affect actions at another level. Here are the key points:

1. **Non-interference Principle**: The core idea is that actions performed by users at a higher security level should not influence what users at a lower security level can observe. This ensures that sensitive information does not leak to unauthorized users
2. **Inputs and Outputs**: The model treats a computer system as a machine with inputs and outputs. It ensures that the outputs seen by users at a lower security level are not affected by inputs from higher security levels    
3. **Formal Security Policies**: The model provides a formal framework for specifying and verifying security policies. It supports rigorous treatment of information flow and helps in proving that a given system satisfies a given security policy


## ISO/IEC 19249
### Architectural Principles 

1. **Domain Separation**: Isolate different functional areas (applications, data, policies...) to limit the impact of potential compromises. [[#Goguen-Meseguer]]
2. **Layering**: Organize the system into layers to improve management and security (e.g.: OSI model).
3. **Encapsulation**: Hide the internal details of components to reduce unwanted interactions.
4. **Redundancy**: Implement duplicate components to ensure system availability and resilience.
5. **Virtualization**: Use virtualization technologies to isolate and protect resources.

### Security Design Principles

1. **Least Privilege**: Assign users and processes only the permissions strictly necessary.
2. **Minimize Attack Surface**: Reduce the number of vulnerable points in the system.
3. **Centralized Parameter Validation**: Control and validate input data at a single point.
4. **Defense in Depth**: Implement multiple layers of security to protect the system.
5. **Separation of Duties**: Divide responsibilities among multiple people or processes to prevent abuse.

### Integration with Modern DevOps Practices

Modern DevOps practices can further enhance these principles:

- **Automation**: Use tools like Jenkins, Docker, and Kubernetes to automate deployment and application management, reducing human error and improving consistency.
- **Continuous Integration/Continuous Deployment (CI/CD)**: Implement CI/CD pipelines to ensure that every code change is tested and deployed quickly and securely.
- **Infrastructure as Code (IaC)**: Use tools like Terraform and Ansible to manage infrastructure as code, improving traceability and reproducibility of configurations.
- **Monitoring and Logging**: Implement monitoring and logging solutions like Prometheus and ELK Stack to detect and respond quickly to security incidents.
- **Collaboration and Communication**: Promote a culture of collaboration between development, security, and operations teams to ensure that security practices are integrated at every stage of the development lifecycle.

## Zero Trust VS Trust but verify
**Trust but Verify**: This principle teaches that we should always verify even when we trust an entity and its behaviour. This requires automated security mechanisms, such as proxy, intrusion detection, and intrusion prevention systems.

**Zero Trust**: This principle treats trust as a vulnerability, and consequently, it caters to insider-related threats. Zero trust does not grant trust to a device based on its location or ownership.


## Vulnerabilities and Risks
- **Vulnerability**: Vulnerable means susceptible to attack or damage. In information security, a vulnerability is a weakness.
- **Threat**: A threat is a potential danger associated with this weakness or vulnerability.
- **Risk**: The risk is concerned with the likelihood of a threat actor exploiting a vulnerability and the consequent impact on the business.
