# nEurothenticate

nEurothenticate is the platform built for Open NeuroPET, it is a gateway for secured data sharing.

## Accessing data with nEurothenticate

### Register 

As a user you can register, which implies we will check your ID which is the basis for accessing EU data. Having your ID, we can transfer data using an [Data User Agreement](https://open-brain-consent.readthedocs.io/en/stable/gdpr/data_user_agreement.html) and, if non-EU based, an additional [Standard Contractual Clauses Agreement](https://ec.europa.eu/info/law/law-topic/data-protection/international-dimension-data-protection/standard-contractual-clauses-scc_en).   

As a user, you can also register your institution and or HPC - which is useful if you plan to download the data or process them on a specific HPC platform. Information about the data protection officer need to be filled in as one need to ensure the IT is secured - see [Data Protection Impact Assessmement](https://gdpr.eu/data-protection-impact-assessment-template/), primarily to ensure data cannot be leaked. 

### Third party access

No data are visible from nEurothenticate, and access must be gained via a 3rd party: OpenNeuro, EBRAINS or BrainLife.


## Deposit data with nEurothenticate

### Direct deposit

You can upload data curated using the [Brain Imaging Data Structure](https://bids.neuroimaging.io/), and filling a few additional information, along with a [Data User Agreement](https://open-brain-consent.readthedocs.io/en/stable/gdpr/data_user_agreement.html). It is essential you create a DUA that respects your national regulation. 

#### What happen to your data?

Data are checked and pushed to EU restricted Google Cloud along the metadata using a jsonld file using [schema.org](https://schema.org/). Thanks to [DataLad](https://www.datalad.org/) your data are visible and accessible worldwide, providing users are identified within nEurothenticate.


### Third party deposit

Using the same mechanism as above, data can be deposite via the OpenNeuro portal.
