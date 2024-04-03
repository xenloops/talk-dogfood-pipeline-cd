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
| 1 | Fully documented deployment processes | Formalize the deployment process and secure the used tooling and processes. |
|   |  | Limit access to production secrets. |
| 2 | Process includes security verification | Automate the deployment process over all stages and introduce sensible security verification tests. |
|   |  | Inject secrets dynamically during deployment process from hardened storages and audit all human access to them. |
| 3 | Process is fully automated with verification of all critical milestones | Automatically verify integrity of all deployed software, independently on whether it's internally or externally developed. |
|   |  | Improve the lifecycle of application secrets by regularly generating them and by ensuring proper use. |


## OWASP ASVS

Further, the OWASP (ASVS) calls out the following:
V10 Mal
V14 Configuration


[Next slide]()
