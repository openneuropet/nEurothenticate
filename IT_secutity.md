# IT security

## Risk management (ISO 27005 and NIST 800-39)

1. identify assets, risks and threats
2. asses risk 
3. prioritize risk
4. treat risks --> Avoid / Control / Accept / Transfer

A risk occurs following a threat because of a vulnerability of an asset. Threats are hardware, software issues and failures, etc. There is also criminal threats, attacks on the IT systems.

What is the *risk appetite* of the organization? which should align more-or less with IT but needs to be explicitly stated. *Risk tolerance* is a statement about the accepted loss, often in terms of money. For measuring risk tolerance in IT, qualitative and quantitative mettrics have been developped, and should fit with the organization decision model. *Residual risk* is what is left after mitigation.

The severity of a risk is it's likelihood x impact. Something likely with mno impact isn't severe and the reverse is true. There must be a **risk register**, a record of identify risks (date and ID, category, risk level, description, impact, score/rating, mitigation, done/to do/left as is).

### Asses risk

A list of risk can be found at see [NST-SP 800-30](https://www.nist.gov/privacy-framework/nist-sp-800-30)

*Qualitative assessment*. It is a Lickert-scale type approach, usual for quick decisions contrasting likelihood and impact.

|likelihood/impact |very low |low |medium |high |very high |
|-                 |:-:      |:-: |:-:    |:-:  |:-:       |
|very likely       |         |    |       |     |          |
|likely            |         |    |       |     |          |
|possibæle         |         |    |       |     |          |
|unlikely          |         |    |       |     |          |
|rare              |         |    |       |     |          |

*Quantitative metrics* Relies often on the Factor Analysis of Information Risk (FAIR) framework, reporting on metrics such as Annuallize Rate of Occurance and Annual loss expectancy

### Treat risk

Avoid - especially for high impact - liability cases 
Control - reduce risk (lower the likelihood)
Accept - allows based on severity
Transfer - out sourcing when possible (share responsability, lowering liability)

## Security triad --> hexad

            Confidentiality 
                    |
                |-    -|
            |-           -| 
          Data -------  Data
        Integriity   Availability
    (+ authenticity)
       (+ control)
       (+ utility)


 ## Roles and responsabilities

 Asset owner - keep system running and decide on proposed procedures.
 IT team: (1) control operators check what is going on (2) conpliance team knows the laws, regulations and best practices (3) internal audits allows to ensure reports for control operators work.

## Information Security Management System

ISO 27001 Information Security Management, lay down requirements for ISMS
ISO 27005 Information Security Risk Management
NISP SP 800-39 Managing Informatiom Security Risk

### Governance, Risk, and Compliance (GRC) tools.

Start with a spreadsheet to establish workflow. GRC tools are expensive in terms of time and money.  

### Options for simple security

Single sign-on accounts, i.e. a single place where each user has an account to access IT, add usual security tips about strong password and 2AF. Servers and Cloud usage. On premisses servers are rarely fully up-to-date firmware or sofware wise leading to high vulnerability to cyber-attack.  

Minumum Viable Approach -- consider the technique that can be quickly be deployed at low cost leading to acceptable residual risk. Larger solution may be considered later.

Phishing to attack email account and get people password is the most common. Multifactor authotenfication must be in place.


