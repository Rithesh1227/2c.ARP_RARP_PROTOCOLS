# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
1.Start the program.

2.Get the frame size from the user
3.To create the address on the user request.
4.To send address to server from the client side.
5.If your address found in the server it will send the required address to client
6.Stop the Program
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
## PROGRAM - ARP
## client.py
```
import socket 
s=socket.socket() 
s.bind(('localhost',8000)) 
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
## server.py
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True:
  ip=input("Enter logical Address : ") 
  s.send(ip.encode()) 
  print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
<img width="1620" height="225" alt="image" src="https://github.com/user-attachments/assets/21548084-0ae5-45b0-99dd-4222c9d29621" />

## PROGRAM - RARP
## client.py
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
## server.py
```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True:
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address", s.recv(1024).decode())
```
## OUPUT -RARP
<img width="1617" height="227" alt="image" src="https://github.com/user-attachments/assets/cb702d95-af60-4e7e-8bc2-6c5aa6e250ef" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
