# Deploy and Manage Azure Compute Resources

20%-25% of AZ-104 exam.  

## Creating A Virtual Machine

### Availability Options

There are four availability options you can choose from when creating your machine:
- **No infrastructure redundancy required**: self explanatory.
  - Great if it is a stand-alone VM since data is not being passed between VMs.
- **Availability zone**: Physically separate your resources within an Azure region.
- **Virtual machine scale set**: Distribute VMs across zones and fault domains at scale.
- **Availability set**: Automatically distribute your VMs across multiple fault domains.
  - The purpose is to protect against hardware failures in any given data center.
  - Two failures are:
    - **Fault domains**: something relating to the computer failed.
      - Virtual machines in the same fault domain share a common power source and physical network switch.
    - **Update Domains**: planned maintenance from Microsoft updating hardware/infrastructure.
      - Virtual machines in the same update domain will be restarted together during planned maintenance.
      - Azure never restarts more than one update domain at a time.

### Security Types

**Security Type**: refers to the different security features available for a virtual machine. There are three options:
- **Standard**: The basic level of security for your virtual machines.
- **Trusted launch virtual machines**: protects against persistent and advanced attacks on Gen 2 virtual machines with configurable features like secure boot and virtual Trusted Platform Module (vTPM).
- **Confidential virtual machines**: on top of Trusted launch, Confidential virtual machine offers higher *confidentiality and integrity guaranteed* with hardware-based trusted execution environment.

### Spot Instances

**Spot instances**: are a way to save money, you do not have to pay full price, but as soon as someone comes along willing to pay full price, you will lose your instance.  
These are great for low-priority workloads.

### Sizes

**Instance Family**:
- **General Purpose**: balanced VM.
  - Balanced CPU-to-memory ratio.
  - Ideal for testing and development, small to medium databases, and low to medium traffic web servers.
- **Compute Optimized**: double the CPU cores.
  - High CPU-to-memory ratio.
  - Good for medium traffic web servers, network appliances, batch processes, and application servers.
- **Memory Optimized**: double the memory.
  - High memory-to-core ratio.
  - Great for relational database servers, medium to large caches, and in-memory analytics.
- **Storage Optimized**: double the local storage.
  - High disk throughput and IO.
  - Ideal for Big Data, SQL, and NoSQL databases.
- **GPU**: access to a graphics processing unit.
  - Specialized virtual machines targeted for heavy graphic rendering and video editing available with single or multiple GPUs.
- **High-Performance Compute**: fastest everything.
  - Fastest and most powerful CPU virtual machines with optional high-throughput network interfaces (RDMA).



### Hibernation

**Hibernation**: saves you time and money by deallocating your virtual machine and saving the contents of its RAM to the root volume.  
This allows you to resume from where you left off when your VM restarts.  

### Disks

- Virtual machines come with one OS disk and one temporary disk (for short term storage).  
  - Additional data disks can be attached.  
- Azure disk storage encryption automatically encrypts data at rest by default, but you can also encrypt at host if you want.
- **Locally redundant storage (data is replicated within a single datacenter) disk types**
  - **Premium SSD**: Best for production and performance sensitive workloads.
  - **Standard SSD**: Best for web servers, lightly used enterprise applications and dev/test.
  - **Standard HDD**: Best for backup, non-critical, and infrequent access.
- **Zone-redundant storage (data is replicated to three zones)**
  - **Premium SSD**: Best for production workloads that need storage resiliency against zone failures.
  - **Standard SSD**: Best for web servers, lightly used enterprise applications and dev/test that need storage resiliency against zone failures.

### Networking

One of the more important aspects when creating a virtual machine.  
Every virtual machine must be attached to a virtual network.  
You can either create a new one or attach it to a pre-existing virtual network.  
Similar to OS disk you have the option of deleting the public IP and NIC when the VM is deleted.  
**Accelerated networking**: enables low latency and high throughput on the network interface.  

### Management and Advanced Options

- If your VM needs to access other resources and you want to use RBAC and Entra ID to manage those permissions, you can create a system assigned managed identity.  
- A relatively new options is you can now login with Entra ID.  
- **Auto-shutdown**: allows you to select a time to automatically shut down your machine.  
- **Enable recommended alert rules**: You can enable the 7 most recommended alerts to get notified on important events happening on your resource.  
- **OS Guest Diagnostics**: give you metrics every minute for your virtual machine.  You can use them to create alerts and stay informed on your applications.  
- **Extensions**: allows you to add new features, like configuration management or antivirus protection, to your virtual machine using extensions.  
- **Azure Dedicated Hosts**: allows you to provision and manage a physical server within our data centers that are dedicated to your Azure subscription.  
  - Gives you assurance that only VMs from your subscription are on the host. 

## Resizing VMs

A huge benefit of cloud based virtual machines is the easy ability to resize them.  
From your VM page, on the blade select Size under the "Availability + scale" section.  
**This is a disruptive event** by changing the size the VM will have to be restarted.  

## Adding Additional Data Disks

- More often than not, we will need to store data on the virtual machines, but since data should not be stored on the C: drive, and the D: drive is ephemeral we will need to add data disks. *This is the recommended way.*
- First we will need to shutdown our VM.
- Under blade category "Settings" > "Disks"
  - Here you can create a new data disk to add.
  - After your new drive is created and added you will need to mount it in the OS. Just need to go to Disk management, and format a new simple volume!  

## Azure Bastion Service

RDP should be removed as it is very insecure and not a good option long term. If you do choose to use it, it is best to change source to only specific IPs.  But a safer alternative is **Azure Bastion Service**.
**Bastion**: is a way to connect remotely to your VM through the Azure portal. No public IPs required, and port 3389 and 22 do not need to be opened anymore.
- There are serveral tiers in Bastion:
  - Developer
  - Basic
  - Standard
  - Premium
