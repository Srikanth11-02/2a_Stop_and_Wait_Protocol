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
CLIENT:
```
import socket

# Create socket
s = socket.socket()

# Connect to server
s.connect(('localhost', 8001))

while True:
    # Receive data from server
    data = s.recv(1024).decode()

    if not data:
        break

    print("Server:", data)

    # Send acknowledgment
    s.send("Acknowledgement Received from the Client".encode())

s.close()
```
SERVER
```
import socket

# Create socket
s = socket.socket()

# Bind host and port
s.bind(('localhost', 8001))

# Listen for connection
s.listen(5)

print("Waiting for connection...")

# Accept client connection
c, addr = s.accept()
print("Connected to:", addr)

while True:
    data = input("Enter a data: ")

    # Send data
    c.send(data.encode())

    # Receive acknowledgment
    ack = c.recv(1024).decode()

    if ack:
        print("Client:", ack)
    else:
        break

c.close()
s.close()
```
## OUTPUT
<img width="1191" height="356" alt="image" src="https://github.com/user-attachments/assets/4d109bac-4e39-4606-88de-c84064f77a06" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
