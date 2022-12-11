# A quick review of Azure for OpenNeuroPET

## Usage

Storing files for distributed access.

## Storage

Data replication using RA-GRS read access geo-redondant storage with copies in EU. RA ensures data can be read from any of the two paired-servers.

Every object has a URL e.g. http://mystorageaccount.blob.core.windows.net or http://mystorageaccount.file.core.windows.net

Containers act as folders, all files are stored into blobs. There is an unlimited number of containers which have unlimited number of blobs. This is an ideal scenario using one container per dataset. 

Data can be stored as hot, cool or archived - with cost of access vs storage being in opposite directions: hot is cheap access expensive storage, archived is expensive access. The most likely scenario is to use cool storage for most datasets, but it is possible to switch between storage 'tier' at any time. There is also a blob life cycle policy allowing to create rules for storage tier applying rules daily, thus optimizing cost (move anyfiles not touched for 30 days to cool).

### What are blobs

Blob type cannot be changed. The default type is a block blob which bundles files. Append blob is for logging scenarios, appending stuff. Page blobs are for frequent read/write opperations. Datasets files are thus stored in block blobs. The virtual machine that handles users, SQL, etc .. can be moved from local server to Azure page if/when traffic is high.

### Dealing with data

*1. uploading data*

There are many options, here are those useful for OpenNeuroPET:
- [AzCopy](https://github.com/Azure/azure-storage-azcopy): CLI for windows, macOS and linux for containers and blobs. 
- Blobfuse: linux virtual file system.

*2. blobs vs files*

| files                      |  blobs                   |
|:--------------------------:|:------------------------:|
| directory objects          | flat-namespace           |
| access trhough file shares | access through container |
| share across VM            | azuee disk single VM     |

Files are mostly used for 'active shared directory' and applications migration.

*3. Backup*

Create a backup vault and give permission at the account level (see below). Create a retention policy and finally configure and enable backup for blobs. Object replication for blobs requires two storage accounts, at least two containers, allows blob versioning and change feed on the source, allow blob versioning on the destination, and configure the onject retention policy.


## Security

By default, data are replicated using geographic pairs, two centres within the same geographic area. Also by default a goegraphic area is an area wit the same data laws.  

Data are always encrypted at rest (Storage Service Encryption SSE) using 256-bit Advanced Encryption Standard (AES). There is an option to use the key vault to use your own encryption. Data can also be encrypted in transit using client-side encrryption, HTTPS or SMB3. Access can be granted using Shared access signature [SAS](https://learn.microsoft.com/en-us/rest/api/storageservices/create-user-delegation-sas). Interactive Access Management (IAM) is only used for Azure files with active directory.

### Authorizing requests to storage

Blobs are objects and each object as an authentification, either using the storage account key (default) or active directory. 

For blobs, shared keys can be used but this gives full access to applications - and one can actually turn off shared access keys ensuring that only SAS is used. SAS can be used to managed roles and permissions. SAS works using security tokens which are time bounded (tip: set start time as now - 15 minutes preventing clock queue issues). Token can specify read, write, delete rights. Finally, we can specify on Azure the protcol allowed )e.g. HTTPS) to use SAS or specific IP or IP range.  

There are three types of SAS: (1) service level (i.e. read data), (2) account level (i.e. push, pull, etc), and (3) user delegation (i.e. access containers and blobs). As administrator, an account level SAS will allow DataLad to create datasets while as users, a user delegation SAS will allow downloading a dataset.  Anonymous access to a blob and container can also be enable, which is useful for non-GDPR regulated data. In this case no need of keys and SAS.  

### Data retention policy and disposal

Azure activity logs are created for all actions on blobs and containers but only covers a 90 days period and it is therefore essential to retreive and aggregate them regularly to create a fully auditable trail. 

To ensure data remain for a period of time (e.g. paid for), one can set containers and blobs in immutatable storage in a WORM state (write once, read many). 






