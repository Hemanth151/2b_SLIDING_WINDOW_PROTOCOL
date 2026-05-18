# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## OUPUT
## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
SERVER
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting...")

conn, addr = s.accept()
print("Connected:", addr)

while True:
    data = conn.recv(1024).decode()

    if not data:
        break

    print("Received:", data)

    conn.send(("ACK: " + data).encode())

conn.close()
s.close()
CLIENT
import socket

c = socket.socket()
c.connect(('localhost', 8000))

while True:
    msg = input("Enter message: ")

    if msg == "exit":
        break

    c.send(msg.encode())

    ack = c.recv(1024).decode()
    print("Server:", ack)

c.close()
<img width="803" height="210" alt="image" src="https://github.com/user-attachments/assets/4b720711-7d58-4e23-83b1-9ed05de055ba" />
<img width="788" height="320" alt="image" src="https://github.com/user-attachments/assets/59df3eeb-4f26-4571-b191-01dd6f98cea9" />


