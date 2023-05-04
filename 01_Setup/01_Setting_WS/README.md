# Setting up the Workstation
1. Clone the Base Workstation template
2. Join the Domain 
```powershell
# The first step is to change the Domain settings
# Get the Interface Index
Get-DNSClientServerAddress

Set-DNSClientServerAddress -InterfaceIndex 8 -ServerAddress 192.168.163.155
# ServerAddress = IP Address of the domain controller
# Add Computer to the domain
Add-Computer -DomainName abhay-ad.com -Credential abhay-ad\Administrator -Force -Restart
```
![Imgur](https://i.imgur.com/Jnikaw6.png)

