1. Checklists: [HackTricks]([https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html]) and [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings)

2. Enumeration scripts: [LinPeas](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS), [linuxprivchecker](https://github.com/sleventyeleven/linuxprivchecker), and [LinEnum](https://github.com/rebootuser/LinEnum)

3. Kernel exploits such as dirty cow. Get linux version from above and use searchsploit.

4. Check installed software using `dpkg -l on linux` and check **[C:/ProgramFiles](/C:/ProgramFiles)** on windows.

5. Check sudo, suid and windows token privileges
s
6. Schedule tasks can be manipulated such as /etc/crontab, /etc/cron.d, and /var/spool/cron/crontabs/root

7. Check bash_history with the history command to see exposed credentials

8. Exposed ssh keys. If we can copy something into the .ssh folder we can create our own key and put the public key in the .ssh folder. We can then use the private key to ssh into it from the attacker host. Also if we can get the private key from the .ssh folder we can use it to ssh too.