- There are a lot of scripts builtin into nmap.

- sudo `nmap TARGET --script SCRIPT_NAME1, SCRIPT_NAME2`

- example of a script is "banner" (for identifying banners) and "smtp-command" (for identifying some of the commands for an smtp server).

- -A is for aggresive scan that determines service detection, OS detection, traceroute and default scripts (-sC).

- We can use –script vuln to determine vulnerabilities for the version of the http server for example
	eg. `sudo nmap ip_address -p 80 -sV –script vuln`