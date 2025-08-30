# Entra ID

- Used to be known as Azure AD.  
- The identity provider for Microsoft.  
- **Microsoft Graph** (REST) is the standard way to interact with Entra.  

## What Entra ID Does

- Cloud-based identity and access management service
- Manages users, groups, and applications
- Provides single sign-on (SSO) to other apps and websites
- Different from Windows Active Directory (on-premises)

## User Types

- **Member users** — Users created directly in your Entra ID
- **Guest users** — External users invited to your tenant (B2B)
- **External identities** — Users from other organizations or social accounts

## Group Types

- **Security groups** — Control access to resources
- **Microsoft 365 groups** — Collaboration (email, SharePoint, Teams)
- **Dynamic groups** — Membership based on user attributes (Premium P1 required)

## Licenses

- **Free** — Basic user/group management, SSO to popular apps
- **Premium P1** — Conditional access, dynamic groups, self-service password reset
- **Premium P2** — Identity protection, privileged identity management

## Important Commands

### PowerShell 

``` Powershell
# Connect to Entra ID
Connect-AzureAD

# Create user
New-AzureADUser -DisplayName "John Doe" -UserPrincipalName "john@contoso.com" -AccountEnabled $true

# Create group
New-AzureADGroup -DisplayName "IT Team" -SecurityEnabled $true -MailEnabled $false

# Add user to group
Add-AzureADGroupMember -ObjectId "group-id" -RefObjectId "user-id"

# Get user info
Get-AzureADUser -Filter "DisplayName eq 'John Doe'"
```

### CLI

``` Bash
# Sign in
az login

# Create user
az ad user create --display-name "John Doe" --user-principal-name "john@contoso.com"

# Create group
az ad group create --display-name "IT Team" --mail-nickname "ITTeam"

# List users
az ad user list --query "[].{Name:displayName,UPN:userPrincipalName}"
```