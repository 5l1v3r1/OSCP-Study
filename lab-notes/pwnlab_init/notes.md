Reconnaissance:

Started by finding the host on the network.

nmap -sS -O 192.168.118.0/24

192.168.118.183 looks guilty.

Enumeration:

root@kali:~# nmap -A -T4 192.168.118.183

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-19 14:34 MDT
Nmap scan report for 192.168.118.183
Host is up (0.00051s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE VERSION
80/tcp   open  http    Apache httpd 2.4.10 ((Debian))
|_http-server-header: Apache/2.4.10 (Debian)
|_http-title: PwnLab Intranet Image Hosting
111/tcp  open  rpcbind 2-4 (RPC #100000)
| rpcinfo:
|   program version   port/proto  service
|   100000  2,3,4        111/tcp  rpcbind
|   100000  2,3,4        111/udp  rpcbind
|   100024  1          36222/tcp  status
|_  100024  1          46475/udp  status
3306/tcp open  mysql   MySQL 5.5.47-0+deb8u1
| mysql-info: 
|   Protocol: 10
|   Version: 5.5.47-0+deb8u1
|   Thread ID: 38
|   Capabilities flags: 63487
|   Some Capabilities: SupportsTransactions, Speaks41ProtocolOld, LongColumnFlag, Support41Auth, IgnoreSpaceBeforeParenthesis, InteractiveClient, LongPassword, SupportsCompression, DontAllowDatabaseTableColumn, FoundRows, ConnectWithDatabase, IgnoreSigpipes, SupportsLoadDataLocal, ODBCClient, Speaks41ProtocolNew, SupportsMultipleStatments, SupportsAuthPlugins, SupportsMultipleResults
|   Status: Autocommit
|   Salt: slG[tV0+&~is)kd5x~2{
|_  Auth Plugin Name: 88
MAC Address: 00:0C:29:96:3F:81 (VMware)
Device type: general purpose
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4
OS details: Linux 3.2 - 4.6
Network Distance: 1 hop

TRACEROUTE
HOP RTT     ADDRESS
1   0.51 ms 192.168.118.183

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.26 seconds

root@kali:~# dirb http://192.168.118.183

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Fri May 19 14:36:16 2017
URL_BASE: http://192.168.118.183/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: http://192.168.118.183/ ----
==> DIRECTORY: http://192.168.118.183/images/                                                                          
+ http://192.168.118.183/index.php (CODE:200|SIZE:332)                                                                 
+ http://192.168.118.183/server-status (CODE:403|SIZE:303)                                                             
==> DIRECTORY: http://192.168.118.183/upload/                                                                          

---- Entering directory: http://192.168.118.183/images/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.183/upload/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

-----------------
END_TIME: Fri May 19 14:36:19 2017
DOWNLOADED: 4612 - FOUND: 2
root@kali:~#
