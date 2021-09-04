## **User Hunting**

Find all machines on the current domain where the current user has local admin access
- Find-LocalAdminAccess –Verbose

Find local admins on all machines of the domain (needs administrator privs on non-dc machines).
- Invoke-EnumerateLocalAdmin –Verbose

Find computers where a domain admin (or specified user/group) has sessions: Invoke-UserHunter
- Invoke-UserHunter -GroupName "RDPUsers"

To confirm admin access
- Invoke-UserHunter -CheckAccess

Find computers where a domain admin is logged-in.
- Invoke-UserHunter -Stealth
