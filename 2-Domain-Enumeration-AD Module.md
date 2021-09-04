## **Active Directory Management Module**

powershell -ExecutionPolicy bypass

Import-Module .\Microsoft.ActiveDirectory.Management.dll
Import-Module .\ActiveDirectory\ActiveDirectory.psd1

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

Search for a particular string in a user's attributes:
- Get-ADUser -Filter 'Description -like "*built*"' - Properties Description | select name,Description

Get list of all properties for users in the current domain
- Get-ADUser -Filter * -Properties * | select -First 1 | Get-Member -MemberType *Property | select Name
- Get-ADUser -Filter * -Properties * | select name,@{expression={[datetime]::fromFileTime($_.pwdlastset)}}

Get a list of computers in the current domain
- Get-ADComputer -Filter * | select Name
- Get-ADComputer -Filter 'OperatingSystem -like "*Server 2016*"' -Properties OperatingSystem | select Name,OperatingSystem
- Get-ADComputer -Filter *  -Properties DNSHostName | %{Test-Connection -Count 1 -ComputerName $_.DNSHostName}
- Get-ADComputer -Filter * -Properties *

Get all the groups in the current domain
- Get-ADGroup -Filter * | select Name
- Get-ADGroup -Filter * -Properties *

Get all groups containing the word "admin" in group name
- Get-ADGroup -Filter 'Name -like "*admin*"' | select Name

Get all the members of the Domain Admins group
- Get-ADGroupMember -Identity "Domain Admins" -Recursive

Get the group membership for a user:
- Get-ADPrincipalGroupMembership -Identity student1

Get list of GPO in current domain
- Get-GPO -All (GroupPolicy module)
- Get-GPResultantSetOfPolicy -ReportType Html -Path C:\Users\Administrator\report.html (Provides RSoP)

Get list of GPO in current domain.
- Get-GPO -All (GroupPolicy module) Get-GPResultantSetOfPolicy -ReportType Html -Path C:\Users\Administrator\report.html (Provides RSoP)

Get OUs in a domain
Get-ADOrganizationalUnit -Filter * -Properties *

Get GPO applied on an OU. Read GPOname from gplink attribute from
- Get-GPO -Guid AB306569-220D-43FF-B03B-83E8F4EF8081 (GroupPolicy module)

See link below for module options
[Microsoft](https://docs.microsoft.com/en-us/powershell/module/activedirectory/?view=windowsserver2019-ps)
