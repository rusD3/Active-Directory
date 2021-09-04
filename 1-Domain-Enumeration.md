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

Search for a particular string in a user's attributes:
- Find-UserField -SearchField Description -SearchTerm
"built"

Get all the groups in the current domain
- Get-NetGroup
- Get-NetGroup –Domain <targetdomain>
- Get-NetGroup –FullData

Get all groups containing the word "admin" in group name
- Get-NetGroup admin

Get all the members of the Domain Admins group
- Get-NetGroupMember -GroupName "Domain Admins" -Recurse

Get the group membership for a user:
- Get-NetGroup –UserName "student1"

List all the local groups on a machine (needs administrator privs on non- dc machines)
- Get-NetLocalGroup -ComputerName dcorp-dc.dollarcorp.moneycorp.local -ListGroups

Get members of all the local groups on a machine (needs administrator privs on non-dc machines)
- Get-NetLocalGroup -ComputerName dcorp-dc.dollarcorp.moneycorp.local -Recurse

Get actively logged users on a computer (needs local admin rights on the target)
- Get-NetLoggedon –ComputerName <servername>

Get locally logged users on a computer (needs remote registry on the target-started by-default on server OS)
- Get-LoggedonLocal -ComputerName dcorp- dc.dollarcorp.moneycorp.local

Get the last logged user on a computer (needs administrative rights and remote registry on the target)
- Get-LastLoggedOn –ComputerName <servername>

Findsharesonhostsincurrentdomain
- Invoke-ShareFinder –Verbose

Find sensitive files on computers in the domain
- Invoke-FileFinder –Verbose

Get all fileservers of the domain
- Get-NetFileServer

Get list of GPO in current domain
- Get-NetGPO
- Get-NetGPO -ComputerName dcorp- student1.dollarcorp.moneycorp.local

Get GPO(s) which use Restricted Groups or groups.xml for interesting users
- Get-NetGPOGroup

Get users which are in a local group of a machine using GPO
- Find-GPOComputerAdmin –Computername dcorp-
- student1.dollarcorp.moneycorp.local

Get machines where the given user is member of a specific group
- Find-GPOLocation -UserName student1 -Verbose

Get OUs in a domain
- Get-NetOU -FullData

Get GPO applied on an OU. Read GPOname from gplink attribute from
- Get-NetOU
- Get-NetGPO -GPOname "{AB306569-220D-43FF-B03B- 83E8F4EF8081}"

See link for more info
[PowerView](https://github.com/PowerShellMafia/PowerSploit/blob/master/Recon/PowerView.ps1)
