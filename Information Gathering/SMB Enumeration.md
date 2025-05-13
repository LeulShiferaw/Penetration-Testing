1. `nmap -v -p 139,445 -oG smb.txt 192.168.50.1-254`: scan port 139 (NetBIOS) and 445 (TCP SMB Port)
2. `sudo nbtscan -r 192.168.50.0/24`: more specialized tools for netBIOS
3. `nmap -v -p 139,445 --script smb-os-discovery ipaddress`: potentially inaccurate way of finding out the OS version of the target
4. `net view \\dc01 \\all`: enumerate SMB shares from a windows client