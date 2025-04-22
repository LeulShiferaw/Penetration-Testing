- Firewalls use a set of rules to block suspicious activity.

- IDS detects suspicious activity and reports it to the administrator.

- IPS complements the IDS and may act on suspicious activity based on its programming.

- -sA is used to overcome firewalls as it is less suspicious. -sT and -sS can be detected by firewalls

- We can deteremine if there is an IDS/IPS in place by using multple VPS( virtual private server). If we get blocked by one we know there is an IPS in place and we could use another IP to get the job done.

- -D RND:5 – is a command we can add to nmap scans to generate different source ip addresses and use our own some where in there. This will make it harder to block our ip or ip range since there are a lot of sources. Decoys must be alive though.

- We can also use -S to specify the source IP address of the scan. We can use different ip addresses if we get blocked.

- Using –source-port 53 could help detect open ports instead of having them returned as filtered.

**Labs**
- Easy lab. Just do `nmap ipaddress -O`. Banner grab from ssh

- Medium Lab. run: `sudo nmap ipaddress -sU -V -p 53 -D RND:4`

- Hard Lab. Look at the DNS proxy part of [Firewall IDS/IPS section](https://academy.hackthebox.com/module/19/section/106). We basically use –source-port 53 and then did: `ncat -nv –source-port 53 ipaddress port` (50000 in this case). In order for this to work I had to disable the service running on my system at port 53.