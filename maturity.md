# Pipeline Security

## What are some things that can go wrong with the build pipeline?

<details>
  <summary> Think: </summary>

* Spoofing
* Tampering
* Repudiation
* Info disclosure
* Elevation of privilege

</details>

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />


## Best Practices in the Pipeline

[OWASP CI/CD Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/CI_CD_Security_Cheat_Sheet.html)

[OWASP Top 10 CI/CD Security Risks](https://owasp.org/www-project-top-10-ci-cd-security-risks/):
* [CICD-SEC-1](https://owasp.org/www-project-top-10-ci-cd-security-risks/CICD-SEC-01-Insufficient-Flow-Control-Mechanisms): Insufficient Flow Control Mechanisms
* [CICD-SEC-2](https://owasp.org/www-project-top-10-ci-cd-security-risks/CICD-SEC-02-Inadequate-Identity-And-Access-Management): Inadequate Identity and Access Management
* [CICD-SEC-3](https://owasp.org/www-project-top-10-ci-cd-security-risks/CICD-SEC-03-Dependency-Chain-Abuse): Dependency Chain Abuse
* [CICD-SEC-4](https://owasp.org/www-project-top-10-ci-cd-security-risks/CICD-SEC-04-Poisoned-Pipeline-Execution): Poisoned Pipeline Execution (PPE)
* [CICD-SEC-5](https://owasp.org/www-project-top-10-ci-cd-security-risks/CICD-SEC-05-Insufficient-PBAC): Insufficient PBAC (Pipeline-Based Access Controls)
* [CICD-SEC-6](https://owasp.org/www-project-top-10-ci-cd-security-risks/CICD-SEC-06-Insufficient-Credential-Hygiene): Insufficient Credential Hygiene
* [CICD-SEC-7](https://owasp.org/www-project-top-10-ci-cd-security-risks/CICD-SEC-07-Insecure-System-Configuration): Insecure System Configuration
* [CICD-SEC-8](https://owasp.org/www-project-top-10-ci-cd-security-risks/CICD-SEC-08-Ungoverned-Usage-of-3rd-Party-Services): Ungoverned Usage of 3rd Party Services
* [CICD-SEC-9](https://owasp.org/www-project-top-10-ci-cd-security-risks/CICD-SEC-09-Improper-Artifact-Integrity-Validation): Improper Artifact Integrity Validation
* [CICD-SEC-10](https://owasp.org/www-project-top-10-ci-cd-security-risks/CICD-SEC-10-Insufficient-Logging-And-Visibility): Insufficient Logging and Visibility

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

## Pipeline maturity and the OWASP SAMM

The [OWASP Software Assurance Maturity Model](https://owaspsamm.org) (SAMM):

* Provides a measurable way to analyze and improve an organization's software security posture
* Is a repeatable method to raise awareness and educate on how to design, develop, and deploy secure software through its self-assessment model
* Supports the complete SDLC and is technology and process agnostic.

(For help using the SAMM, see the site or contact one of the many fine [SAMM practictioners listed](https://owaspsamm.org/practitioners).)

<br />

* SAMM covers 15 security practices, including **Secure Deployment**
* SAMM divides the maturity of each practice into three levels
* Maturity actually on a continuous scale: [0.0 - 3.0]

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

## OWASP SAMM

For Secure Deployment, to achieve each level, certain practices must be getting performed:

| Level | Requirement | Activities |
|--|--|--|
| 1 | Fully documented, up-to-date, accessible deployment process.  | Formalize the deployment process and secure the tooling and processes used. |
|   | Application secrets secured and different per environment. | <p> Limit access to production secrets based on principle of least privilege. <p> Restrict developers from production secrets. |
| 2 | Automated process includes security verification. | <p> Automate the deployment process over all stages. <p> Use security verification tests. <p> Alert on vulnerabilities. <p> Keep deployment logs for defined time. |
|   | Secrets get dynamically injected during deployment. | <p> Inject from hardened stores. <p> Prevent human access to secret storage. <p> Confirm that no secrets remain in source or configuration files. <p> Log and alert any access attempts. |
| 3 | Consistently validate artifact integrity. | <p> Process automatically rolls back deployment on integrity breach, using file signatures created at build time. <p> Confirm authenticity of external software. |
|   | Practice application secret lifecycle management. | <p> Generate/synchronize application secrets using a vetted solution. <p> Application instances use unique secrets. <p> Periodically change and update secrets. |

<br /><br />

## OWASP ASVS

The ASVS also divides its standards into three levels:

**Level 1** is the bare minimum that all applications should strive for, or as a first step in a multi-phase effort or for applications do not store or handle sensitive data.

**Level 2** ensures that security controls are in place, effective, and used within the application. Appropriate for applications that handle significant business-to-business transactions, or industries where integrity is a critical facet. A Level 2 app adequately defends against most of the risks associated with software today.

**Level 3** is the highest level of ASVS verification, and is typically reserved for significant levels of security verification, such as those within the military, health and safety, critical infrastructure, etc. Organizations may require this for applications that perform critical functions, where failure could significantly impact the organization's operations. A Level 3 app adequately defends against advanced application security vulnerabilities and also demonstrates principles of good security design.

For deployment, the OWASP (ASVS) calls out the following standards:

### V10 Malicious code

Best efforts should be undertaken to ensure that the code has no inherent malicious code or unwanted functionality. This is not possible without complete access to source code, including third-party libraries.

| Min level | Standard |
|--|--|
| 1 | The application must not load or execute code from untrusted sources. |

### V14 Configuration

| Min level | Standard |
|--|--|
| 1 | Ensure all components are up to date, using a dependency checker during build. |
| 1 | Remove all unneeded features, documentation, sample applications and configurations before deployment. |
| 1 | If application assets (e.g. libraries, CSS) are hosted externally (e.g. a CDN), use Subresource Integrity (SRI) to validate the integrity of the assets. |
| 1 | Disable server and application framework debug modes in production. |
| 1 | Do not expose detailed version information of system components in HTTP responses. |
| 1 | Use HTTP security headers, e.g: Content-Type, Content Security Policy, Strict-Transport-Security. |
| 2 | Verify that third-party components come from pre-defined, trusted, and continually maintained repositories. |
| 2 | Maintain a Software Bill of Materials (SBOM) of all third-party libraries in use. |
| 2 | Sandbox third-party libraries to expose only the required behavior to the application. |
| 2 | Verify that HTTP headers added by a proxy are authenticated by the app. |


[Next slide](artifact_mgmt.md)
