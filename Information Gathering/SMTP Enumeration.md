0. Simple Mail Transfer Protocol
1. We can gather information about a host or network from vulnerable mail servers
2. `nc -nv ipaddress 25`: to connect to SMTP port
	-  ![[Pasted image 20250512174121.png]]
		![[Pasted image 20250512174216.png]]
3. 
```python
	#!/usr/bin/python

	import socket
	import sys

	if len(sys.argv) != 3:
		print("Usage: vrfy.py <username> <target_ip>")
		sys.exit(0)
	
	s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
	
	ip = sys.argv[2]
	connect = s.connect((ip, 25))
	
	banner = s.recv(1024)
	print(banner)
	
	user = (sys.argv[1]).encode()
	s.send(b'VRFY' + user + b'\r\n')
	result = s.recv(1024)
	
	print(result)
	
	s.close()
```
- The above code will verify if the input username is part of the vulnerable mail server at target ip
4. On windows we can run `Test-NetConnection -Port 25 ipaddress` to check if SMTP server is up and running
5. We can also use telnet. To get telnet on windows so that we can access the SMTP service we can use `dism /online /Enable-Feature /FeatureName:TelnetClient`
6. The above command will require root privileges so we can get the telnet.exe from `C:\windows\system32\telnet.exe` and then pass it to the windows machine using curl and http server
7. Once we have the telnet exe we can run `telnet ipaddress 25`
8. 