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
- **Geo-zone-redundant storage (GZRS): Optimal data protection solution that includes the offerings of both GRS and ZRS.
  - Recommended for critical data scenarios.
  - Three copies of your files in three different datacenters in two different regions.
  - **This is the safest option if you NEED your data safe.**

### Advanced Options