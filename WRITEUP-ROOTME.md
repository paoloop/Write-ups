TOOLS USED: 

NMAP
GOBUSTER
LINPEAS




THE MACHINE IS ROOTME

For firts thing run the tool name Nmap: 

	nmap -p- IPMACHINE

I foud two ports open wich there are:

	ssh 22

	http 80


enter on the website and run the gobaster 

	gobuster dir -u http://IP:PORT -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt

there are you two directory:

	/panel
	/uploads

in the panel i can upload a file for do the reverse shell and whit uploads i can run it
there is a check for the extansion of file , for bypass i use this taype .php5



Now the need  do escalate our privilage.For do that , we use another tool called linepas.
run this on the machine for extract the information for possible privialge escalation.


it found there is vuln in:

	urs/bin/python 

so we have to use python for open file root.txt

	python -c 'print(open("/root/root.txt").read())'


 
