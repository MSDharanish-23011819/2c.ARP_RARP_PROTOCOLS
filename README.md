# 2c.SIMULATING ARP /RARP PROTOCOLS
# NAME : DHARANISH MS
# REGISTER NO : 212223240027

## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
### Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
### Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.

## PROGRAM - ARP
### Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"SA:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode()) 
    except KeyError:
        c.send("Not Found".encode())

```
### Server 
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address: ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
### Client
![Screenshot 2024-05-06 134605](https://github.com/MSDharanish-23011819/2c.ARP_RARP_PROTOCOLS/assets/147139454/f031a0be-448e-4b01-b946-4db10f668a15)



### Server 

![Screenshot 2024-05-06 134618](https://github.com/MSDharanish-23011819/2c.ARP_RARP_PROTOCOLS/assets/147139454/fb849671-1ad7-4f91-b177-c5882491e123)


## PROGRAM - RARP
### Client
```
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
### Server
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```

## OUTPUT -RARP
### Client
![Screenshot 2024-05-06 134753](https://github.com/MSDharanish-23011819/2c.ARP_RARP_PROTOCOLS/assets/147139454/a4330a5e-4ce9-4dc0-8a57-74f46a9ed012)


### Server
![Screenshot 2024-05-06 134804](https://github.com/MSDharanish-23011819/2c.ARP_RARP_PROTOCOLS/assets/147139454/3bcb0743-d15a-49a5-9d13-5c39ba5fb15a)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
