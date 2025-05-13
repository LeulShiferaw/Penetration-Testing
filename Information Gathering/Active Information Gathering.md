	1. DNS Enumeration
	- DNS is a distributed database responsible for translating domain names to ip addresses.
	- Types of DNS records: NS (the name of authoritative servers hosting the DNS records), A (ipv4 address), AAAA (ipv6 address), MX (contains names of servers responsible for handling email), PTR, CNAME (used to create aliases for other host records), TXT (any arbitrary data)
	- Manually enumerating DNS
		- `host www.megacorpone.com`: to get ip address of dns
		- `host -t mx megacorpone.com`: to retrieve mx records
		- `host -t txt megacorpone.com`: to retrieve txt records
		- To enumerate we can test manually like this: `host idontexist.megacorpone.com`
		- `for ip in $(cat list.txt); do host $ip.megacorpone.com; done`: to enumerate all the list items as potential subdomains
	- Automatically enumerating DNS
		- `dnsrecon -d megacorpone.com -t std`: standard scanning
		- `dnsrecon -d megacorpone.com -D ~/list.txt -t brt`: brute forcing a list
		- `dnsenum megacorpone.com`: using dnsenum
	- Windows version
		- `nslookup mail.megacorpone.com`: this is the same as host
		- `nslookup -type=TXT info.megacorpone.com 192.168.50.151`: to get txt records from a specific DNS server
2. TCP/UDP manual scanning theory
	- `nc -nvv -w 1 -z 192.168.50.152 3388-3390`: This will scan range 3388-3390 using tcp.
	- `nc -nv -u -z -w 1 192.168.50.149 120-123`: This will scan the range 120-123 using udp
3. Nmap: [[Nmap]]
4. Windows Nmap
	- We can download windows nmap version
	- If we don't have internet access to download it, we can use 
		 `Test-NetConnection -Port 445 ipaddress` on powershell
	- This will test if 445 is open on the ipaddress
	- To test a range from 1-1024:
	![[Pasted image 20250512153741.png]]
5. SMB Enumeration: [[SMB Enumeration]]
6. SMTP Enumeration: [[SMTP Enumeration]]