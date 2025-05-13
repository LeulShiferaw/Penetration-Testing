1. `nmap ipaddress`: basic scan. Generates some traffic in iptables about 72KB.
2. `nmap -p 1-65535 ipaddress`: generates a lot more traffic about 4MB.
3. `sudo nmap -sS ipaddress`: stealth scanning. It doesn't complete the TCP 3-way handshakre. Faster and doesn't generate as much traffic.
4. `nmap -sT ipaddress`: completes 3-way handshake
5. `sudo nmap -sU ipaddress`: uses a udp scan that relies on icmp port unreachable packet. For some ports it sends a port specific packet such as for SNMP (port 161).
6. `sudo nmap -sU -sS ipaddress`: Use both for better and more coverage results.
7. `nmap -sn 192.168.50.1-253`: Network sweeping. Checks which hosts are up and running.
8. `nmap -v -sn 192.168.50.1-253 -oG ping-sweep.txt`: sweep the network and generate a grepable result.
9. `nmap -p 80 192.168.50.1-253 -oG web-sweep.txt`: sweep a specific tcp or udp port.
10. `nmap -sT -A --top-ports=20 192.168.50.1-253 -oG top-sweep.txt`: Scan the top 20 ports and do OS detection, default NSE scripts and traceroute using -A.
11. `sudo nmap -O ipaddress --osscan-guess`: -O will determine the os version, but will only spit out a result if it is accurate. --osscan-guess will display the guess whether accurate or not.