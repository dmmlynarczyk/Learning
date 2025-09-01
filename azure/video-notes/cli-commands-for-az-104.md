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
