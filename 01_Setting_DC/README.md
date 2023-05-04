# 01 Installing the Domain Controller

1. Use `sconfig` to:
    - Change Hostname
    - Change the IP Address to Static
    - Change DNS Server to our own IP Address
    - Change the defalt gateway to 192.168.163.2

2. Install thte Active Directory Windows Feature

```powershell
Install-WindowsFeature  AD-Domain-Services -IncludeManagementTools -Verbose
```