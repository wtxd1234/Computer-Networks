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
  - Two types
    1. ___Client-server architecture___
![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/83600b26-3a3a-441d-b43c-02ddb5b836eb)
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
![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/544655db-3052-4e43-981f-8db6a21c9f31)
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
