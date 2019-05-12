# Socket programming
### Communication between client and server over wireless TCP/UDP protocols

## What is NSLookup?
- Name server Lookup
- Obtain domain name
- IP address mapping
- DNS records


###### All the files are jupyter notebooks. Instead of creating pyton files, you can chose to run the notebooks as they are.

## 1. Perform nslookup with python script:
Follow the instrunctions to perform nslookup with python
1. ```git clone https://github.com/Adhira-Deogade/Client_Server-communication.git```
2. Copy the code in [*nslookup.ipynb*](nslookup.ipynb)
3. Create a new python file named "nslookup.py"
4. ```nano nslookup.py```
5. Paste the code and exit the file (Ctrl+O and Ctrl+X)
6. ```python nslookup.py "webite name"``` (Eg. ```python nslookup.py gmail.com```)

You will obtain the server that yuor computer is connected to and the port number
You will also obtain the server to which your server is communicating in order to obtain information from gmail.com (Non-suthoritative)

## 2. Open a web browser and a website with Linux and python
1. Run the code in [Webbrowser.ipynb](WebBrowser.ipynb)
2. ```webbrowser.get(chrome_path).open(url, new=2)``` where
    - *chrome_path* is the path to chrome applciation
    - url: url to be opened (here "gmail.com")
    - *new=2* indicates to open a new tab
  
## 3. Creating a client-server communication with User Datagram Protocol(UDP)
  ### 1. Creating [UDP server](UDPserver.ipynb)
   1. ```socket.socket(socket.AF_INET, socket.SOCK_DGRAM)``` 
   creates a socket with following specifications:
      - ```AF_NET``` defines an IPv4 connection
      - ```SOCK_DGRAM``` defines datagram for User Datafram Protocol
   2. ```ServerSocket.recvfrom(2048)``` obtains client's address and its message
   3. ```ServerSocket.sendto(modifiedmessage,ClientAddress)``` Sends modified data to client address
    When the server is ready to receive data, start the client
    
  ### 2. Creating [UDP client](UDPclient.ipynb)
   1. ```ClientSocket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)``` Create socket for client with same configuration as server (IPv4 and datagram)
   2. ```ClientSocket.sendto(message,(ServerName,ServerPort))``` Send data to server address
   3. ```ClientSocket.close()``` Close the socket
    
## 4. Creating a client-server communication with Transmission Control Protocol(TCP)
  ### 1. Creating [TCP server](TCPserver.ipynb)
   1. ```serverSocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)``` creates a socket with following specifications:
      - ```AF_NET``` defines an IPv4 connection
      - ```SOCK_STREAM``` defines streams of data for Transmission Control Protocol
   2. ```serverSocket.bind(ServerAddress)``` Associates server port number with socket
   3. ```serverSocket.listen(1)```Waits for some client to knock on the socket door (defines maximum number of queued connections (atleast 1)
    4. ```connection_socket, addr = serverSocket.accept()``` Create a connection socket
    3. Receive, update and send the modified message back to client address. Close the connection
  
  ### 2. Creating [TCP client](TCPclient.ipynb)
   1. ```ClientSocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)``` Create socket for client with same configuration as server (IPv4 and streams)
   2. ```clientSocket.recvfrom(2048)``` Keep receiveing information from server
   
   
## Exercise
##### Write a python code such that -> Client will continuously provide mathematical problems, while server will keep solving them

1. Create a [TCP server](assgn_server.ipynb)
2. On receving the math problem, solve it with ```modified_message = eval(message)```
3. Create a [TCP client](assgn_client.ipynb)
4. Send math query to server with ```str(raw_input('Enter the lower case message: '))```


##### Always, first start the server and then the client
