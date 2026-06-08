# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links

## ALGORITHM:
### Server Algorithm
1. Start the program.
2. Create a TCP socket.
3. Bind the socket to a host address and port number.
4. Listen for incoming client connections.
5. Accept a client connection.
6. Open the file to be transferred in read mode.
7. Read the file contents.
8. Send the contents to the client through the socket.
9. Close the file.
10. Close the connection.
11. Stop the program.
### Client Algorithm
1. Start the program.
2. Create a TCP socket.
3. Connect to the server using the server IP address and port number.
4. Receive the file data from the server.
5. Create a new file.
6. Write the received data into the file.
7. Close the socket connection.
8. Stop the program.
   
## PROGRAM
### server.py
```py
import socket

# Create socket
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind address and port
server.bind(('localhost', 8000))

# Listen for client
server.listen(1)

print("Waiting for client connection...")

conn, addr = server.accept()

print("Connected to:", addr)

# Open file and send contents
with open("sample.txt", "rb") as file:

    data = file.read()

    conn.sendall(data)

print("File Sent Successfully")

conn.close()
server.close()
```
### client.py
```py
import socket

# Create socket
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to server
client.connect(('localhost', 8000))

# Receive file contents
data = b''

while True:

    packet = client.recv(1024)

    if not packet:
        break

    data += packet

# Save received file
with open("received_file.txt", "wb") as file:

    file.write(data)

print("File Received Successfully")

client.close()
```

## OUPUT
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/1eb6cff5-bf2e-49d8-b79b-7934559180d6" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
