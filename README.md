# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
## SERVER
```
# fileserver.py

import socket

# Create socket
server = socket.socket()

# Bind IP and port
server.bind(("127.0.0.1", 5555))

# Listen for client
server.listen(1)

print("Server waiting for connection...")

# Accept client
client, addr = server.accept()

print("Connected to:", addr)

# Ask filename
filename = input("Enter file name to send: ")

try:
    # Open and send file
    with open(filename, "rb") as file:
        data = file.read()
        client.send(data)

    print("File sent successfully")

except FileNotFoundError:
    print("File not found")

# Close connections
client.close()
server.close()
```
## CLIENT
```
# fileclient.py

import socket

# Create socket
client = socket.socket()

# Connect to server
client.connect(("127.0.0.1", 5555))

# Save file name
save_name = input("Enter name to save file: ")

# Receive data
data = client.recv(1000000)

# Save file
with open(save_name, "wb") as file:
    file.write(data)

print("File received successfully")

# Close connection
client.close()
```
## OUPUT
## SERVER
<
  
<img width="1114" height="219" alt="image" src="https://github.com/user-attachments/assets/9fc27667-1ab9-4d33-94d5-8eab650cd17f" />



## CLIENT 


<img width="1135" height="171" alt="image" src="https://github.com/user-attachments/assets/ed105dd3-d5e7-4e39-9f10-d44706ef9603" />


## FILE
## SERVERSIDE
<img width="1531" height="827" alt="image" src="https://github.com/user-attachments/assets/3072a74d-da4f-482e-a62d-09f0b56c5c98" />


## CLIENTSIDE
<img width="1484" height="755" alt="image" src="https://github.com/user-attachments/assets/770b262a-1c90-4162-bec3-b32e5f3f9554" />


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
