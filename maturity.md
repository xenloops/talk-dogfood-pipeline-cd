# Pipeline maturity and the OWASP SAMM

The [OWASP Software Assurance Maturity Model](https://owaspsamm.org) (SAMM):

* Provides a measurable way to analyze and improve an organization's software security posture
* Is a repeatable method to raise awareness and educate on how to design, develop, and deploy secure software through its self-assessment model
* Supports the complete SDLC and is technology and process agnostic.

(For help using the SAMM, see the site or contact one of the many fine [SAMM practictioners listed](https://owaspsamm.org/practitioners).)

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

* SAMM covers 15 security practices, including **Secure Deployment**
* SAMM divides the maturity of each practice into three levels
* Maturity acually on a continuous scale: [0.0 - 3.0]


For Secure Deployment, to achieve each level, certain practices must be getting performed:

| Level | Requirement | Activities |
|--|--|--|
| 1 | Fully documented, up-to-date, accessible deployment process.  | Formalize the deployment process and secure the used tooling and processes. |
|   | Application secrets secured and different per environment. | Limit access to production secrets based on principle of least privilege. Restrict developers from production secrets. |
| 2 | Automated process includes security verification. | Automate the deployment process over all stages. Use security verification tests. Alert on vulnerabilities. Keep deployment logs for defined time. |
|   | Secrets get dynamically injected during deployment. | Inject from hardened stores. Prevent human access to secret storage. Confirm that no secrets remain in source or configuration files. Log and alert any access attempts. |
| 3 | Consistently validate artifact integrity. | Process automatically rolls back deployment on integrity breach, using file signatures created at build time. Confirm authenticity of external software. |
|   | Practice application secret lifecycle management. | Generate/synchronize application secrets using a vetted solution. Application instances use unique secrets. Periodically change and update secrets. |


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
| 1 | The application must not load or execute code from untrusted sources, such as modules, plugins, code, or libraries. |

### V14 Configuration

| Min level | Standard |
|--|--|
| 1 | Ensure all components are up to date, preferably using a dependency checker during build or compile time. |
| 1 | Remove all unneeded features, documentation, sample applications and configurations before deployment. |
| 1 | If application assets (e.g. JavaScript libraries, CSS, or web fonts) are hosted externally (e.g. a CDN), Subresource Integrity (SRI) is used to validate the integrity of the asset. |
| 1 | Verify that third party components come from pre-defined, trusted, and continually maintained repositories. |
| 1 | Maintain a Software Bill of Materials (SBOM) of all third party libraries in use. |

[Next slide]()
