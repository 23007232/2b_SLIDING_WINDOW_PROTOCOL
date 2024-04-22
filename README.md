# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
To implent the program for the implementationof sliding window protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
CLIENT
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
   while(i<len(l)):
    st+=s
    c.send(str(l[i:st]).encode())
    ack=c.recv(1024).decode()
    if ack:
       print(ack)
       i+=s

```
SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```
## OUTPUT:
SERVER:
![image](https://github.com/23007232/2b_SLIDING_WINDOW_PROTOCOL/assets/139115574/b0483f80-5782-413d-bc12-527010e0a5bf)

CLIENT:
![image](https://github.com/23007232/2b_SLIDING_WINDOW_PROTOCOL/assets/139115574/925a6ca4-2a52-4b41-b9d5-52b60f14a8e3)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
