# 2a_Stop_and_Wait_Protocol
## NAME : C.Shrenidhi 
## REGISTER NO : 212223040196 
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
server.py
import socket 

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

print("Server is listening on port 8000...")

c, addr = s.accept()
print("Connection from:", addr)

while True:
    i = input("Enter data: ")
    c.send(i.encode())

    ack = c.recv(1024).decode()   # FIXED: ⁠ -decode() ⁠ → ⁠ .decode() ⁠
    if ack:
        print("Client:", ack)
        continue 
    else:
        c.close()   # FIXED: ⁠ C.close() ⁠ → ⁠ c.close() ⁠
        break

client.py

import socket 

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    data = s.recv(1024).decode()   # FIXED: ⁠ rec ⁠ → ⁠ recv ⁠
    if not data:  # if server closes connection
        break
    print("Server:", data)
    s.send("Acknowledgement Received".encode())


```

## OUTPUT
# Client

![WhatsApp Image 2025-09-03 at 11 29 45_2527db83](https://github.com/user-attachments/assets/81751760-fdf3-4605-bcc2-06726b97e6ed)

# Server

![WhatsApp Image 2025-09-03 at 11 29 22_97bfed8b](https://github.com/user-attachments/assets/283c8187-dce0-454d-9de5-e40aba28abe8)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
