# NTP-Server.md
Configure the Windows Server as an NTP Server
1.	Open PowerShell Ise as administrator 
enter the command below
w32tm /config /manualpeerlist:"au.pool.ntp.org" /syncfromflags:manual /reliable:YES /update
(if its for other reason can be change to that region time zone)
2.	Stop and start the NTP services  by using the command below
net stop w32time
net start w32time


Open the Windows Firewall for NTP Traffic


1.	 Open Windows Firewall with Advanced Security (you can search for it in the Start menu).
2.	Click on Inbound Rules.
3.	On the right-hand side, click New Rule.
4.	Choose Port, then select UDP and type 123 in the specific port box.
5.	Allow the connection.
6.	Apply this rule to the appropriate profiles (Domain, Private, and Public) as needed.
7.	Give the rule a name (e.g., "Allow NTP Traffic") and click Finish.




Test the NTP Server

On Windows Machine use below command 
w32tm /stripchart /computer:<ServerName> /dataonly /samples:5

On linux machine: use below command
 ntpq -p <ServerIP>



Additional Configuration


1.	Open Regedit.
2.	Go to HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W32Time\Parameters
3.	Modify NTP server value to au.pool.ntp.org
 
 
