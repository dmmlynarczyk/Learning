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

