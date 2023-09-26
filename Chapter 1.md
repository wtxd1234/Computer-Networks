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
| A source host wants to communicate with a destination host  | It uses resources (e.g., bandwidth) along a path from the source host to the destination host in an on-demand manner.  |  It must _reserve_ resources along a path (called __circuit__ or __dedicated end-to-end connection__) from source host to destination host. <br><br>The resource must be reserved for the _entire duration of the communication session_.  |
Example  |  Internet  |  Telephone networks  |

- switching
  1. Switching from one router to the other
     - switch from one network to the other
     - switch btw different network devices
     - e.g.: packet & circuit
  2. Switching depend on:
     - Efficiency & Intelligence
       - Efficiency: use less amount of resources
       - Intelligence: able to choose the most suitable path to transmission
  
- bandwidth: range of frequencies which include the information to transmit (it is a type of resource)

### The Network Core: Packet Switching
- Main concept
  -  ___Store-and-Forward Transmission___
      -  Packet switch must receive (store) all bits of a packet, then only it can transmit (forward) the first bit of the packet

- Network performance
  - __Queuing delay__
  - __Packet loss__
- Suppose Host A and B are sending packets to Host E. Hosts A and B first send their packets along 10 Mbps links to the first router. The router then directs these packets to the 1.5 Mbps link. If, during a short interval of time, the arrival rate of packets to the router exceeds 1.5 Mbps, congestion拥塞/过剩 will occur at the router as the queue becomes full. This increases _queuing delay_ and _packet loss_.

```
Just imagine that parking is limited parking while you're finding parking.
Parking is full then you cannot park there.
This is the idea of PACKET LOSS.

To get parking, you have to wait for parking.
The more cars in the parking, you need to queue for a longer time.
This is the idea of QUEUING DELAY.

```


![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/5d11eeb2-cf06-427b-ae3b-0921ab533f6c)

- __Routing protocol__
  - Each router __determine the shortest path to each destination__ and __use the shortest path to configure its forwarding table__

- __Forwarding table__
  - Each host __has IP address__. Each router uses a forwarding table __to map a destination IP address to one of its outgoing links__.

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/b14d7ef9-470e-469b-8aaf-16718669eef8)

### The Network Core: Circuit Switching
- 2 types:
1. ___Frequency-Division Multiplexing (FDM)___
   - A link dedicate a frequency band to each connection
     - The width of the frequency band indicate bandwidth
     - Example: 4kHz
2. ___Time-Division Multiplexing (TDM)___
   - A link dedicate one time slot in every frame to each connection
     - Note:
     1. Time is divided into fixed duration frames
     2. Each frame is divided into a fixed number of time slots

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/bff08018-8085-4c23-8bb8-399185e8258b)

|      | Packet switching | Circuit switching |
| --- | --- | --- |
| Performance Efficiency | Higher<br>&bull;No reservation<br>&emsp;&bull;More sharing of link capacity | Lower<br>&bull;Require reservation<br>&emsp;&bull;Reserved resources may not be fully utilized<br>&emsp;&bull;Reserved resources may not be sufficient<br>&emsp;&emsp;&bull;Underutilized reserved resources cannot be used for other packets |
| Packets need to wait at queue? | Yes<br>&bull;There is variable and umpredictable delay<br>&bull;Not suitable for real-time service | No<br>&bull;Reserved resource provides guaranteed constant rate |
| Complexity | Lower | Higher<br>&bull;Reservation requires end-to-end signaling protocol |
| Cost Efficiency | Higher<br>&bull;No reservation<br>&emsp;&bull;Less cost involve | Lower |
| Popularity | More popular | Less popular |

### Overview of Delay in Packet-Switched Networks

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/92fb043e-8a53-46a3-9887-b04b334b45a0)

### Queuing Delay and End-to-end Delay

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/66328573-9680-44ac-a246-a7956667f265)

### Packet Loss and Throughput

- ___Packet Loss___
  - Packets arriving at a __full queue__ will cause __packet drop__
    - Lost packet may be __retransmitted__

- ___Throughput吞吐量___ (Only counted only when the transmission is successful)
  - __Rate__ (bits/seconds) at which bits are transferred between 
__source host and destination host__
  - 2 types
    - ___Instantaneous瞬间 throughput___
      - Rate at a __given point in time__
    - ___Average throughput___
      - Rate over a __longer period of time__

- ___Bottleneck link___ (slowing down the speed)
  - Link on end-to-end path that constraints end-to-end throughput
  - What is the bottleneck bandwidth in each of the following scenarios?
    - __min{ R<sub>c</sub>, R<sub>s</sub>}__
  - What is the end-to-end delay in each of the following scenarios?
    - __F / min{ R<sub>c</sub> , R<sub>s</sub>}__
   
![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/06f24d1e-a18a-4a78-b77a-20dbb63c9957)

- ___Internet___
  - What is the end-to-end delay in the following scenario?
    - For a particular connection, the end-to-end delay is F / min{ R<sub>c</sub>, R<sub>s</sub>}. This is because, 
in Internet, R >> R<sub>s</sub> and R >> R<sub>c</sub>, and so the bottleneck link occurs at the access network

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/f7a64ee3-c50d-4c0b-af61-cf6470898926)

### Protocol Layers and Their Service Models

- Protocol stack
  - Two types
    - ___Internet Protocol Stack___
    - ___ISO Open Systems 
Interconnection (OSI) 
Reference Model___
- Each layer
  - Perform certain actions
  - Use services of the layer directly 
below it
- Layering 
  - Divide a complex system into layers
  - Advantage
    - Can maintain and update each 
layer without affecting the 
entire system
  - Disadvantage
    - Similar functions in more than 
one layer
      - E.g.: error recovery in the link 
layer and network layer

![image](https://github.com/wtxd1234/Computer-Networks/assets/41671135/70c5a9aa-c2cd-4f55-a556-c2ace89a890c)

### Layered Architecture

| Layer | Packet | Functions |
| --- | --- | --- |
| Application Layer | Message | &bull;Support network applications<br> &bull;Provide Domain Name System (DNS)<br> &emsp;&bull;Translate address (e.g., www.ietf.org to 32-bit address)<br> &bull;Examples: HTTP, email |
| Transport Layer | Segment | &bull;Break a long message into shorter segment<br>&bull;Reduce source host transmission rate during congestion<br>&bull;Examples: transmission control protocol (TCP), user datagram protocol (UDP) |
| Network Layer | Datagram | &bull;Determine routes between source host and destination host<br>&bull;Example: IP Protocol|
| Link Layer (Ethernet, WiFi) | Frame | &bull;Transmit frame from a transmitting host to a receiving host over one link<br>&bull;Example: Ethernet, WiFi | 
| Physical Layer | Bit | &bull; Transmit bits on physical media (e.g., wireless, fiber optic) | 
