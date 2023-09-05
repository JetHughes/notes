---
title: "21-network-accounting-and-visibility"
tags: 
- cosc301
- lecture
sr-due: 2023-08-03
sr-interval: 3
sr-ease: 250
---

> [!INFO] 
> could go into a lot of detila
> three qustions: what is network, accounting. why we need accounting. how do we do accounting.
> always three questions: what, why, how
> before you stufy compsci. e.g., what is it, why do it, how do I do it. without first two questions we don't care about the third one. 
> learn how to learn. normally how takes a lot of time. 
> at uni - better to broaden knowledge. specialise later.  

Business Requirements 
- How to efficiently track network and application resource usage? 
- How to account and bill for resource being utilized? 
- How to effectively plan to allocate and deploy resources most efficiently? 
- How to track customers to enhance marketing customer service opportunities? 
- How to know if customers are adhering to usage policy agreements?

> [!INFO] 
> related to management. relative to management. 
> track customers usage. 
> we need a mechanism to enforce it

Why Account? 
- Usage-based Billing 
	- Charge groups/people for used bandwidth. 
- Peering agreements 
- Security analysis 
	- Provide audit trail for connections, including src/dest addr, protocol, port, time, duration 
- Network monitoring & anomaly detection 
- Network/capacity planning 
- Application monitoring and profiling 
- User monitoring and profiling.

> [!INFO] 
> commercial world - easy to understand why we need it. 
> we need to pay. but how to pay fairly?
> (now we have the overall picture our knowledge can be structured. we can place information into this structure)
> learning is reoganisation of your knowledge in a structured way

What/Who to Account? 
- Subnets 
	- Traffic through router 
	- Useful for demarcation routers, to enable charging to departments. 
- Hosts 
	- Useful when each host is used by a single entity 
- Users 
	- Authenticating proxy 
- Switch ports 
	- Higher implementation cost
	
	> [!INFO] 
	> demarcation routers: routers on the boundary
	> track usage of subnets
	> sometimes computer is shared by multiple users. can have different ports on a switch which are measured separately. need hardware to implement this tracking

Where are we accounting? 
- Datalink Layer 
	- Bad 
	- All Ethernet frames, including broadcast and management 
- Network Layer 
	- Common 
	- includes traffic that may be unwanted. 
	- Charges for IP headers too. 
	- Makes protocols such as SSH very expensive. 
- Application Layer 
	- Common at proxies 
	- fairest from users’ point of view 
	- does not charge for LAN/IP overhead traffic.

> [!INFO] 
> count number of packets
> count ip packets
> count datagrams
> different places to do the accounting
> extra overhead from recording data can be unfairly loaded onto the user.
> normally not suggested at datalink layer
> network layer is better: easier for e.g. cisco to implement tools
> application layer also good.
> stuff to think about (should three way handskates etc be charged to the user)
> you can argue for different methods of accounting

Caching and Charging 
- If a user’s request goes through a proxy, do they still get charged for cache hits? 
	- Is it fair that the first requester gets charged if subsequent users do not? 
	- Similar problems with multicast. 
	- Are you charging for a data product (bytes), or a service (connectivity)? 
- Charge provider or consumer? 
- Consumers want predictable charging.

> [!INFO]
> accesing external website from with university network. uni network proxy server may cache the site.
> does does the user still get charged the second time they acess it?
> similar problem with multicast. e.g., email to mail list with 1000 people, 
> usually charge consumer and provider.

International/Domestic 
- Commercial links may be charged at different rates for different types of traffic. 
- How can we tell whether traffic is international or domestic? 
	- Use a table of known national-IP ranges. 
	- Hard to come by, no standard mechanism. 
	- Processor / memory intensive. 
- Best results comes from routing tables for national routers.

> [!INFO] costly to find out it something is international or domestic.
> need to find a balance between fine-grained vs coarse-grained.
> fine -> make more money, but use more resources

Getting the Data (1) 
- Method 1: Use firewall counters 
	- Put rules at the start of your firewall that match only (no ACCEPT or DROP). 
	- Each rule has byte and packet counters. 
	- What about traffic that would be dropped? Most useful for client-requested data. 
	- Adds to latency. 
	- Cannot acquire a post-capture breakdown of traffic.

> [!INFO] when a firewall recieves traffic it checks all the rules to allow or not a user. also can add checks to find the users an number of bytes and do accounting from it. but this can add latency

Getting the Data (2) 
- Method 2: Capture packet headers 
	- Either listen on a router, or a switch’s mirror port 
	- Flexibility in processing of the packet headers 
		- As in Method 1, there can be problems with respect to NAT. Do you get the packets pre/post NAT? 
		- Again, don’t know if packets get dropped.
> [!INFO] network address translation, convert local to global address
> can have problem if packets get dropped by the router. traffic jam in router ⇒drop packets and resend. still have to pay for dropped packets. 

Capturing Packets 
- Modern (usually managed) switches have a mirror port, in which a copy of every frame that goes through the switch also gets forwarded out the mirror port. 
- For optical networks, fibre splitters can be used. 
- A traffic probe would be attached to the copied data. 
- Unlike router methods, that can be useful for measuring link-local activity, although this is less useful for most accounting

NetFlow 
- Developed by Cisco originally. 
- Primary accounting technology used in industry today. 
	- IPFIX (IP Flow Information Export) is IETF’s standardisation of NetFlow 
	- Different versions export different sorts of values. 
	- Version 5 most common for IPv4. 
	- Version 9 for IPv6. 
- Use UDP as transport

> [!INFO] 
> UDP used to convey accounting information
> need to record every flow in a unidirectional flow

Flow Concept in NetFlow 
- A flow is a unidirectional sequence of packets between a given source and destination, defined by a 7-tuple key consisting of the following fields: 
	- Source IP address 
	- Destination IP address 
	- Source Port 
	- Destination Port 
	- IP Protocol 
	- Ingress interface 
	- IP Type of Service

> [!INFO] first four field uniqely identify the network traffic between the two software entities. e.g., client, web server. 
> ip protocol is: udp, tcp, etc

NetFlow Architecture 
- NetFlow Exporter 
	- observes packet data and creates records from the monitored network traffic and transmits that data to the NetFlow collector. 
- NetFlow Collector 
	- collects the records sent from the exporter, stores them in a local database and forwards the records to an analyzer. 
- NetFlow Analyzer 
	- analyzes the NetFlow records for information of interest, which may include bandwidth usage, policy adherence, and forensic research
![NetFlow Architecture](https://i.imgur.com/Ft2ufcK.png)

> [!INFO] exporter collects the information. collecter stores the data.. storage is in the collector

NetFlow Records 
- The statistical information gathered from the network traffic is placed in a flow record. 
- Each record is stored and managed in NetFlow cache 
	- Once a flow has been created and placed in the cache, it remains active until it expires 
	- After the flow expires, the record is added to a NetFlow Export datagram for transmission to the NetFlow collector 
- A NetFlow record may include many of all of the following statics: 
	- NetFlow version 
	- Flow Sequence (Identifier) 
	- Input and output SNMP indices 
	- Flow size in packets and bytes 
	- Timestamp for flow start and stop times 
	- Layer 3 header data (Source/Destination IP Addresses, IP protocol) 
	- Port Numbers 
	- Type of Service (ToS). 
	- Layer 3 Routing information ( IP address of the next-hop, Source and destination IP masks) 
	- Multiprotocol Label Switching (MPLS) labels (version 9 only) 
	- IPv6 addresses and ports (Netflow version 9 only)
![netflow diagram](https://i.imgur.com/f0CK1BC.png)

![Flow Tracking in NetFlow](https://i.imgur.com/dFb17fh.png)

Radius 
- Remote Authentication Dial In User Service: a user authentication network security and accounting protocol. 
	- Used in port-based systems, such as dial-in, wired or even wireless (WPA Enterprise, 802.1x) 
	- Only accounts for total traffic. Cannot break down traffic into services, different destinations, etc. 
	- runs in the application layer, using UDP as transport

> [!INFO] radius
> used to authentication in wireless networks. also used to accounting as they are user based.

Proxy Caches 
- Because proxies can authenticate users, it is reasonable to use them as user-based accounting points. 
- However, this only covers a fraction of the traffic that could be accounted for on an internet link—e.g. what about peer-to-peer? 
- SOCKS proxies could be more effective.
> [!INFO] e.g., uni saves websites. source of request can be hidden. privacy issue in vocles
> SOCKS - secures socket. 

Connection Logger 
- Used for security history—make a historical record of connections made to the server. 
- Can be useful in dealing with network break-ins, and can be important in supporting legal action. 
- Data should be immutable—send to receive-only station.

Summary 
- What is network accounting? 
- How to perform network accounting? 
- Accounting tools 
	- NetFlow 
	- Radius 
	- Proxy cache 
	- Connection logger