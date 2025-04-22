1. nmap into the system

2. use whatweb to get information

3. Go through the source code

4. Use gobuster (`gobuster dir -u http://<ip>/directory -w wordlist`)

5.  Go through the directories of gobuster

6. Found admin (username) and nibbles (password)

7. Go to plugins in admin.php using the above username and password

8. Configure My Images

9. Upload php shell command to reverse shell it

10. Listen on attacker

11. Open the shell file from /nibblelog/content/plugins/myimages/image.php

12. Submit user.txt from home folder and unzip personal.zip from home folder

13. Get Linenum.sh using file transfer because you can’t open vim

14. Run it to see that /home/nibbler/personal/stuff/monitor can run with sudo without password

15. Add reverseshell at the end of the file because we can edit it

16. run listener on a new port on attacker and execute the full path with sudo

17. Get root.txt from /root

18. Alternative is metasploit module but it doesn’t seem to work for me.