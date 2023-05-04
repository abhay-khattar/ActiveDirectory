# 01 Installing the Domain Controller
[Resource Line](https://woshub.com/windows-server-core-install-active-directory-domain-controller/)

1. Use `sconfig` or use the associated commands to change it manually to:
    - Change Hostname
    - Change the IP Address to Static
    - Change DNS Server to our own IP Address
    - Change the defalt gateway to 192.168.163.2
```powershell
Rename-Computer -NewName Computer_Name
New-NetIPAddress –InterfaceAlias “Wired Ethernet Connection” –IPv4Address “192.168.163.155” –PrefixLength 24 -DefaultGateway 192.168.163.2
Set-DnsClientServerAddress -InterfaceAlias “Wired Ethernet Connection” -ServerAddresses 192.168.163.2
# We can get the Interface Index using Get-NetAdapter and use the tag -InterfaceIndex in the command to change the existing adapter
```

2. Install thte Active Directory Windows Feature

```powershell
Install-WindowsFeature  AD-Domain-Services -IncludeManagementTools -Verbose
# To check if the AD-Domain-Services has been installed or not use the following 
Get-WindowsFeature -Name *AD*
# This will list all the windows features that has AD and the AD-Domain-Services should be crossed
```
![Imgur](https://i.imgur.com/yWyuiMo.png)

3. Install the Active Directory Domain
```powershell
Get-Command -Module ADDSDeployment
# Import-Module ADDSDeployment
Install-ADDSForest
# Set the Domain name, and domain password
```
4. We will have to change the DNS Configuration again (as it is looped back to the localhost when the AD is setup)
```powershell
Set-DnsClientServerAddress -InterfaceIndex 6 -ServerAddresses 192.168.163.155 
# Server Address is the IP Address of the Domain Controller
```