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
## Client:
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
## Server:
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000))
while True:    
    print(s.recv(1024).decode()) 
    s.send("acknowledgement recived from the server".encode())
```

## OUTPUT
## Client:
![439242434-76d12c49-730d-4a2d-83c5-ba5b20509257](https://github.com/user-attachments/assets/e25e0b23-3d37-483d-a677-a658948d8758)
## Server:
![439242615-da5f375d-53c5-4c85-9920-825a0cacd060](https://github.com/user-attachments/assets/b6c81bcf-8457-4fdf-ae3f-e8249fa94c7c)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
