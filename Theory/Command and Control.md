- Think of a netcat listener that is capable of handling many reverse shells calling back at once.
- **Domain Footprinting**: Using a known good host as proxy. Such as cloudflare
	 1. The C2 Operator has a domain that proxies all requests through Cloudflare.   
	2. The Victim beacons out to the C2 Domain.
	3. Cloudflare proxies the request, then looks at the Host header and relays the traffic to the correct server.
	4. The C2 Server then responds to Cloudflare with the C2 Commands.
	5. The Victim then receives the command from Cloudflare.
- **C2 Profiles**: Aka NGINX Reverse Proxy, Aka Apache Mod_Proxy/Mod_Rewrite, Aka Malleable HTTP C2 Profiles
	1. The Victim beacons out to the C2 Server with a custom header in the HTTP request, while a SOC Analyst has a normal HTTP Request  
	2. The requests are proxied through Cloudflare
	3. The C2 Server receives the request and looks for the custom header, and then evaluates how to respond based on the C2 Profile.
	4. The C2 Server responds to the client and responds to the Analyst/Compromised device.
- Examples of C2 software:
	- Metasploit: Free
	- Armitage: Free
	- Powershell Empire/Starkiller: Free
	- Covenant: Free
	- Silver: Free
	- Cobalt Strike: Paid
	- Brute Ratel: Paid