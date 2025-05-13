0. Simple Network Management Protocol
1. `sudo nmap -sU --open -p 161 192.168.50.1-254 -oG open-snmp.txt`: This will scan the target ip range for open snmp services
2. `echo public > community; echo private >> community; echo manager >> community`: to build the community strings file. Community strings are like passwords. We will use this later for other snmp enumeration commands
3. `for ip in $(seq 1 254); do echo 192.168.50.$ip; done > ips`: build the ip list
4. `onesixtyone -c community -i ips`: gets a list of snmp services
5. `snmpwalk -c public -v1 -t 10 ipaddress`: using the output from here we can  use them for social engineering attacks.
6. `snmpwalk -c public -v1 ipaddress 1.3.6.... (OID)`: This will enumerate what ever the OID is representing. Example of OIDs and what they represent is below:![[Pasted image 20250512181752.png]]