The internet is a [[Networks|network]] of networks which is governed by ISPs which supply the connection between these networks. An ISP's network is usually an **autonomous system**. This autonomous system is connected to others through border routers which defines how traffic flows through the **Border Gateway [[Networks#Protocols|Protocol]]** (BGP). Within an autonomous system interior routers are managed by **Tiered ISPs** which route traffic within their networks. This peering agreement between ISP's usually results in them sharing traffic and an **Internet Exchange Point** (IXP) which connects to the wider web.

The **Internet of Things** refers to the concept of connecting smaller, non computer devices to the internet. This allows automation through differing technologies being connected.

# Internet Access
Internet access is done through end users making a physical connection to an ISP network through the following internet access technologies:
- **Asymmetric Digital Subscriber Line** (ADSL) compromises between analog telephone and digital networks. It is the highest cost and needs an individual cable for each user, as a result telephone cables are commonly used. These ADSL lines send data asymmetrically to a DSL Access Multiplexer to split the voice and data signals within the telephone line.
- **Fibre Optic** is commonly seen as the fastest due to its use of light as to transfer signals. Australia uses a **National Broadband Network** which promises fibre to premises and fibre to node connection.
- **Mobile Data** makes up around a third of internet traffic. This is commonly done through 4G antennas which are operated by ISPs who provide WIFI to large areas at a speed of theoretically 1Gbit/s. It splits areas up into cells which can be seamlessly traversed. 5G is a newer standard which has a 10Gbit/s data rates with higher frequencies than 4G.

After this the ISP **authenticates** user for security and billing purposes, which it then assigns an **IP Address** to the new device. It then informs the device about the IP address of the routers and the DNS servers to use. Once this is done it has become a part of the internet.

This internet access is spread through **load balancing**. This allows multiple devices to run simultaneously over large bits of data. This data is also **cached** as to allow commonly accessed websites to be routed quicker. Load balancing solves the issue of distributing requests across servers however, a **Content Delivery Network** (CDN) is used to operate servers in multiple locations and supply the data.

# Internet Governance
No single organisation governs the internet, however the most prominent organisations are:
- Internet Society (ISOC
	- Internet Architecture Board (IAB)
	- Internet Engineering Task Force (IETF)
	- Internet Engineering Steering Group (IESG)
	- Internet Research Task Force (IRTF)
- Internet Corporation for Assigned Names and Number (ICANN) which deals with IP addresses and host names.
- Internet Governance Forum (IGF) which deals with stakeholders in the internet.
- International Telecommunication Union (ITU) which deals with hardware standards.

**Net Neutrality** is a concept within internet governance which seeks to stop ISPs' influence on what can be accessed, and how fast it can be by the user. While the internet probably shouldn't be 100% neutral as certain datatypes should be prioritised, it still offers a perspective on how ISPs should conduct themselves.
