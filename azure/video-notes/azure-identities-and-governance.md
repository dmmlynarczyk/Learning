# Manage Azure Identities and Governance

**20%-25% of AZ-104 exam.**  

## Entra ID Basics

> [!NOTE]
> Azure AD is now called Entra ID.  
> Any time you see Azure AD in studying, it should be Entra ID

**Microsoft Entra ID:** is Microsoft's cloud-based identity and access management service that handles user authentication and authorization for Azure resources.  
It is derivative of **Microsoft Active Directory**, which is their on-premises service for managing users, computers, and resources.

## License Tiers

- **Microsoft Entra ID Free:** No SLA, AI, and other advanced features, but great for most basic users just starting out
  - Basic user/group management, SSO to popular apps
- **Microsoft Entra ID P1:** Includes some advanced features
  - Conditional access, dynamic groups, self-service password reset
- **Microsoft Entra ID P2:** Includes everything in P1 and more advanced features
  - Identity protection, privileged identity management, and *Microsoft Entra ID Protection*
- **Microsoft Entra ID Governance:** Add-on license, you must have a P1 or P2 already

## Basic Concepts of Account, Tenant, Subscription, and Resource Group

- **Account** is a person or a program
  - If an app, it is called a **Managed Identity**
- **Tenant** is a representation of an organization
  - Typically represented bya  public domain, but will be assigned a .onmicrosoft.com domain if not specified
  - A dedicated instance of **Entra ID**
  - **Every Azure Account is part of at least one tenant**  
- **Subscription** is an agreement with Microsoft to use Azure services, and how you will pay for that usage.
  - All Azure resource usage will be billed to the payment method of the subscription
- **Resource Group** is a container that holds related resources.

## Domains

If you choose not to add a custom domain you will be stuck with a <domain>.onmicrosoft.com style domain, which is the generic Microsoft domain space.  If you do want to add a custom domain, you will need to add either a **TXT** or **MX** record to your domain registrar records page to show you have ownership of that domain.   

## Groups

Groups are simply a way to organize based on a fixed assignment or on a dynamic property.  
When creating groups you have the option to *allow Azure AD roles to be assigned to the group.*  This allows you to use the group as a way to assign permissions.  The group is just an organizational structure.  

**Dynamic Groups:** are groups that are assigned members automatically based on certain criteria being met. *(If user position is X, location is Y, department is Z, etc.)*

**Assigned Groups:** are groups that have members set by the administrator manually.

## Licenses

> [!NOTE]
> Adding, removing, and reprocessing licensing assignments is only available within the M365 Admin Center.  

Certain good features are locked behind a license such as "Self-Service Password Change for cloud users."  Instead of users being able to change their passwords on their own, liek the license would allow, users would have to call in to the help desk instead.  
Items such as "Multifactor authentication for administrator roles" is part of the free tier, so it allows your admin accounts to at least be secure.  This is only for the authenticator app though, things like SMS and Phone MFA are through a license.  
Licenses may not be able to be assigned without a 'Usage Location' listed in the user's information.  

## Administrative Units

**Administatvie Unit:** is a resource inside of Entra that can act as a container for other resources.  It can contain only users, groups, or devices.  
It is a way of segregating permissions into a logical seperation.  So certain users can only affect certain parts of the organization instead of the entire organization.  

In my lab example, Teacher1 is a *Password Administrator* for Classroom1.  He can reset passwords for any person in Classroom1, but not in any othere classroom.  Student1 is a user inside of Classroom1, so he is the only person that can have their password reset by Teacher1.  An interesting thing is that we can also add groups to the assignment, so if we added a *Student Group* to Classroom1, then teacher1 could reset passwords for anyone inside of that group.  A container inside a container.  

## Devices

**Devices:** represent the physical devices that users use to access organizational tools, information, and resources.  My cellphone and home computer are devices that access my company's resources.  
In devices section you can set things like, don't allow rooted/jailbroken devices or insecure devices to access resources.  

## Self-Service Password Reset

Password reset is available to administrative users already, but not for other users without special licensing.  
By default self service password reset is set to 'None', but there are three options to choose from:
- **None:** no one can reset their password by themselves, and users must call in to helpd desk.  
- **Selected:** limited to a specifc group of users.  
- **All:** all users are able to reset their passwords themselves.  
This essentially just allows the user to hit the "Forgot Password" option on the Azure login screens.  

**Password Pushback:** should be enabled for a company that is AD Sync'd.  This allows a user to change their password for Azure/M365 and it will push into the on-prem Active Directory.  

## Role Based Access Control (RBAC) 

**Role Based Access Control (RBAC):** is a security feature in Azure that allows you to grant specific permissions to different Azure entities based on their ROLES in your organization.  
At a basic level, "in order for a user to interact with a resource in Azure, you need permissions."  With 10,000s of users, and 1,000s of resources, it quickly becomes impossible to manage properly.  There could be literally millions of permissions that need to be worked on when all is said and done.  

RBAC allows you to define a number of "roles" across the organization that you can then assign those roles to individuals.  Those roles have a static number of permissions, meaning you do not have to worry about giving access to too much.  As long as the role is setup properly, the user will be given least access permissions.  
Users *CAN* be assigned to multiple roles.  

### Benefits of RBAC

- A level of abstraction the helps to simplify management
- This means fewer errors, and nobody has extra permissions that may be overlooked.
- Easier for new users to be added to the system and assigned the correct permissions.

### Role Types

- **Owner:** Grants full access to manage all resources, including the ability to assign roles in Azure RBAC.  
- **Contributor:** Grants full access to manage all resources, *but does not allow you to assign roles in Azure RBAC*, manage assignments in Azure Blueprints, or *share image galleries.*  
- **Reader:** View all resources, but does not allow you to make any changes.  


You can also make custom roles!  
To do this you need to have an Azure Premium P1/P2 to gain access to custom roles.  But it will allow you to get super-granular into permissions to pick and choose specifics.  
This is done at the Subscription level under IAM > "+ Custome Role"  

### Interpret Access Assignments

You can view who has access to different resources, by goining into that resource group, clicking "Access Control (IAM), clicking "role assignments", and you will be presented with a list of users with different roles.  
The other way is be selecting the user in Entra ID and selecting either "Azure role assignments" or "Assigned roles"  
