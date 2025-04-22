- For quickly grabbing banners from websites, I could do `nc -nv ip_address port` or run `nmap -sV –script=banner target`
- We can use `curl -IL url` for grabbing banners too.
- To grab banners, we tcpdump on the interface that connects the two ip addresses and  nc into the port from another terminal. We should see the banner in the tcp dump.
	Eg. 
	`tcpdump -i tun0 host your_ip and target_ip`
	`nc -nv target_ip target_port`
- In the tcpdump look for Flag P (push). This line should contain the banner.