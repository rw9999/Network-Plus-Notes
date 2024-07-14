# The Open Systems Interconnection Specifications

The OSI model has seven hierarchical layers that were developed to enable different networks to communicate reliably between disparate systems.

#

### Internetworking Models

In the very first networks, the computers involved could communicate only with other computers made by the same manufacturer. For example, companies ran either a complete DECnet solution or an IBM solution—not both together.

In the late 1970s, the **Open Systems Interconnection (OSI)** reference model was created by the International Organization for Standardization (ISO) to break through this barrier.

The OSI model was meant to help vendors create interoperable network devices and software in the form of protocols, or standards, so that different vendors’ networks could become compatible and work together.

The OSI model is the primary architectural model for networks. It describes how data and network information are communicated from an application on one computer through the network media to an application on another computer. The OSI reference model breaks this approach into layers.

#

### The Layered Approach

Basically, a **reference model** is a conceptual blueprint of how communications should take place.

It addresses all the processes required for effective communication and divides these processes into logical groupings called **layers**. 

When a communication system is designed in this manner, it’s known as **layered architecture**.

Software developers can use a reference model to understand computer communication processes and see exactly what must be accomplished on any one layer and how.

In other words, if I need to develop a protocol for a certain layer, I only need to focus on that specific layer’s functions. I don’t need to be concerned with those of any other layer because different protocols will be in place to meet the different layers’ needs.

The technical term for this idea is **binding**. The communication processes that are related to each other are bound, or grouped together, at a particular layer.

#

### Advantages of Reference Models

The OSI model is hierarchical, and I’d like to point out that the same beneficial characteristics can actually apply to any layered model, such as the TCP/IP model.

Understand that the central purpose of the OSI model, and all networking models, is to allow different vendors’ networks to interoperate smoothly.

This short list depicts some of the most important advantages we gain by using the OSI layered model:

- The OSI model divides network communication processes into smaller and simpler components, thus aiding component development, design, and troubleshooting.

- It allows multiple-vendor development through the standardization of network components.

- It encourages industry standardization by defining the specific functions that occur at each layer of the model.

- It allows various types of network hardware and software to communicate.

- It prevents changes in one layer from affecting other layers, facilitating development and making application programming much easier.

## The OSI Reference Model

One of the greatest functions of the OSI specifications is to assist in data transfer between disparate hosts regardless of whether they’re Unix/Linux, Windows, or macOS based.

But keep in mind that the OSI model isn’t a physical model; it’s a conceptual and comprehensive yet fluid set of guidelines, which application developers utilize to create and implement applications that run on a network. 

It also provides a framework for creating and implementing networking standards, devices, and internetworking schemes.

The OSI model has seven layers:

- Application (layer 7)
- Presentation (layer 6)
- Session (layer 5)
- Transport (layer 4)
- Network (layer 3)
- Data Link (layer 2)
- Physical (layer 1)

![image](https://github.com/user-attachments/assets/2d2e9722-2e4e-4e7b-97b6-0fa30d161858)

The OSI’s seven layers are divided into two groups.

The top three layers define the rules of how the applications working within host machines communicate with each other as well as with end users.

The bottom four layers define how the actual data is transmitted from end to end.

![image](https://github.com/user-attachments/assets/030bb5d8-b003-48f3-8b6d-731ba6f7eba1)

![image](https://github.com/user-attachments/assets/42482812-4eff-4313-8500-222001069cc5)

Remember that none of the upper layers “know” anything about networking or network addresses. That’s the responsibility of the four bottom layers.

The four bottom layers define how data is transferred through physical media, switches, and routers. These bottom layers also determine how to rebuild a data stream from a transmitting host to a destination host’s application.

#

### The Application Layer

The Application layer of the OSI model marks the spot where users actually communicate or interact with the computer.

Technically, users communicate with the network stack through application processes, interfaces, or application programming interfaces (APIs) that connect the application in use to the operating system of the computer.

The Application layer chooses and determines the availability of communicating partners along with the resources necessary to make their required connections.

It coordinates partnering applications and forms a consensus on procedures for controlling data integrity and error recovery.

The Application layer comes into play only when it’s apparent that access to the network will be needed soon.

The Application layer acts as an interface between the application program—which isn’t part of the layered structure—and the next layer down by providing ways for the application to send information down through the protocol stack. Browsers don’t reside within the Application layer—it interfaces with Application layer protocols when it needs to deal with remote resources.

For instance, Microsoft Word doesn’t reside at the Application layer, it interfaces with the Application layer protocols.

The Application layer is also responsible for identifying and establishing the availability of the intended communication partner and determining whether sufficient resources for the requested communication exist.

These tasks are important because computer applications sometimes require more than just desktop resources. Often, they unite communicating components from more than one network application.

Prime examples are file transfers and email as well as enabling remote access, network-management activities, and client-server processes like printing and information location. Many network applications provide services for communication over enterprise networks, but for present and future internetworking, the need is fast developing to reach beyond the limitations of current physical networking.

#

### The Presentation Layer

The Presentation layer gets its name from its purpose: it presents data to the Application layer and is responsible for data translation and code formatting.

A successful data-transfer technique is to adapt the data into a standard format before transmission.

Computers are configured to receive this generically formatted data and then convert it back into its native format for reading—for example, from EBCDIC to ASCII.

By providing translation services, the Presentation layer ensures that the data transferred from one system’s Application layer can be read and understood by the Application layer on another system.

The OSI has protocol standards that define how standard data should be formatted. Tasks like data compression, decompression, encryption, and decryption are all associated with this layer. Some Presentation layer standards are even involved in multimedia operations.

#

### The Session Layer

The Session layer is responsible for setting up, managing, and then tearing down sessions between Presentation layer entities.

This layer also provides dialog control between devices, or nodes.

It coordinates communication between systems and serves to organize their communication by offering three different modes: one direction (**simplex**), both directions, but only one direction at a time (**half-duplex**), and bi-directional (**full-duplex**).

The Session layer basically keeps an application’s data separate from other applications’ data. For a good example, the Session layer allows multiple web browser sessions on your desktop at the same time.

#

### The Transport Layer

The Transport layer segments and reassembles data into a data stream.

Services located in the Transport layer handle data from upper-layer applications and unite it onto the same data stream.

They provide end-to-end data transport services and can establish a logical connection between the sending host and destination host on an internetwork.

The Transport layer is responsible for providing the mechanisms for multiplexing upper-layer applications, establishing virtual connections, and tearing down virtual circuits.

It also hides the many and sundry details of any network-dependent information from the higher layers, facilitating data transfer.

The term reliable networking relates to the Transport layer and means that acknowledgments, sequencing, and flow control will be used.

The Transport layer can be connectionless or connection-oriented, but it’s especially important for you to really understand the connection-oriented portion of the Transport layer.

### Connection-Oriented Communication

Before a transmitting host starts to send segments down the model, the sender’s TCP process contacts the destination’s TCP process to establish a connection.

The resulting creation is known as a **virtual circuit**.

This type of communication is called **connection-oriented**.

During this initial handshake, the two TCP processes also agree on the amount of information that will be sent in either direction before the respective recipient’s TCP sends back an acknowledgment. 

With everything agreed on in advance, the path is paved for reliable communication to take place.

![image](https://github.com/user-attachments/assets/da8ff348-6d9e-4953-ab14-a205d13b0742)

Both of the hosts’ application programs begin by notifying their individual operating systems that a connection is about to be initiated.

The two operating systems communicate by sending messages over the network confirming that the transfer is approved and that both sides are ready for it to take place.

After all of this required synchronization occurs, a connection is fully established and the data transfer begins. 

This virtual circuit setup is called **overhead**.

While the information is being transferred between hosts, the two machines periodically check in with each other, communicating through their protocol software to ensure that all is going well and that data is being received properly.

Let me sum up the steps in the connection-oriented session—the TCP three-way handshake:

1. The first “connection agreement” segment is a request for synchronization.

2. The next segments acknowledge the request and establish connection parameters—the rules—between hosts. These segments request that the receiver’s sequencing is synchronized here as well so that a bidirectional connection is formed.

3. The final segment is also an acknowledgment. It notifies the destination host that the connection agreement has been accepted and that the connection has been established. Data transfer can now begin.

Sometimes congestion can occur during a transfer because a high-speed computer is generating data traffic a lot faster than the network can handle transferring it.

A bunch of computers simultaneously sending datagrams through a single gateway or to a destination can also clog things up.

In the latter case, a gateway or destination can become congested even though no single source caused the problem. Either way, the problem is like a freeway bottleneck—too much traffic for too small a capacity.

### Flow Control

Data integrity is ensured at the Transport layer by maintaining flow control and by allowing users to request reliable data transport between systems.

Flow control provides a means for the receiver to govern the amount of data sent by the sender.

It prevents a sending host on one side of the connection from overflowing the buffers in the receiving host—an event that can result in lost data.

Reliable data transport employs a connection-oriented communications session between systems, and the protocols involved ensure that the following will be achieved:

1. The segments delivered are acknowledged back to the sender upon their reception.

2. Any segments not acknowledged are retransmitted.

3. Segments are sequenced back into their proper order upon arrival at their destination.

4. A manageable data flow is maintained in order to avoid congestion, overloading, and data loss.

When a machine receives a flood of datagrams too quickly for it to process, it stores them in a memory section called a **buffer**.

But this buffering tactic can only solve the problem if the datagrams are part of a small burst.

If not, and the datagram deluge continues, a device’s memory will eventually be exhausted, its flood capacity will be exceeded, and it will react by discarding any additional datagrams.

The transport function of network flood-control works well. Instead of just dumping resources and allowing data to be lost, the transport can issue a “not ready” indicator to the sender, or source, of the flood.

![image](https://github.com/user-attachments/assets/2fa848e8-b5cd-4c4c-acff-b57687238a8d)

After the peer machine’s receiver processes the segments abounding in its memory reservoir (its buffer), it sends out a “ready” transport indicator. When the machine waiting to transmit the rest of its datagrams receives this “go” indictor, it resumes its transmission.

During fundamental, reliable, connection-oriented data transfer, datagrams are delivered to the receiving host in exactly the same sequence they’re transmitted.

So, if any data segments are lost, duplicated, or damaged along the way, a failure notice is transmitted.

This error is corrected by making sure the receiving host acknowledges it has received each andevery data segment, and in the correct order.

To summarize, a service is considered connection-oriented if it has the following characteristics:

- A virtual circuit is set up (such as a three-way handshake).
- It uses sequencing.
- It uses acknowledgments.
- It uses flow control.

### Windowing

Ideally, data throughput happens quickly and efficiently. And as you can imagine, it would be slow if the transmitting machine had to wait for an acknowledgment after sending each segment.

But because time is available after the sender transmits the data segment and before it finishes processing acknowledgments from the receiving machine, the sender uses the break as an opportunity to transmit more data.

The quantity of data segments (measured in bytes) that the transmitting machine is allowed to send without receiving an acknowledgment is represented by something called a window.

Windows are used to control the amount of outstanding, unacknowledged data segments.

It’s important to understand that the size of the window controls how much information is transferred from one end to the other.

Although some protocols quantify information by observing the number of packets, TCP/IP measures it by counting the number of bytes.

![image](https://github.com/user-attachments/assets/b7f0732f-d96a-48d5-a936-25c80e7ebeed)

When you’ve configured a window size of 1, the sending machine waits for an acknowledgment for each data segment it transmits before transmitting another. 

If you’ve configured a window size of 3, the sending machine is allowed to transmit three data segments before an acknowledgment is received.

In reality, the window size actually delimits the amount of bytes that can be sent at a time.

If a receiving host fails to receive all the segments that it should acknowledge, the host can improve the communication session by decreasing the window size.

### Acknowledgments

Reliable data delivery ensures the integrity of a data stream being sent from one machine to the other through a fully functional data link. It guarantees that the data won’t be duplicated or lost.

This is achieved through something called **positive acknowledgment with retransmission**—a technique that requires a receiving machine to communicate with the transmitting source by sending an acknowledgment message back to the sender when it receives data.

The sender documents each segment it sends and waits for this acknowledgment before sending the next segment.

When it sends a segment, the transmitting machine starts a timer and retransmits if it expires before an acknowledgment is returned from the receiving end.

![image](https://github.com/user-attachments/assets/e975de79-fd7f-481f-b957-4f2475ceed31)

The sending machine transmits segments 1, 2, and 3. The receiving node acknowledges it has received them by requesting segment 4. When it receives the acknowledgment, the sender then transmits segments 4, 5, and 6. If segment 5 doesn’t make it to the destination, the receiving node acknowledges that event with a request for the segment to be resent. The sending machine will then resend the lost segment and wait for an acknowledgment, which it must receive in order to move on to the transmission of segment 7.

The Transport layer doesn’t need to use a connection-oriented service. That choice is up to the application developer. It’s safe to say that if you’re connection-oriented, meaning that you’ve created a virtual circuit, you’re using TCP. If you aren’t setting up a virtual circuit, then you’re using UDP and are considered connectionless.

#

### The Network Layer

The Network layer manages logical device addressing, tracks the location of devices on the network, and determines the best way to move data.

This means that the Network layer must transport traffic between devices that aren’t locally attached.

Routers are layer 3 devices that are specified at the Network layer and provide the routing services within an internetwork. 

It happens like this: First, when a packet is received on a router interface, the destination IP address is checked. If the packet isn’t destined for that particular router, the router looks up the destination network address in the routing table.

Once the router chooses an exit interface, the packet is sent to that interface to be framed and sent out on the local network.

If the router can’t find an entry for the packet’s destination network in the routing table, the router drops the packet.

**Data Packets**

These are used to transport user data through the internetwork. Protocols used to support data traffic are called **routed protocols**. Two examples of routed protocols are Internet Protocol (IP) and Internet Protocol version 6 (IPv6).

**Route-Update Packets**

These are used to update neighboring routers about the networks connected to all routers within the internetwork. Protocols that send route-update packets are called routing protocols, and some common ones are Routing Information Protocol (RIP), RIPv2, Enhanced Interior Gateway Routing Protocol (EIGRP), and Open Shortest Path First (OSPF). Route-update packets are used to help build and maintain routing tables on each router.

![image](https://github.com/user-attachments/assets/90341cfd-fdba-4946-9706-4e1ea9ac0a90)

**Network Addresses**

These are protocol-specific network addresses. A router must maintain a routing table for individual routing protocols because each routing protocol keeps track of a network that includes different addressing schemes, like IP and IPv6.Think of it as a street sign in each of the different languages spoken by the residents who live on a particular street. If there were American, Spanish, and French folks on a street named Cat, the sign would read Cat/Gato/Chat.

**Interface**

This is the exit interface a packet will take when destined for a specific network.

**Metric**

This value equals the distance to the remote network. Different routing protocols use different ways of computing this distance. For now, just know that some routing protocols, namely RIP, use something called a **hop count**—the number of routers a packet passes through en route to a remote network. Other routing protocols alternatively use bandwidth, delay of the line, and even something known as a tick count, which equals 1/18 of a second, to make routing decisions.


Routers break up broadcast domains, which means that broadcasts by default aren’t forwarded through a router. This is a good thing because it reduces traffic on the network.

Routers also break up collision domains, but this can be accomplished using layer 2 (Data Link layer) switches as well.

Because each interface in a router represents a separate network, it must be assigned unique network identification numbers, and each host on the network connected to that router must use the same network number.

![image](https://github.com/user-attachments/assets/6f4f24d2-bfa9-432f-b25e-88152ffbea34)

Here are some key points about routers that you really should commit to memory:

- Routers, by default, won’t forward any broadcast or multicast packets.

- Routers use the logical address in a Network layer header to determine the next-hop router to forward the packet to.

- Routers can use access lists, created by an administrator, to control security on the types of packets that are allowed to enter or exit an interface.

- Routers can provide layer 2 bridging functions if needed and can simultaneously route through the same interface.

- Layer 3 devices (routers, in this case) provide connections between virtual LANs (VLANs).

- Routers can provide quality of service (QoS) for specific types of network traffic.

  A router can also be referred to as a layer 3 switch. These terms are interchangeable.

  #

  ### The Data Link Layer

The Data Link layer provides the physical transmission of the data and handles error notification, network topology, and flow control.

This means the Data Link layer ensures that messages are delivered to the proper device on a LAN using hardware (MAC) addresses and translates messages from the Network layer into bits for the Physical layer to transmit.
