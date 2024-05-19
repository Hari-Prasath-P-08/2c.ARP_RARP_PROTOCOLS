# 2c.SIMULATING ARP /RARP PROTOCOLS

### Name: HARI PRASATH. P
### Reg. No: 212223230070

## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP:

### Client Side:

```python

import socket
s=socket.socket()
s.bind(('localhost',80))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())
```

### Server Side:

```python
import socket
s=socket.socket()
s.connect(('localhost',80))
while True:
   ip=input("Enter logical Address : ")
   s.send(ip.encode())
   print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP:

![322833698-9a658380-1dd7-47f6-b410-59d1bc177f17](https://github.com/Hari-Prasath-P-08/2c.ARP_RARP_PROTOCOLS/assets/139455593/220b504d-f868-4448-ba05-b79f52da0fce)

## PROGRAM - RARP:

### Client Side:

```python
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())
```

### Server Side:

```python
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP:

![322834297-9e330176-c32d-4b95-ba20-5fd79bdacd02](https://github.com/Hari-Prasath-P-08/2c.ARP_RARP_PROTOCOLS/assets/139455593/0822aac9-a08d-4900-9626-88cf1d136c87)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
