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

Get all the groups in the current domain
- Get-NetGroup
- Get-NetGroup –Domain <targetdomain>
- Get-NetGroup –FullData

Get all groups containing the word "admin" in group name
- Get-NetGroup *admin*

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
