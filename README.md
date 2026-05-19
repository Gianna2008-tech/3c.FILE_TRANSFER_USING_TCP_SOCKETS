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
## client
```import socket

s = socket.socket()
host = socket.gethostname()
port = 60000

s.connect((host, port))
s.send("Hello server!".encode())

with open("received_file.txt", "wb") as f:
    while True:
        print("Receiving data...")
        data = s.recv(1024)

        if not data:
            break

        f.write(data)

print("Successfully received the file")

s.close()
print("Connection closed")
```
server
```
import socket

port = 60000
s = socket.socket()
host = socket.gethostname()

s.bind((host, port))
s.listen(5)

print("Server waiting for connection...")

while True:
    conn, addr = s.accept()
    print("Connected with", addr)

    data = conn.recv(1024)
    print("Server received:", data.decode())

    filename = "mytext.txt"

    f = open(filename, "rb")
    data = f.read(1024)

    while data:
        conn.send(data)
        data = f.read(1024)

    f.close()
    print("Done sending")

    conn.close()
```
## OUPUT
<img width="942" height="491" alt="Screenshot 2026-05-19 205801" src="https://github.com/user-attachments/assets/35a6b79c-03d1-4681-a41e-f0c179b1ed7d" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
