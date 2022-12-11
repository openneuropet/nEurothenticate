# A quick review of Azure for OpenNeuroPET

## Usage

Storing files for distributed access.

## Storage

Data replication using RA-GRS read access geo-redondnat storage with copies in EU. RA ensures data can be read from any of the two paired-servers.

Every object has a URL e.g. http://mystorageaccount.blob.core.windows.net or http://mystorageaccount.file.core.windows.net

Containers act as folders, all files are stored into blobs. There is an unlimited number of containers which have unlimited number of blobs. This is an ideal scenario using one container per dataset. 

Data can be stored as hot, cool or archived - with cost of access vs storage being in opposite directions: hot is cheap access expensive storage, archived is expensive access. The most likely scenario is to use cool storage for most datasets, but it is possible to switch between storage 'tier' at any time. There is also a blob life cycle policy allowing to create rules for storage tier applying rules daily, thus optimizing cost (move anyfiles not touched for 30 days to cool).

### What are blobs

Blob type cannot be changed. The default type is a block blob which bundles files. Append blob is for logging scenarios, appending stuff. Page blobs are for frequent read/write opperations. Datasets files are thus stored in block blobs. The virtual machine that handles users, SQL, etc .. can be moved from local server to Azure page if/when traffic is high.

### Dealing with data

*1. uploading data*

There are many options, here are those useful for OpenNeuroPET:
- AzCopy: CLI for windows and linux for containers and blobs.
- Blobfuse: linux virtual file system.

*2. blobs, files, queue data*

| files                      |  blobs                    |
|----------------------------|:-------------------------:|
| directory objects          |  flat-namespace           |
| access trhough file shares |  access through container |
| share across VM            | azuee disk single VM      |

## Security



### Access

Access via multiple tools, including the Azure Blob Storage client library for Python - to be used by DataLad.

Blobs are objects and each object as an authentification, either using the storage account key (default) or active directory. 

Containers can be public or private -- allowing CC0 datasets to be shared openly while GDPR datasets are in private containers. 

Shared access signature [SAS](https://learn.microsoft.com/en-us/rest/api/storageservices/create-user-delegation-sas)

