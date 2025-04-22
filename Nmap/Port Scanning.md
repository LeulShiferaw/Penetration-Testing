- You can have open, closed, filtered (unknown), unfiltered (accesible but unknown), open|filtered (firewall), closed|filtered(unknown)
- If root -sS is default otherwise -sT is default.
- -sU for udp scanning
- -sV for version scanning
- It will be faster if we include –disable-arp-ping -Pn -n.
	Eg. sudo nmap IP_ADDRESS -sU -Pn -n –disable-arp-ping
- Press [Space bar] to get an update on the scan if it is long.
- -F is for fast scan of the top 100 ports.