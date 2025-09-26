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
## SERVER.PY

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

## CLIENT.PY

```
import socket
s=socket.socket()
s.connect(('localhost', 8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement received from the server".encode())
```


## OUPUT

## SERVER:
<img width="1462" height="753" alt="exp2bs py" src="https://github.com/user-attachments/assets/6cfc3b1a-7f1b-48ca-a31a-eb5f5434233b" />

## CLIENT:
<img width="1467" height="752" alt="exp2bc py" src="https://github.com/user-attachments/assets/c306cc59-336f-4a90-8de7-bce86ac16981" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
