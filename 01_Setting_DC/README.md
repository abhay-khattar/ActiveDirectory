# 01 Installing the Domain Controller

1. Use `sconfig` to:
    - Change Hostname
    - Change the IP Address to Static
    - Change DNS Server to our own IP Address
    - Change the defalt gateway to 192.168.163.2

2. Install thte Active Directory Windows Feature

```powershell
Install-WindowsFeature  AD-Domain-Services -IncludeManagementTools -Verbose
# To check if the AD-Domain-Services has been installed or not use the following 
Get-WindowsFeature -Name *AD*
# This will list all the windows features that has AD and the AD-Domain-Services should be crossed
```
![Imgur](https://i.imgur.com/yWyuiMo.png)

3. 