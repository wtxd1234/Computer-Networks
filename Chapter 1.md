# Chapter 1: Computer Networks and the Internet 
## 1.1 What is Internet?
### A Nuts-and-Bolts Description and Services Description

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/24298a85-7844-45f5-be54-96b75bed8333)


- Internet Service Provider (ISP)
  - Provide internet access
  - Examples: Telephone companies

- Host/ End System
  - 2 types:
  1. __Client__: like computer or phone...
  2. __Server/ Data centers__: more powerful machines that store and distribute web pages

- Link
  - Different links, different transmission rate (bits per seconds, bps)
  - Examples: Twisted-pair copper wire, fiber optics, microwaves...

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/e2cac532-1ff1-4194-bd1e-541a8abb55f7)

- Packet
  - Steps: 
  1. Host divide data into _segments_, add _header_ to each segment to generate a _packet_
  2. Destination reassemble packets into data
     - Packets: fundamental unit of data in networks
     - Packet: header + payload
     - Header: it contains network information --- necessary for the network to work
     - Payload: actual data

### What is a Protocol?

- Network protocol
  - Message
    - Format
    - Order
      - Example: TCP connection request → TCP connection response → Get 
\<address\> → \<file\>

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/66b8481e-8f0e-4c2c-b1ab-a824c1159ddf)

## 1.2 The Network Edge
### Access Networks

- Access Networks
  - Connect hosts to edge router
    - Edge router is the ___first router___ in the __global or regional ISPs__
    - Edge router is the ___last router___ in the __mobile network, home network or institutional network__

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/e0657eef-9b26-4a5b-b72c-8bc3fb5f7921)

## 1.3 The Network Core
- 2 types:
1. __Packet Switching__
2. __Circuit switching__

|        |  Packet switching  |  Circuit switching  |
|  ---  |  --- |  --- |
|  Requirement on end-to-end resource reservation  |  No  |  Yes  |
| A source host wants to communicate with a destination host  | It uses resources (e.g., bandwidth) along a path from the source host to the destination host in an on-demand manner.  |  It must _reserve_ resources along a path (called __circuit__ or __dedicated end-to-end connection__) from source host to destination host. The resource must be reserved for the _entire duration of the communication session_.  |
Example  |  Internet  |  Telephone networks  |

### The Network Core: Packet Switching
- Main concept
  -  ___Store-and-Forward Transmission___
    -  Packet switch must receive (store) all bits of a packet, then only it can transmit (forward) the first bit of the packet

- Network performance
  - __Queuing delay__
  - __Packet loss__
