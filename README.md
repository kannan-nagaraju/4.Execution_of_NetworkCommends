# 4.Execution_of_NetworkCommands:
#### NAME:N.KANNAN
#### REGISTER NO:212223230097
#### DEPARTMENT:AI&DS
## AIM :Use of Network commands in Real Time environment:
## Software : Command Prompt And Network Protocol Analyzer:
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

## PROGRAM:
## CLIENT:
```
import socket
from pythonping import ping
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
while True:
    c,addr=s.accept()
    print("Connecting from ",addr)
    try:
        hostname=c.recv(1024).decode().strip()
        if hostname:
            try:
                response=str(ping(hostname,verbose=True))
                c.send(response.encode())
            except Exception as e:
                c.send("ping failed  {}".format(e).encode())
        else:
            c.send("Hostname not provided".encode())
    except Exception as e:
        print("Error: ",e)
    finally:
        c.close()
```
## SERVER;
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
try:
    while True:
        ip= input("Enter Website u want to ping :")
        s.send(ip.encode())
        response=s.recv(1024).decode()
        if response:
            print ("Ping result :",response)
        else:
            print ("No response from server")
except Exception as e:
    print ("Error:", e)
finally:
    s.close()
```
## TRACEROUTE COMMAND:
```
from scapy.all import* 
target = ["www.google.com"] 
result, unans = traceroute(target,maxttl=32) 
print(result,unans)
```

## Output:
## CLIENT:
![image](https://github.com/kannan-nagaraju/4.Execution_of_NetworkCommends/assets/145742755/b352d552-45e7-4604-b54d-f91685993d56)
## SERVER:
![image](https://github.com/kannan-nagaraju/4.Execution_of_NetworkCommends/assets/145742755/32814358-614e-45da-a0db-e9928d2c6366)
## TRACEROUTE COMMAMD:
![image](https://github.com/kannan-nagaraju/4.Execution_of_NetworkCommends/assets/145742755/0b57ff48-5b9b-4dd8-8305-1ced7e3d8103)

## Result:
Thus Execution of Network commands Performed.
