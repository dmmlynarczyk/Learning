# Manage Azure Identities and Governance

**20%-25% of AZ-104 exam.**  

## Entra ID Basics

> [!NOTE]
> Azure AD is now called Entra ID.  
> Any time you see Azure AD in studying, it should be Entra ID

**Microsoft Entra ID**: is Microsoft's cloud-based identity and access management service that handles user authentication and authorization for Azure resources.  
It is derivative of **Microsoft Active Directory**, which is their on-premises service for managing users, computers, and resources.

## License Tiers

- **Microsoft Entra ID Free** — No SLA, AI, and other advanced features, but great for most basic users just starting out
  - Basic user/group management, SSO to popular apps
- **Microsoft Entra ID P1** — Includes some advanced features
  - Conditional access, dynamic groups, self-service password reset
- **Microsoft Entra ID P2** — Includes everything in P1 and more advanced features
  - Identity protection, privileged identity management, and *Microsoft Entra ID Protection*
- **Microsoft Entra ID Governance** — Add-on license, you must have a P1 or P2 already

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


