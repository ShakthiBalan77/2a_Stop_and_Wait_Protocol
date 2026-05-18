# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
Server Code:
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

print("Waiting for connection...")
c, addr = s.accept()
print(f"Connected to {addr}")

while True:
    i = input("Enter data to send: ")
    c.send(i.encode())

    ack = c.recv(1024).decode()
    if ack:
        print("Client:", ack)
    else:
        c.close()
        break
```
```
Client Code:
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    data = s.recv(1024).decode()
    if data:
        print("Server:", data)
        s.send("Acknowledgement Received".encode())
    else:
        s.close()
        break
```
## OUTPUT
<img width="1397" height="953" alt="image" src="https://github.com/user-attachments/assets/c0b4595a-fa67-4112-9d84-9d41d81017e3" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
