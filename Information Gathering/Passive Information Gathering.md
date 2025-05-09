1. Whois: can be used to gather information about a target.
	eg. `whois megacorpone.com -h 192.168.50.251` or `whois megacorpone -h whois.verisign-grs.com`
2. Google Hacking: use google search engine for passive information gathering
	 eg. `site:megacorpone`
		`site:megacorpone filetype:txt`
		`site:megacorpone -filetype:html`: excludes html filetypes
		`site:megacorpone intitle:"index of" "parent directory"`: includes searches    with those titles
	- Use Google Hacking Database for more search types
3. Netcraft: searchdns.netcraft.com can be used to find information on targets.
4. Open-source code: search through repos on github or the like. We can filter the search to find specific items that might be of use for compromising the target's system. One search tactic: `filename: users`. On megacorpone we found that this enabled us to find xampp.users which contained a username and password combination.
	- We can also use tools such as Gitrob and Gitleaks
5. Shodan: a search engine for IoT devices connected to the internet. We can search for eg: 'hostname:megacorpone.com' (without spaces) and then go through the ports to see for example the different ssh port that are open including their banners (versions)
6. Security Headers and SSL Server Test: google both to find their websites. They scan the target and give a summary of their security strength. 