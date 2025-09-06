# CLI Commands For AZ-104 Exam

The exam does not require programming in the sense of coding, but does require knowledge of scripting (PowerShell, Azure Portal, and Bash/CLI).  
Additionally it is good to know how to at least read JSON templates and CLI responses.

## Why Do We Need This?

- Allows for automation of commonly used tasks.
- Allows for error reduction, since you can now check scripts into a source control repository and copy known good working scripts.
  - Now all you need to do is edit minimal things like names or IP addresses and run them.
  - Also allows you to share and track changes to scripts.

## Memorizing PowerShell and CLI Commands

There is a predictable naming convention for commands.  
**For Bash commands**:  
``` bash
az vm list
az vm create
az vm delete
```
``` bash
az keyvault list
az keyvault create
az keyvault delete
```
Notice the convention that the middle word defines the service or subservice that we will be running commands on.  
**For PowerShell commands**:  
``` powershell
Get-AzVM
New-AzVM
Remove-AzVM
```
Verb is the first part of the word but the last bit is the consistent service name, *but with no spaces like in Bash.*  

## Important PowerShell Commands

- **To install a new AZ module in PowerShell** run the following command as an administrator:  
  ``` powershell
  Install-Module -Name AZ -AllowClobber -Repository PSGallery -Force
  ```
- **To update a new AZ Module** run the following command as an administrator:
  ``` powershell
  Update-Module -Name AZ -AllowClobber -Repository PSGallery
  ```
- **To connect to an Azure account**:
  ``` powershell
  Connect-AzAccount
  ```
  - *This will bring up a sign-in screen for you to authenticate from.*
- **To download the latest version of PowerShell**:
  - Download for your operating system from [Github](https://github.com/PowerShell/PowerShell/releases)

## EntraID Management

### Creating A New User

The following two lines will take a password, that you make that is complex enough to meet your organizations complexity requirements and assign it to a variable `$passwordProfile`.  
Next it will create a new user with specific flags such as UserPrincipalName, DisplayName, Password, AccountEnabled, JobTitle, Department, and UsageLocation.  

1. Assign your variables:
  ``` powershell
  $password = <string>
  $uname = <string>
  $nickname = <string>
  $upn = <string> # this is the email address
  $jobTitle = <string>
  $dept = <string>
  $location = <string>
  ```

2. Store your complex password:
  ``` powershell
  $passwordProfile = New-Object -TypeName "Microsoft.Azure.PowerShell.Cmdlets.Resources.MSGraph.Models.ApiV10.MicrosoftGraphPasswordProfile" -Property @{Password=$password}
  ```
3. Create a new user for your domain:
  ``` powershell
  New-AzADUser -UserPrincipalName $upn -DisplayName $uname -MailNickname $nickname -PasswordProfile $passwordProfile -AccountEnabled $true -JobTitle $jobTitle -Department $dept -UsageLocation $location
  ```

The flags used for creating the user come from [learn.microsoft.com](https://learn.microsoft.com/en-us/powershell/module/az.resources/new-azaduser?view=azps-14.3.0)