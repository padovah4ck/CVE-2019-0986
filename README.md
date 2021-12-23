# Security Research for FUN

All focused on Microsoft Windows OS

## CVE-2019-0986
https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2019-0986  
This is the PoC I've sent to Microsoft when I reported the above vulnerability  

This PoC exploits "User Profile Service" (ProfSvc.dll).  

It will delete all files within an arbitrary directory despite of the permissions set on that directory  
(except files that are exclusively locked by SYSTEM processes).

Requisite for this:  
1) attacker user cannot have a current active session (he has to be logged-off the system).  
2) attacker user must have an existing HOME directory. 

This is why we are going to delete NTUSER.DAT file (in the attacker HOME directory) in order to trigger the right condition for exploitation.  
So, next step: you shoud log in with another arbitrary "user_2" and exec the exploit with user_1 (attacker) credentials.  


You'll find a precompiled exe bin\x64\Debug directory   
```
Usage :
NtDataPoc.exe USERNAME DOMAINNAME PASSWORD DIRECTORY_TO_DELETE  
  
Example :  
NtDataPoc.exe theuser win10-dev MySecretPwd c:\secureDirectory  
```

IDE VS 2015/2017 | CSproj is available. Compile platform choiche is yours: suggested is x64   
   
   
This has been tested on :  
```
OS Name:                   Microsoft Windows 10 Enterprise N  
OS Version:                10.0.17763 N/A Build 17763
```  
```
OS Name:                   Microsoft Windows 8.1 Pro
OS Version:               6.3.9600 N/D build 9600
```  

---

![Beer](https://icons.iconarchive.com/icons/flat-icons.com/flat/48/Beer-icon.png)  [Buy me a beer if you like ;-)](https://www.buymeacoffee.com/padovah4ck)
