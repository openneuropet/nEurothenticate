# nEurothenticate

nEurothenticate is a FAIR platform built by Open NeuroPET. It is a gateway for public and secured brain imaging data sharing. Public means datasets metadata are publicly available making data Findable, while maintaining access control. Users and institutions are identified allowing to share data using data user agreements making data Accessible. The platform uses curated data following the [Brain Imaging Data Structure](https://bids.neuroimaging.io/), making data Interoperable and Reusable.

## Accessing data with nEurothenticate

### Register 

As a user, you and your institution must register. This is a necessary step to check your ID and allowing an institutional Data Protection Impact Assessement (i.e. having a small document showing the data will be shared privately and securely with you on your institution server). Thse steps are the basis for accessing EU data. Having your ID, we can transfer data using an [Data User Agreement](https://open-brain-consent.readthedocs.io/en/stable/gdpr/data_user_agreement.html) and, if non-EU based, an additional [Standard Contractual Clauses Agreement](https://ec.europa.eu/info/law/law-topic/data-protection/international-dimension-data-protection/standard-contractual-clauses-scc_en).   

### Direct and Third party access

No data are visible from nEurothenticate, but metadata (information about datasets) are visible. After registration you will be able to obtain a temporary key to access data. This can also be gained via a 3rd party: OpenNeuro, CONP or EBRAINS. Download can only be done (for now) using our partner, [DataLad](https://www.datalad.org/).

## Deposit data with nEurothenticate

### Direct deposit

You can upload data curated using the [Brain Imaging Data Structure](https://bids.neuroimaging.io/), and filling a few additional information, along with a [Data User Agreement](https://open-brain-consent.readthedocs.io/en/stable/gdpr/data_user_agreement.html). It is essential you create a DUA that respects your national regulation. As part of our pay for services, we can also curate the data for you or provide private data sharing.

#### What happen to your data after deposit?

Data are checked, metadata enriched and pushed to EU restricted Cloud (Microsoft Azure) along the metadata using a jsonld file using [schema.org](https://schema.org/). Thanks to [DataLad](https://www.datalad.org/) your data are visible and accessible worldwide, providing users are identified within nEurothenticate.
