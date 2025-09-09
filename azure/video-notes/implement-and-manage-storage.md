# Implement and Manage Storage

15%-20% of AZ-104 exam.  

## Create Storage Accounts

When creating a storage account it is important to remember that the region that you choose will directly affect the amount you pay.  But you want the data to live close to you for accessing.  Region can also be chosen based on the jurisdiction of the data you are storing.  For example, health data for U.S. patients, need to be stored in the U.S.  

### Redundant Storage

> [!NOTE]
> Not all redundancy options are available in all regions.

The data in your Azure storage account is always replicated (*copied three times*) to ensure durability and high availability, but there are different methods on how and where that data is replicated to. 
- **Locally-redundant storage (LRS)**: Has basic protections against server rack and drive failures.
  - Lowest cost option.
  - Stored in one region/one data center
  - Recommended for non-critical scenarios.
- **Geo-redundant storage (GRS)**: Intermediate option with failover capabilities in a secondary region.
  - Recommended for backup scenarios.
  - Takes your data out to another region.
    - So three copies in a datacenter in your region and three copies of your data in another region.
- **Zone-redundant storage (ZRS)**: Intermediate option with protection against datacenter-level failures.
  - Recommended for high availability scenarios.
  - Spreads across three datacenters across one region.
- **Geo-zone-redundant storage (GZRS)**: Optimal data protection solution that includes the offerings of both GRS and ZRS.
  - Recommended for critical data scenarios.
  - Three copies of your files in three different datacenters in two different regions.
  - **This is the safest option if you NEED your data safe.**

### Advanced Options

Just like in AWS, Azure has an option to allow/disallow anonymous access on individual storage containers.  It is best to leave it off (*Default*) as this will greatly reduce an accidental leak of anything in your storage accounts.  

The default version are set, because they are typically the best options, and shouldn't be altered unless you have specific reasons for altering.  

### Blob Storage Access tiers

**Access Tier**: is the default tier that is inferred by any blob *without an explicitly set tier*
- **Hot**: Optimized for frequently accessed data and everyday usage scenarios (*Default*)
- **Cool**: Optimized for infrequently accessed data and backup scenarios
- **Cold**: Optimized for rarely accessed data and backup scenarios
- **Archived**: Can only be set at the blob level and not on the account.  VERY SLOW to get your data otherwise VERY EXPENSIVE for priority retrieval.


### Networking

There are three ways you can connect to your storage account:
- By default storage accounts have public internet access, so anyone, anywhere in the world can access the storage account data if they have the public URL and they have the Access Key!  
- If that gives you uneasy-ness, you can choose to only allow from selected virtual networks and IP addresses.  
- Otherwise you can disable all public access and only allow for private access.  
  - By choosing this option you can create a private endpoint to allow a private connection to your resource.

### Data Protection

**Data Protection**: Keeps your data protected from accidental or erroneous deletion or modification of files.  
**Point-in-time restore**: allows you to restore a container to an earlier state in time.  
**Soft Delete**: when you go to delete a file, it will mark is as 'marked for deletion' and not actually delete it.  You will then have a number of days, specified by you, to retrieve the file before it is actually deleted.  
**Tracking**: Allows you to keep track of changes made to your blob data.  
**File immutability**: means that you have a file that can never be deleted or edited, and you can be certain that it has not been changed.  

## Encryption

There are two encryption types in Azure:
- **Microsoft-managed keys**: where Microsoft takes care of everything, and everything is stored on the hard drives encrypted. (*Default*)
- **Customer-managed keys**: you create and manage the keys and provided the keys to a key vault that you reference.

