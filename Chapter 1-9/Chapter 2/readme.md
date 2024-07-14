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

