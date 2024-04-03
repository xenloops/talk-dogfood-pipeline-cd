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

Further, the OWASP (ASVS) calls out the following:
V10 Mal
V14 Configuration


[Next slide]()
