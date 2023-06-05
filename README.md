# EX-10 APPLICATION USING TCP SOCKETS - FILE TRANSFER PROGRAM


## DATE :10-05-2023

## AIM :
To write a python program for creating File Transfer using TCP Sockets Links.
## ALGORITHM :

```
1.Start the program.
2.Get the frame size from the user.
3.To create the frame based on the user request.
4.To send frames to server from the client side.
5.If your frames reach the server, it will send ACK signal to client otherwise 
  it will sendNACK signal to client.
6.Stop the program
```
## PROGRAM :
```
Developed By: Yashaswi Mitta
Reg No: 212221230062
```
### client:
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    while True:
        print('receiving data...')
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
        f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')

```
### server:
```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename='mytext.txt'
    f = open(filename,'rb')
    l = f.read(1024)
    while (l):
        conn.send(l)
        print('Sent ',repr(l))
        l = f.read(1024)
    f.close()
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
```
## OUTPUT:
![cn 10-1](https://github.com/yashaswimitta/EX-10/assets/94619247/f2ea4f47-defb-490b-8df7-fb3e8c9df258)




## RESULT:
Thus, the python program for creating File Transfer using TCP Sockets Links was successfully created and executed.

