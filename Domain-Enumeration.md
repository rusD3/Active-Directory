## **Active Directory Management Module**

powershell -ExecutionPolicy bypass

Import-Module ".\Microsoft.ActiveDirectory.Management.dll"
Import-Module ".\Microsoft.ActiveDirectory.Management.resources.dll"

Getcurrentdomain
- Get-ADDomain

Get object of another domain
- Get-ADDomain -Identity example.com

Get domain SID for the current domain
- (Get-ADDomain).DomainSID

Get domain controllers for the current domain
- Get-ADDomainController

Get domain controllers for another domain
- Get-ADDomainController -DomainName example.com -Discover

Get a list of users in the current domain
- Get-ADUser -Filter * -Properties *
- Get-ADUser -Identity user1 -Properties *
- Get-ADUser -Filter * | select SameAccountName

Get list of all properties for users in the current domain
- Get-ADUser -Filter * -Properties * | select -First 1 | Get-Member -MemberType *Property | select Name
- Get-ADUser -Filter * -Properties * | select name,@{expression={[datetime]::fromFileTime($_.pwdlastset)}}

See link below for module options
[Microsoft](https://docs.microsoft.com/en-us/powershell/module/activedirectory/?view=windowsserver2019-ps)

## **PowerView**
Load PowerView
. .\PowerView.ps1

Get current domain
- Get-NetDomain

Get object of another domain
- Get-NetDomain -Domain example.com

Get domain SID for the current domain
- Get-DomainSID

Get domain policy for the current domain
- Get DomainPolicy

Get domain policy for another domain
- (Get-DomainPolicy -domain example.com)."system.access"

Get domain controllers for the current domain
- Get-NetDomainController

Get domain controllers for another domain
- Get-NetDomainController -Domain example.com

Get a list of users in the current domain
- Get-NetUser
- Get-NetUser -UserName example-user

See link for more info
[PowerView](https://github.com/PowerShellMafia/PowerSploit/blob/master/Recon/PowerView.ps1)
