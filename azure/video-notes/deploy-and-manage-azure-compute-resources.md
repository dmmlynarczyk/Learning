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

### Security Types

**Security Type**: refers to the different security features available for a virtual machine. There are three options:
- **Standard**: The basic level of security for your virtual machines.
- **Trusted launch virtual machines**: protects against persistent and advanced attacks on Gen 2 virtual machines with configurable features like secure boot and virtual Trusted Platform Module (vTPM).
- **Confidential virtual machines**: on top of Trusted launch, Confidential virtual machine offers higher *confidentiality and integrity guaranteed* with hardware-based trusted execution environment.

### Spot Instances

**Spot instances**: are a way to save money, you do not have to pay full price, but as soon as someone comes along willing to pay full price, you will lose your instance.  
These are great for low-priority workloads.

### Sizes

[TO ADD]

### Hibernation

**Hibernation**: saves you time and money by deallocating your virtual machine and saving the contents of its RAM to the root volume.  
This allows you to resume from where you left off when your VM restarts.  
