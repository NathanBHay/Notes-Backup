A network can be broken down into 4 fundamental parts. These being:
- **Client** which gives user access to the network.
- **Server** which stores data or software on the network.
- **Switches** which connect a client to a LAN.
- **Router** which connects to a network.

The types of networks include:
- **Local Area Network** (LAN) which is usually over a small space.
- **Backbone Network** (BN) which connects LANs.
- **Metro Area Network** (MAN) which connects networks over city suburb.
- **Wide Area Network** which connects MANs and BNs.

# Signals
A data signal is a series of oscillating current sent through a cabled connection. These physical signals allow interfacing between devices. There are two types of signals, those being:
- **Analog Signals** which are a continuous $\sin$ wave of electricity that encodes data.
- **Digital** which is a series of [[Number Systems#Binary|binary]] digit signals sent as electricity.
To turn digital data into analog signals is a process called *modulation* and conversely *demodulation* does the opposite. Both happen within the **modem**.

# Protocols
A protocol is a form of language which defines how two application layers talk between each other. Protocols takes the form of **headers** that are added during each [[Networks#Network Layers|network layer]] as to correctly route messages from one physical layer to another physical layer on another network. Each layer adds its own header in a process called **message encapsulation**.

# Network Layersw
To communicate through devices there are a multiple layers of abstraction which for which a message has to go through. Protocols guide this process and allow it to happen.

## Physical Layer
The physical or hardware layer is the lowest level and is concerned with actual hardware. It deals with the network [[Networks#Signals|signals]] which are communicated between devices. Some common network devices which are within the physical layer are:
- **Network Cables** which use a variety of cables as to allow a direction connection between devices.
- **Network Interface Card** which connects devices to a wireless network or through ethernet.

## Data Link Layer
The data link layer defines the interface between hardware and software. It is also responsible for error detection, as it stops **collisions** between packets and re-transmits them if damaged. It determines which device within the network is used. The [[Networks#Protocols|protocol]] used here is is dependent on the devices connection. It encodes the **frame** which contains a **Media Access Control** (MAC) address.

**Ethernet** is the common [[Networks#Protocols|protocol]] used to connect devices within the data link layer. **Media Access Control** in ethernet is based on the **CSMA/CD** method. This is broken down as:
- **Carrier Sense** (CS) where a device listens to the network and starts to transmit when it is silent.
- **Multiple Access** (MA) describes the multiple devices that share the same medium.
- **Collision Detection** (CD) means that while a device is sending it will be ready to stop data before a collision happens.
Ethernet was originally based on a **shared-bus** where all devices were connected through one bus. However, due to this only one device can send at a time, all devices receive all messages, and collision detection limits the size of the network. To solve this a **hub-based** ethernet is used. This solution keeps all data in a **forwarding table** that identifies the order and where all messages are sent within a network. This forwarding table is done through **switches** which uses the MAC address to send packets directly to the destination device.

**Wireless Lan** (WLAN) is a [[Networks#Protocols|protocol]] to connect between devices which uses radio waves as [[Networks#Signals|signals]] between devices. These signals have 13 defined frequencies to operate if within the **2.4 GHz** band. WLAN within the **5 GHz** band has many more frequencies. An **Independent BSS** is a form of WLAN where all devices within a network interface. However, this makes it difficult to get data from outside networks. As a result a **Infrastructure BSS** is commonly used which has a central **Access Point** (AP) which routes messages. WLAN is limited by a need for more **Collision Avoidance** meaning it uses a **CSMA/CA** method to solve issues. This method commonly uses an **ARQ** protocol to ensure collisions didn't happen.

## Network Layer
Network layer is responsible for **routing** between a network. Thus, finding the shortest path from a start to a final location. The [[Networks#Protocols|protocol]] used here is the **Internet Protocol** (IP) which encodes the **packet**.

An IP address is hierarchical with the first two bytes identifying location and the last two being the device within it. Thus each byte defines a unique **subnet**. Each subnet corresponds to a single LAN within a network. These **subnet masks** are written in **dot notation** such as 255.255.255.255, or **CIDR notation** which translates to /32, where the slash is the amount of numbers bits defined for the subnet. This provides a total number of hosts where the number from CIDR notation is the $2 ^{address\;size - subnet} -2$. This provides an address range $Subnet\;address + number\;of\;host$.

There are multiple IP address versions the most popular being:
- **IPv4** which is 32 bits long, thus limited by the amount of combinations.
- **IPv6** which is 128 bits long with 23 bits to identify a *Regional Internet Registry*, another 9 for the *Internet Service Provider*, a further 16 bits to uniquely identify a network, 16 more for subnets and the last 64 for interface IDs within the subnet.

**Doman Name System** (DNS) is responsible for mapping readable addresses to an IP address. This is done through a DNS request to a DNS server which then sends a user to the requested website. **Address Resolution Protocol** (ARP) furthers maps these IP addresses to a MAC address.

A **Router** is the device that is responsible for connecting networks and how packets flows. They use a **routing table** as to make decisions where to send packets within a network. There are two types of routing which are:
- **Static Routing** which prepares a fixed routing table and manually updates when a network changes.
- **Dynamic Routing** where routers build dynamic tables by exchanging information. This is done using a **distance vector** or **link state** algorithm.

## Transport Layer
Transport layer moves the data between networks as to find the final location of the target network. The [[Networks#Protocols|protocol]] used here is the **Transmission Control Protocol** (TCP) which encodes **segments**. This is done by breaking messages up into short segments as to be able to transfer them through the lower layers. To do this a **port** is used to determine which application or process the information goes to.

To establish a connection a **three-way handshake** between the client sending a SYN packet, a server replying with a SYN, ACK and acknowledgement number, and a client sending a ACK with a sequence and acknowledgement number. This connection is then closed with a **four-way handshake** where a client or server sends a **FIN** packet, which is acknowledged with an **ACK** and a **FIN** packet back, thus leading to the original device sending an **ACK** back.

The transport layer also deals with **error control** and corrects them by resending discarded **frames** found within the [[Networks#Data Link Layer|data link layer]] by using the **Automatic Repeat Request** (ARQ). A **TCP packet** includes two numbers the **sequence number**, how many bytes transmitted already, and **acknowledgement number**, how many bytes received from the other side. Through this errors are found if packets are missed.

While **TCP** is the standard it does lead to bigger packets if sending shorter messages. To combat this **User Datagram Protocol** (UDP) is used for smaller messages. Each packets is sent individually and may arrive in any order, thus **connectionless**. As well as **compact** with only 8 bytes compared to 20 for TCP.

## Application Layer
The application layer is the individual bit of software used on the computer. The [[Networks#Protocols|protocol]] used is the **HTTP** protocol which encodes **data**. An application has several types of logic in which it runs. These include:
- **Presentation Logic** is the part of the application that provides the user interface.
- **Application Logic** defines how the application behaves.
- **Data Access Logic** defines how it manages data.
- **Data Storage** defines where the data is kept.
Traditional applications uses all of these however modern apps with network integration have different **application architectures** which define what tasks are performed.

# World Wide Web
The World Wide Web is based on two main protocols. Those being **HTTP** which communicates between browser and server, and **[[HTML]]** which describes a webpage. The user enters a request response cycle where where methods such as *get*, *post* and *head* lead to inputs and outputs within the webpage.

# Email
Email is a form of communication which uses protocols:
- **SMTP** which transfers messages between the client and mail server.
- **POP** which downloads emails to the client.
- **IMAP** where multiple clients can access a mailbox.
- **MIME** which encodes emails and allows unique formatting.
