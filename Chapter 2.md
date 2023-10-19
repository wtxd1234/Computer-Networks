# Chapter 2: Application Layer
## 2.1 Principle of Network Applications

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/d1f5cd92-9de8-4cfb-a22f-5275fe4e9468)

- Examples of Applications
  - Web and HTTP
  - Domain Name System (DNS)
  - Peer-to-peer applications
- Applications run on a host
  - Not network core
    - No need to write software for network core
      - The network core doesn't run user applications
- Application Architecture
  - 2 types
    1. ___Client-server architecture___
<br>![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/83600b26-3a3a-441d-b43c-02ddb5b836eb)
       - __Server__
         - Characteristic
           - Always-on host
           - Has a permanent IP address
           - Data center
             - Comprised of hundreds to thousands of servers to serve all requests from clients
         - Function
           - Service requests from clients
       - __Client__
         - Characteristic
           - May have dynamic IP addresses
           - Do not communicate directly with each other
         - Function
           - Send a request to the server
       - Example
         - Web server (server) service request from a browser (client)
           - Browsers do not communicate directly with each other
    2. ___Peer-to-peer architecture___
<br>![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/544655db-3052-4e43-981f-8db6a21c9f31)
       - __Peer__
         - Characteristic
           - Hosts communicate directly with each other
           - No always-on host
         - Function
           - Peer request service from other peers, then provide service to other peers
       - Advantage
         - __Self-scalability__
           - New peers provide service to other peers
         - Low cost
           - An expensive server is not necessary
       - Example of applications
         - File sharing (BitTorrent)
         - Internet Telephony (Skype)

## 2.1 Processes Communicating

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/19835f54-e893-4457-afc9-4f32bc2a04d8)

- __Process__
  - Program running within a host
  - Processes in different hosts communicate by exchanging __messages__
    - Hosts are uniquely identified by IP address (e.g.: 128.119.245.12)
    - Process is uniquely identified by the port number (e.g.: 80)
    - Example: Client process in browser sends a request to a server process in web server
- __Socket (Application Programming Interface, API)__
  - Software interface
    - Process sends and receives messages to/from its socket
    - Between the application layer and transport layer

## 2.2 Web and HTTP
- __HyperText Transfer Protocol (HTTP)__
  - __Application layer__ protocol for web page
  - Web page consists 
    - Base HTML file
    - Object
      - HTML file
      - JPEG image
    - Base HTML file and object are identified by __URL (host name and path name)__
  - Client-server model
    - __client__: Web browser requests, receives and displays Web objects 
      __server__: Web server sends objects in response to requests
  - Two types of messages
     1. HTTP request
     2. HTTP response
  - Use __TCP__
    - Client (browser) initiate TCP connection (creates socket) using port 80 to server
    - Server (web server) accepts TCP connection from client
    - HTTP messages (application-layer protocol messages) exchanged between client and server
    - TCP connection closed
  - Is __stateless__
    - Server maintain no information about past client requests
  - 2 types of connections
    1. ___Non-persistent HTTP connection___
       - Send at most one object over a single TCP connection, then close the connection
       - Require multiple connections to download multiple objects
    2. ___Persistent HTTP connection___
       - Send multiple objects over a single TCP connection, then close the connection
       - Require a single connection to download multiple objects

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/a7327458-13d9-4432-950c-85f5d001d934)

### HTTP Connections: Non-Persistent Connection
![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/d3b482b2-aa95-46f0-988f-779ce05123ef)

- ___Round-Trip Time (RTT)___
  - Time for a packet to travel from client to server and then back to client
- ___HTTP Response Time = 2RTT + File Transmission Time___
  - one RTT to setup TCP connection
  - one RTT for the exchange of HTTP request and HTTP response
  - File transmission time
- Disadvantage
  - Require multiple connections to download multiple objects
    - HTTP response time for each object
    - Solution
      - Client setup parallel TCP connections to receive objects simultaneously

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/86ad74ac-b027-4181-8404-bd752e174550)

### HTTP Connections: Persistent Connection
- Persistent HTTP connection
  - Server leaves connection open after sending HTTP response.
    - Subsequent HTTP messages between same client and server sent over the connection
    - The connection close whenever it is not used for a certain time
  - Use __pipelining__
    - Client can send HTTP request and receive HTTP response simultaneously
  - As little as one RTT for all the referenced objects

#### HTTP Message Format: HTTP Request
![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/703997e0-ccb1-4ab5-846b-9dd97d2076d5)

#### HTTP Message Format: HTTP Response
![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/1d2909d1-f4e2-4893-a1b5-663ffa5035f6)

## 2.3 Web Caching
- ___Web cache (Proxy server)___
  - Store recently requested object in its storage 
    - Satisfy client request without involving origin server
  - Client (browser) send HTTP request to cache 
    - Cache return object if it is in the cache
    - Cache request object from origin server if it is not in the cache
  - Advantage 
    - Reduce response time for client request
    - Reduce traffic 
    - Enable effective content delivery

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/219ebbd9-5b70-42b6-a645-793ec6aa117b)

### Caching Example (1/3)
![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/9d1b6297-eaf7-40a0-b8ef-670044fd464d)

### Caching Example (2/3): Increase Access Link
![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/f7f1df46-33b2-44db-8a7c-d13932bb5fdf)

### Caching Example (3/3): Install Web Cache
![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/18be731f-af18-4a39-a6f5-4641628bac69)

## 2.4 Domain Name System (DNS)
- Main function
  - __DNS server translate hostname to IP address__
    - E.g.: cnn.com = 121.7.106.83
- Characteristic
  - A hierarchy of DNS servers as __distributed database__
    - Why __not centralized__?
      - Single point of failure
      - High traffic volume
      - High delay 
        - DNS server may be __far from DNS client__
      - High maintenance
        - Large record for all hostname

### How DNS Works: A Distributed, Hierarchical Database
![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/28bb8f77-48d5-4f07-8fe9-c042faa9dd44)

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/5065181d-f5b2-40d3-b9a3-e85bc5ab78d8)

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/94d65f09-9a3c-4639-a303-ebc54f13d3fa)

### How DNS Works: DNS Caching
- ___DNS caching___
  - Objective
    - __Reduce number of DNS message__
    - __Improve delay performance__
  - Function
    - Local DNS server 
      - Store mapping of hostname and IP address in cache
      - Retrieve cached IP address
        - So, reduce visits to root name servers 
  - Cache entry timeout (disappear) after some time (e.g. two days)
    - So, out-of-date cache entry is removed

## 2.5 Peer-to-peer Applications: Client-Server vs. Peer-to-peer Architecture
![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/25895746-e2d6-473a-ad71-ea85c21012c4)

### Peer-to-peer Applications:Distribution Time for Client-Server Architecture
![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/9c678236-1ef6-4d8f-82e8-46db68b81c12)

### Peer-to-peer Applications:Distribution Time for Peer-to-peer Architecture
![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/b0c82b78-fdd2-46b2-84a9-c31ae4bfa10c)
