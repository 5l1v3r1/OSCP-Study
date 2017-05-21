dirb http://192.168.118.187

nikto -host 192.168.118.187

curl http://192.168.118.187/robots.txt

nmap --script http-methods -p 80 192.168.118.187

nmap --script http-methods -p 443 192.168.118.187



wpscan --url 192.168.118.187 -e vp u


Don't skip the simple stuff.  Always try generic credentials for admin pages.
