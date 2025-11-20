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
<img width="815" height="648" alt="image" src="https://github.com/user-attachments/assets/c63b135f-d39c-4e34-90cf-d5e61c481548" />


Invoke msfconsole:
## OUTPUT:
<img width="954" height="388" alt="image" src="https://github.com/user-attachments/assets/5b72cbd5-4b5e-478c-b6ae-4bfc6418b1d3" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="1146" height="672" alt="image" src="https://github.com/user-attachments/assets/1f541eb3-1e0c-4306-bfab-58d4de919ae5" />



Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="737" height="418" alt="image" src="https://github.com/user-attachments/assets/f51746be-e904-4fa0-a353-25a57c3d22e9" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="931" height="395" alt="image" src="https://github.com/user-attachments/assets/1485d7a8-6954-4558-9c07-c08506184e63" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
<img width="884" height="510" alt="image" src="https://github.com/user-attachments/assets/c9b1f591-7ff1-4ab2-875f-6ed0e286cd8a" />



Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:
<img width="1734" height="805" alt="image" src="https://github.com/user-attachments/assets/07bc615b-9692-4705-b3ac-592e373c160c" />



The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:




## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="931" height="395" alt="image" src="https://github.com/user-attachments/assets/08b0e09a-aea5-41f7-8ae2-3e6ccfe73748" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="1696" height="458" alt="image" src="https://github.com/user-attachments/assets/eb6fa4c8-6524-418e-ae88-d6d669c9cc10" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="1384" height="273" alt="image" src="https://github.com/user-attachments/assets/728b6eff-bfcb-4f82-b5a6-8bf918e1ffd2" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="1005" height="143" alt="image" src="https://github.com/user-attachments/assets/63827ad0-ffae-49e6-bbbd-489d06adde0f" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:

<img width="1330" height="504" alt="image" src="https://github.com/user-attachments/assets/90484d2a-cdae-41fe-8df5-a67f367fee15" />



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:

<img width="935" height="266" alt="image" src="https://github.com/user-attachments/assets/7f2c8d67-cddf-4135-a6fe-f7af51c5b4f1" />

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
