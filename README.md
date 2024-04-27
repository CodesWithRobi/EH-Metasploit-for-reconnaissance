# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:
![image](https://github.com/CodesWithRobi/EH-Metasploit-for-reconnaissance/assets/130537166/5dd48b5e-cb4d-4222-8251-4c1ce5cc66bd)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
> systemctl start postgresql

> msfdb init

Invoke msfconsole:
## OUTPUT:
![image](https://github.com/CodesWithRobi/EH-Metasploit-for-reconnaissance/assets/130537166/42369811-2f46-4ab2-adae-441ebee35f47)




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![image](https://github.com/CodesWithRobi/EH-Metasploit-for-reconnaissance/assets/130537166/17c367ef-e4dd-4998-8da1-a3fe516406ca)


Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000
## OUTPUT:
![image](https://github.com/CodesWithRobi/EH-Metasploit-for-reconnaissance/assets/130537166/e896bbf5-edbf-4809-9eae-dfdfcf45bacf)

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
![image](https://github.com/CodesWithRobi/EH-Metasploit-for-reconnaissance/assets/130537166/55568150-1887-4aba-9e9c-e3883437f582)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

![image](https://github.com/CodesWithRobi/EH-Metasploit-for-reconnaissance/assets/130537166/4c30bee3-fd41-4116-b3b5-5a2e33caf308)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
##OUTPUT
![image](https://github.com/CodesWithRobi/EH-Metasploit-for-reconnaissance/assets/130537166/6b71f6b9-b46d-4374-a9bd-21868b9faffc)



The info command provides information regarding a module or platform,
![image](https://github.com/CodesWithRobi/EH-Metasploit-for-reconnaissance/assets/130537166/21496da5-fef2-42d8-b5b7-e7e926c1ccc3)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
> systemctl start postgresql

> msfdb init

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![image](https://github.com/CodesWithRobi/EH-Metasploit-for-reconnaissance/assets/130537166/9f998219-a2ae-4dbc-8c97-0ab720f38b24)



Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
![image](https://github.com/CodesWithRobi/EH-Metasploit-for-reconnaissance/assets/130537166/24f85f8d-f911-4951-8bcf-4733c754c982)


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version

![image](https://github.com/CodesWithRobi/EH-Metasploit-for-reconnaissance/assets/130537166/f1525598-74e1-4bed-8b42-ce0161a3a9b9)


Use the set rhosts command to set the parameter and run the module, as follows:
![image](https://github.com/CodesWithRobi/EH-Metasploit-for-reconnaissance/assets/130537166/4282f715-91f9-48a5-8a18-4ab4d687e4cf)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
![image](https://github.com/CodesWithRobi/EH-Metasploit-for-reconnaissance/assets/130537166/12bbbb4f-c3ca-44e5-8016-cbf94c421902)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
> set PASS_FILE /usr/share/wordlists/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
> set RHOSTS <metasploitable-ip-address>

Set BLANK_PASSWORDS to true in case there is no password set for the root account.
>set BLANK_PASSWORDS true
![image](https://github.com/CodesWithRobi/EH-Metasploit-for-reconnaissance/assets/130537166/6695fce9-029d-4321-b5cf-026f1fe618b3)


## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
