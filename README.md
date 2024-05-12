# Ex No:4 Execution of Network Commands
# Name: NARESH.R
# Reg No: 212223240104
## AIM:
Use of Network commands in Real Time environment
## Software:
Command Prompt And Network Protocol Analyzer
## Procedure: 
To do this EXPERIMENT- follows these steps:
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
### PING COMMAND:
#### Client.py:
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
#### Server.py:
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

## OUTPUT:
## PING COMMAND:
### Client Window:
![Screenshot 2024-04-20 002515](https://github.com/SriVignesh-G/4.Execution_of_NetworkCommends/assets/147576510/3d05709e-36b9-48f9-9b80-8bc91922d7ce)

### Server Window:
![Screenshot 2024-04-20 002523](https://github.com/SriVignesh-G/4.Execution_of_NetworkCommends/assets/147576510/c45d2b4f-2c3b-4c07-abb4-087e25049fe2)

## TRACEROUTE COMMAND:
![Screenshot 2024-04-20 003241](https://github.com/SriVignesh-G/4.Execution_of_NetworkCommends/assets/147576510/8ef0ea0a-5f02-48c2-b1bf-24d6ff1bd02b)


## Result
Thus Execution of Network commands Performed. 
