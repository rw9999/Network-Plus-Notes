# The Current Ethernet Specifications

### Network Basics

![image](https://github.com/user-attachments/assets/4d6b68d9-9835-45ff-bb10-78a04e1a444d)

A basic LAN network that’s connected together using an Ethernet connection to a hub.

This network is actually one collision domain and one broadcast domain.

They’re both on the same LAN connected with a multiport repeater (a hub).

Bob is going to use Sally’s MAC address (known as a **hardware address**), which is burned right into the network card of Sally’s PC, to get a hold of her.

Bob is going to start by using name resolution (hostname–to–IP address resolution), something that’s usually accomplished using Domain Name Service (DNS).

And note that if these two hosts are on the same LAN, Bob can just broadcast to Sally asking her for the information (no DNS needed)

Here’s the output from a network analyzer depicting a simple name-resolution process from Bob to Sally:

    Time            Source             Destination         Protocol      Info

    53.892794       192.168.0.2        192.168.0.255       NBNS          Name query NB SALLY<00>

Because the two hosts are on a local LAN, Windows (Bob) will broadcast to resolve the name Sally (notice the destination 192.168.0.255 is a broadcast address).

Let’s take a look at the second part of the information:

    EthernetII,Src:192.168.0.2(00:14:22:be:18:3b),Dst:Broadcast(ff:ff:ff:ff:ff:ff)

This output shows that Bob knows his own MAC address and source IP address but not Sally’s IP address or MAC address. So, Bob sent a Data Link layer broadcast address of all Fs and an IP LAN broadcast to 192.168.0.255.

After the name is resolved, the next thing Bob has to do is broadcast on the LAN to get Sally’s MAC address so he can communicate to her PC:

    Time        Source         Destination     Protocol     Info
    
    5.153054    192.168.0.2    Broadcast       ARP          Who has 192.168.0.3? Tell 192.168.0.2

Next, check out Sally’s response:

    Time        Source          Destination    Protocol      Info
    
    5.153403    192.168.0.3     192.168.0.2    ARP           192.168.0.3 is 00:0b:db:99:d3:5e
   
    5.53.89317  192.168.0.3     192.168.0.2    NBNS          Name query response NB 192.168.0.3
 
Bob now has both Sally’s IP address and her MAC address (00:0b:db:99:d3:5e).

These are both listed as the source address at this point because this information was sent from Sally back to Bob.

So, finally, Bob has all the goods he needs to communicate with Sally.

Importantly, understand that Sally still had to go through the same resolution processes to communicate back to Bob

#

### Ethernet Basics

Ethernet is a contention media-access method that allows all hosts on a network to share the same bandwidth of a link.

Ethernet is popular because it’s readily scalable, meaning that it’s comparatively easy to integrate new technologies, such as Fast Ethernet and Gigabit Ethernet, into an existing network infrastructure.

It’s also relatively simple to implement in the first place, and with it, troubleshooting is reasonably straightforward.

Ethernet uses both Data Link and Physical layer specifications

### Collision Domain

The term collision domain is an Ethernet term that refers to a particular network scenario wherein one device sends a packet out on a network segment and thereby forces every other device on that same physical network segment to pay attention to it.

This is bad because if two devices on one physical segment transmit at the same time, a **collision event**—a situation where each device’s digital signals interfere with another on the wire—occurs and forces the devices to retransmit later.

Collisions have a dramatically negative effect on network performance.

The situation just described is typically found in a hub environment where each host segment connects to a hub that represents only one collision domain and one broadcast domain.

### Broadcast Domain

A broadcast domain refers to the set of all devices on a network segment that hear all the broadcasts sent on that segment.

Even though a broadcast domain is typically a boundary delimited by physical media like switches and repeaters, it can also reference a logical division of a network segment where all hosts can reach each other via a Data Link layer (hardware address) broadcast.

#

### CSMA/CD

Ethernet networking uses carrier sense multiple access with collision detection (CSMA/CD), a media access control contention method that helps devices share the bandwidth evenly without having two devices transmit at the same time on the network medium.

CSMA/CD was created to overcome the problem of those collisions that occur when packets are transmitted simultaneously from different hosts.

Good collision management is crucial because when a host transmits in a CSMA/CD network, all the other hosts on the network receive and examine that transmission.

Only bridges, switches, and routers, but not hubs, can effectively prevent a transmission from propagating throughout the entire network.

![image](https://github.com/user-attachments/assets/9b988df3-98e8-461a-92c0-94e1ab2caec2)

When a host wants to transmit over the network, it first checks for the presence of a digital signal on the wire.

If all is clear, meaning that no other host is transmitting, the host will then proceed with its transmission.

The transmitting host constantly monitors the wire to make sure no other hosts begin transmitting.

If the host detects another signal on the wire, it sends out an extended jam signal that causes all hosts on the segment to stop sending data (think busy signal).

The hosts respond to that jam signal by waiting a while before attempting to transmit again.

Backoff algorithms, represented by the clocks counting down on either side of the jammed devices, determine when the colliding stations can retransmit. If collisions keep occurring after 15 tries, the hosts attempting to transmit will then time out.

When a collision occurs on an Ethernet LAN, the following things happen:

- A jam signal informs all devices that a collision occurred.

- The collision invokes a random backoff algorithm.

- Each device on the Ethernet segment stops transmitting for a short time until the timers expire.

- All hosts have equal priority to transmit after the timers have expired.

And following are the effects of having a CSMA/CD network that has sustained heavy collisions:

- Delay

- Low throughput

- Congestion

Backoff on an 802.3 Ethernet network is the retransmission delay that’s enforced when a collision occurs. When a collision occurs, a host will resume transmission after the forced time delay has expired. After this backoff delay period has expired, all stations have equal priority to transmit data.

#

### Broadband/Baseband

We have two ways to send analog and digital signals down a wire: broadband and baseband.

We hear the term broadband a lot these days because that is pretty much what everyone uses at home.

It allows us to have both our analog voice and digital data carried on the same network cable or physical medium.

Broadband allows us to send multiple frequencies of different signals down the same wire at the same time (called frequency-division multiplexing) and to send both analog and digital signals.

Baseband is what all LANs use.

This is where all the bandwidth of the physical media is used by only one signal.

For example, Ethernet uses only one digital signal at a time, and it requires all the available bandwidth. 

If multiple signals are sent from different hosts at the same time, we get collisions; same with wireless, except that uses only analog signaling.

#

### Bit Rates vs. Baud Rate

Bit rate is a measure of the number of data bits (0s and 1s) transmitted in one second in either a digital or analog signal. A figure of 56,000 bits per second (bps) means 56,000 0s or 1s can be transmitted in one second, which we simply refer to as bps.

In the 1970s and 1980s, we used the term baud rate a lot, but that was replaced by bps because it was more accurate. Baud was a term of measurement named after a French engineer, Jean-Maurice-Émile Baudot, because he used it to measure the speed of telegraph transmissions.

One baud is one electronic state change per second—for example, from 0.2 volts to 3 volts or from binary 0 to 1. However, since a single state change can involve more than a single bit of data, the bps unit of measurement has replaced it as a more accurate definition of how much data you’re transmitting or receiving.

#

### Wavelength

With electromagnetic radiation, radio waves, light waves, or even infrared (heat) waves make characteristic patterns as they travel through space. Some patterns can be the same, and some can be different.

![image](https://github.com/user-attachments/assets/8e423164-b45b-4e94-94c7-d1b6e15b6388)

Each wave pattern has a certain shape and length.

The distance between peaks (high points) is called wavelength.

If two wave patterns are different, we would say they’re not on the same wavelength and that is the way we tell different kinds of electromagnetic energy apart.

We can use this to our advantage in electronics by sending traffic on different wavelengths at the same time.

#

### Half-and Full-Duplex Ethernet

Half-duplex Ethernet is defined in the original 802.3 Ethernet specification.

Basically, when you run half-duplex, you’re using only one wire pair with a digital signal either transmitting or receiving.

This really isn’t all that different from full-duplex because you can both transmit and receive—you just don’t get to do that at the same time running half-duplex as you can if you’re running full-duplex.

If a host hears a digital signal, it uses the CSMA/CD protocol to help prevent collisions and to permit retransmitting if a collision does occur. Half-duplex Ethernet—typically 10BaseT—is only about 30 to 40 percent efficient because a large 10BaseT network will usually provide only 3 Mbps to 4 Mbps at most. Although it’s true
that 100 Mbps Ethernet can and sometimes does run half-duplex, it’s just not very common to find that happening anymore.

In contrast, full-duplex Ethernet uses two pairs of wires at the same time instead of one wire pair like half-duplex employs.

Plus, full-duplex uses a point-to-point connection between the transmitter of the sending device and the receiver of the receiving device (in most cases the switch). This means that with full-duplex data transfer, you not only get faster data-transfer speeds, but you get collision prevention too.

You don’t need to worry about collisions because now it’s like a freeway with multiple lanes instead of the single-lane road provided by half-duplex.

Full-duplex Ethernet is supposed to offer 100 percent efficiency in both directions—forexample, you can get 20 Mbps with a 10 Mbps Ethernet running full-duplex, 200 Mbps for Fast Ethernet, or even 2000 Mbps for Gigabit Ethernet.

But this rate is something known as an **aggregate rate**, which translates as “you’re supposed to get” 100 percent efficiency.

Full-duplex Ethernet can be used in many situations; here are some examples:

- With a connection from a switch to a host

- With a connection from a switch to a switch

- With a connection from a host to a host using a crossover cable

You can run full-duplex with just about any device except a hub.

You may be wondering: If it’s capable of all that speed, why wouldn’t it deliver? Well, when a full-duplex Ethernet port is powered on, it first connects to the remote end and then negotiates with the other end of the Fast Ethernet link. 

This is called an **auto-detect mechanism**. This mechanism first decides on the exchange capability, which means it checks to see if it can run at 10, 100, or even 1000 Mbps. It then checks to see if it can run full-duplex, and if it can’t, it will run half-duplex instead

Hosts usually auto-detect both the Mbps and the duplex type available (the default setting), but you can manually set both the speed and duplex type on the network interface card (NIC)

![image](https://github.com/user-attachments/assets/250fe181-8263-464c-8091-aaca134d789f)

Today, it’s pretty rare to go into a NIC configuration on a host and change these settings, but this example demonstrates that you can do that if you want.

Remember that half-duplex Ethernet shares a collision domain and provides a lower effective throughput than full-duplex Ethernet, which typically has a private collision domain and a higher effective throughput.

Lastly, remember these important points:

- There are no collisions in full-duplex mode.

- A dedicated switch port is required for each full-duplex host.

- The host network card and the switch port must be capable of operating in full-duplex mode.

## Ethernet at the Data Link Layer

Ethernet at the Data Link layer is responsible for Ethernet addressing, commonly referred to as hardware addressing or MAC addressing.

Ethernet is also responsible for framing packets received from the Network layer and preparing them for transmission on the local network through the Ethernet contention media-access method known as CSMA/CD.

Ethernet MAC addresses are made up of hexadecimal addresses.

### Binary to Decimal and Hexadecimal Conversion

Each digit used is limited to being either a 1 (one) or a 0 (zero), and each digit is called 1 bit (short for binary digit). 

Typically, you count either 4 or 8 bits together, with these being referred to as a nibble and a byte, respectively.

What’s interesting about binary numbering is the value represented in a decimal format—the typical decimal format being the base-10 number scheme.

The binary numbers are placed in a value spot, starting at the right and moving left, with each spot having double the value of the previous spot.

![image](https://github.com/user-attachments/assets/9de1f3d2-29b9-402b-b8b2-0a3600eb28a2)

Remember, a nibble is four bits and a byte is eight bits. In network addressing, we often refer to a byte as an **octet**.

Mathematically, octal addressing actually refers to base 8, which is completely different from the base 10 we are familiar with.

What all this means is that if a one digit (1) is placed in a value spot, then the nibble or byte takes on that decimal value and adds it to any other value spots that have a 1. And if a zero (0) is placed in a bit spot, you don’t count that value.

If we have a 1 placed in each spot of our nibble, we then add up 8 + 4 + 2 + 1 to give us a maximum value of 15. Another example for our nibble values is 1010, which means that the 8 bit and the 2 bit are turned on and equal a decimal value of 10. If we have a nibble binary value of 0110, then our decimal value is 6 because the 4 and 2 bits are turned on.

![image](https://github.com/user-attachments/assets/566fe631-ee18-4e57-a11c-a5c67c1567b8)

Hexadecimal addressing is completely different than binary or decimal—it’s converted by reading nibbles, not bytes.

First, understand that the hexadecimal addressing scheme uses only the numbers 0 through 9. And because the numbers 10, 11, 12, and so on can’t be used (because they are two-digit numbers), the letters A, B, C, D, E, and F are used to represent 10, 11, 12, 13, 14, and 15, respectively.

![image](https://github.com/user-attachments/assets/a4ee0ab8-52c8-4ed6-92d4-6b42b2f43065)

![image](https://github.com/user-attachments/assets/ea39536a-56b7-461a-9ac0-a43baf5fb60f)

So suppose you have something like this: 0x6A. (Some manufacturers put 0x in front of characters so you know that they’re a hex value, while others just give you an h. It doesn’t have any other special meaning.) What are the binary and decimal values?

To correctly answer that question, all you have to remember is that each hex character is one nibble and two hex characters together make a byte.

To figure out the binary value, first put the hex characters into two nibbles and then put them together into a byte. 6 = 0110 and A (which is 10 in decimal) = 1010, so the complete byte is 01101010

To convert from binary to hex, just take the byte and break it into nibbles.

#

### Ethernet Addressing

Ethernet addressing works by using the Media Access Control (MAC) address burned into each and every Ethernet NIC. 

The MAC, or hardware, address is a 48-bit (6-byte) address written in a hexadecimal format.

![image](https://github.com/user-attachments/assets/6852a9db-1d5d-4c10-ad0f-0949ea81e40e)

The organizationally unique identifier (OUI) is assigned by the Institute of Electrical and Electronics Engineers (IEEE) to an organization.

It’s composed of 24 bits, or 3 bytes.

The organization, in turn, assigns a globally administered address (24 bits, or 3 bytes) that is unique to each and every adapter it manufactures.

The Individual/Group (I/G) address bit is used to signify if the destination MAC address is a unicast or a multicast/broadcast Layer 2 address. 

If the bit is set to 0, then it is an Individual MAC address and is a unicast address. If the bit is set to 1, it is a Group address and is a multicast/ broadcast address.

The next bit is the Local/Global bit (L/G). This bit is used to tell if the MAC address is the burned-in-address (BIA) or a MAC address that has been changed locally.

You’ll see this happen when we get to IPv6 addressing. 

The low-order 24 bits of an Ethernet address represent a locally administered or manufacturer-assigned code. This portion commonly starts with 24 0s for the first card made and continues in order until there are 24 1s for the last (16,777,216th) card made. You’ll find that many manufacturers use these same six hex digits as the last six characters of their serial number on the same card.

#

### Ethernet Frames

The Data Link layer is responsible for combining bits into bytes and bytes into frames.

Frames are used at the Data Link layer to encapsulate packets handed down from the Network layer for transmission on a type of physical media access.

The function of Ethernet stations is to pass data frames between each other using a group of bits known as a MAC frame format. This provides error detection from a cyclic redundancy check (CRC). But remember—this is error detection, not error correction.

![image](https://github.com/user-attachments/assets/e119e268-ca64-4bb9-a23e-8cf36cb28c56)

Encapsulating a frame within a different type of frame is called **tunneling**.

The following information regarding frame headings and the various types of Ethernet frames are beyond the scope of the CompTIA Network+ objectives.

Following are the details of the different fields in the 802.3 and Ethernet frame types:

**Preamble** An alternating 1,0 pattern provides a clock at the start of each packet, which allows the receiving devices to lock the incoming bit stream.

**Start of Frame Delimiter (SOF)/Synch** The preamble is seven octets, and the start of a frame (SOF) is one octet (synch). The SOF is 10101011, where the last pair of 1s allows the receiver to come into the alternating 1,0 pattern somewhere in the middle and still sync up and detect the beginning of the data.

**Destination Address (DA)** This transmits a 48-bit value using the least significant bit (LSB) first. The DA is used by receiving stations to determine whether an incoming packet is addressed to a particular host and can be an individual address or a broadcast or multicast MAC address. Remember that a broadcast is all 1s (or Fs in hex) and is sent to all devices, but a multicast is sent only to a similar subset of hosts on a network.

**Source Address (SA)** The SA is a 48-bit MAC address used to identify the transmitting device, and it uses the LSB first. Broadcast and multicast address formats are illegal within the SA field.

**Length or Type** 802.3 uses a Length field, but the Ethernet frame uses a Type field to identify the Network layer protocol. 802.3 by itself cannot identify the upper-layer routed protocol and must be used with a proprietary LAN protocol—Internetwork Packet Exchange (IPX), for example.

**Data** This is a packet sent down to the Data Link layer from the Network layer. The size can vary from 64 to 1,500 bytes.

**Frame Check Sequence (FCS**) FCS is a field that is at the end of the frame and is used to store the CRC.

You can see that the following frame has only three fields: Destination, Source, and Type, displayed as Protocol Type on this analyzer:

    Destination: 00:60:f5:00:1f:27
    Source: 00:60:f5:00:1f:2c

**Protocol Type: 08-00 IP** This is an Ethernet_II frame. Notice that the Type field is IP, or 08-00 (mostly just referred to as 0x800) in hexadecimal.

The next frame has the same fields, so it must be an Ethernet_II frame too:

    Destination: ff:ff:ff:ff:ff:ff Ethernet Broadcast
    Source: 02:07:01:22:de:a4

**Protocol Type: 08-00 IP** Did you notice that this frame was a broadcast? You can tell because the destination hardware address is all 1s in binary, or all Fs in hexadecimal.

You can see that the Ethernet frame is the same Ethernet_II frame we use with the IPv4 routed protocol. The difference is that the Type field has 0x86dd when we are carrying IPv6 data, and when we have IPv4 data, we use 0x0800 in the Protocol field:

    Destination: IPv6-Neighbor-Discovery_00:01:00:03 (33:33:00:01:00:03)
    Source: Aopen_3e:7f:dd (00:01:80:3e:7f:dd)

**Type: IPv6 (0x86dd)** This is the beauty of the Ethernet_II frame. Because of the Protocol field, we can run any Network layer routed protocol and it will carry the data because it can identify that particular Network layer protocol!

## Ethernet at the Physical Layer

Ethernet was first implemented by a group called DIX (Digital, Intel, and Xerox). They created and implemented the first Ethernet LAN specification, which the IEEE used to create the IEEE 802.3 Committee. This was a 10 Mbps network that ran on coax, then on twisted-pair, and finally on fiber physical media.

The IEEE extended the 802.3 Committee to three new committees known as 802.3u (Fast Ethernet), 802.3ab (Gigabit Ethernet on Category 5+), and then finally to 802.3ae (10 Gbps over fiber and coax).

![image](https://github.com/user-attachments/assets/611fbda9-b002-45a6-9119-3db718c9500a)

When designing your LAN, it’s really important to understand the different types of Ethernet media available to you.

The Electronic Industries Association and the newer Telecommunications Industry Alliance (EIA/TIA) together form the standards body that creates the Physical layer specifications for Ethernet. The EIA/TIA specifies that Ethernet use a registered jack (RJ) connector on unshielded twisted-pair (UTP) cabling (RJ-45). However, the industry is calling this just an 8-pin modular connector.

Each Ethernet cable type that is specified by the EIA/TIA has something known as **inherent attenuation**, which is defined as the loss of signal strength as it travels the length of a cable and is measured in decibels (dB).

The cabling used in corporate and home markets is measured in categories. A higher-quality cable will have a higher-rated category and lower attenuation.

For example, Category 5 is better than Category 3 because Category 5 cables have more wire twists per foot and therefore less crosstalk. Crosstalk is the unwanted signal interference from adjacent pairs in the cable.

Here are the original IEEE 802.3 standards:

**10Base2** This is also known as thinnet and can support up to 30 workstations on a single segment. It uses 10 Mbps of baseband technology, coax up to 185 meters in length, and a physical and logical bus with Attachment Unit Interface (AUI) connectors. The 10 means 10 Mbps, and Base means baseband technology—a  signaling method for communication on the network—and the 2 means almost 200 meters. 10Base2 Ethernet cards use BNC (British Naval Connector, Bayonet Neill-Concelman, or Bayonet Nut Connector) and T-connectors to connect to a network.

**10Base5** Also known as thicknet, 10Base5 uses a physical and logical bus with AUI connectors, 10 Mbps baseband technology, and coax up to 500 meters in length. You can go up to 2,500 meters with repeaters and 1,024 users for all segments. 

**10BaseT** This is 10 Mbps using Category 3 UTP wiring. Unlike on 10Base2 and 10Base5 networks, each device must connect into a hub or switch, and you can have only one host per segment or wire. It uses an RJ-45 connector (8-pin modular connector) with a physical star topology and a logical bus.

Each of the 802.3 standards defines an AUI, which allows a one-bit-at-a-time transfer to the Physical layer from the Data Link media-access method. This allows the MAC address to remain constant but means the Physical layer can support both existing and new technologies. The original AUI interface was a 15-pin connector, which allowed a transceiver (transmitter/ receiver) that provided a 15-pin- to- twisted- pair conversion.

There’s an issue, though—the AUI interface can’t support 100 Mbps Ethernet because of the high frequencies involved. So basically, 100BaseT needed a new interface, and the 802.3u specifications created one called the Media Independent Interface (MII) that provides 100 Mbps throughput. The MII uses a nibble, which you of course remember is defined as 4 bits. Gigabit Ethernet uses a Gigabit Media Independent Interface (GMII) and transmits 8 bits at a time.

802.3u (Fast Ethernet) is compatible with 802.3 Ethernet because they share the same physical characteristics. Fast Ethernet and Ethernet use the same maximum transmission unit (MTU) and the same MAC mechanisms, and they both preserve the frame format that is used by 10BaseT Ethernet. Basically, Fast Ethernet is just based on an extension to the IEEE 802.3 specification, and because of that, it offers us a speed increase of 10 times 10BaseT.

100BaseT and 100BaseTX: What’s the difference? 100BaseT is the name of a group of standards for Fast Ethernet that includes 100BaseTX. Also included are 100BaseT4 and 100BaseT2. The same can be said about 1000BaseT and 1000BaseX.

Ethernet’s implementation over fiber can sometimes be referred to as 100BaseTF even though this isn’t an actual standard. It just means that Ethernet technologies are being run over fiber cable.

Here are the expanded IEEE Ethernet 802.3 standards, starting with Fast Ethernet:

**100BaseTX (IEEE 802.3u)** 100BaseTX, most commonly known as Fast Ethernet, uses EIA/TIA Category 5 or 5e or 6 and UTP two-pair wiring. It allows for one user per segment up to 100 meters long (328 feet) and uses an RJ-45 connector with a physical star topology and a logical bus.

**100BaseFX (IEEE 802.3u)** Uses 62.5/125-micron multimode fiber cabling up to 412 meters long and point-to- point topology. It uses ST and SC connectors, which are media-interface connectors

**1000BaseCX (IEEE 802.3z)** Copper twisted-pair called twinax (a balanced coaxial pair) that can run only up to 25 meters and uses a special 9-pin connector known as the High-Speed Serial Data Connector (HSSDC).

**1000BaseT (IEEE 802.3ab)** Category 5, four-pair UTP wiring, and up to 100 meters long (328 feet).

**1000BaseTX** Category 5, two-pair UTP wiring up to 100 meters long (328 feet). Not used, and has been replaced by Category 6 cabling.

**1000BaseSX (IEEE 802.3z)** The implementation of Gigabit Ethernet runs over multimode fiber-optic cable instead of copper twisted-pair cable and uses short wavelength laser. Multimode fiber (MMF), using a 62.5-and 50-micron core, utilizes an 850 nanometer (nm) laser and can go up to 220 meters with 62.5-micron; 550 meters with 50-micron.

**1000BaseLX (IEEE 802.3z)** Single-mode fiber that uses a 9-micron core, 1,300 nm laser, and can go from 3 km up to 10 km.

**10GBaseT** 10GBaseT is a standard created by the IEEE 802.3an committee to provide 10 Gbps connections over conventional UTP cables (Category 5e, 6, 6A, or 7 cables). 10GBaseT allows the conventional RJ-45 used for Ethernet LANs. It can support signal transmission at the full 100-meter distance specified for LAN wiring. If you need to implement a 10 Gbps link.

**10GBaseSR** An implementation of 10 Gigabit Ethernet that uses short-wavelength lasers at 850 nm over multimode fiber. It has a maximum transmission distance of between 2 and 300 meters (990 feet), depending on the size and quality of the fiber.

**10GBaseLR** An implementation of 10 Gigabit Ethernet that uses long-wavelength lasers at 1,310 nm over single-mode fiber. It also has a maximum transmission distance between 2 meters and 10 km, or 6 miles, depending on the size and quality of the fiber.

**10GBaseER** An implementation of 10 Gigabit Ethernet running over single-mode fiber that uses extra-long- wavelength lasers at 1,550 nm. It has the longest transmission distances possible of all the 10 Gigabit technologies: anywhere from 2 meters up to 40 km, again depending on the size and quality of the fiber used.

**10GBaseSW** 10GBaseSW, as defined by IEEE 802.3ae, is a mode of 10GBaseS for MMF with an 850 nm laser transceiver and a bandwidth of 10 Gbps. It can support up to 300 meters of cable length. This media type is designed to connect to SONET equipment.

**10GBaseLW** 10GBaseLW is a mode of 10GBaseL supporting a link length of 10 km on standard single-mode fiber (SMF) (G.652). This media type is also designed to connect to SONET equipment.

**10GBaseEW** 10GBaseEW is a mode of 10GBaseE supporting a link length of up to 40 km on SMF based on G.652 using optical-wavelength 1,550 nm. This is another media type designed to connect to SONET equipment.

**40GBaseT** 40GBaseT is a standard created by the IEEE 802.3bq committee and supports Ethernet speeds up to 40G and is also used for 25G Ethernet connections commonly found in server NICs. There is less distance than the slower Ethernet types with 40GBaseT limited to 30 meters. This is usually sufficient for data center cabling. Category 8 cabling is required to support the high data rates of 25GBaseT and 40GBaseT.

If you want to implement a network medium that is not susceptible to electromagnetic interference (EMI), fiber-optic cable provides a more secure, long-distance cable that is not susceptible to EMI at high speeds as UTP is.

![image](https://github.com/user-attachments/assets/0e0cc709-2972-48ee-9e9c-301c7c79e83a)

![image](https://github.com/user-attachments/assets/86f992c6-46c2-48ac-b69c-d302b3de56c0)

![image](https://github.com/user-attachments/assets/0fd8892c-2561-4555-9c6e-c894a71f6a41)

An advantage of 100BaseFX over 100BaseTX is longer cable runs, but 100BaseTX is easier to install.

## Ethernet over Other Standards (IEEE 1905.1-2013)

IEEE 1905.1-2013 is an IEEE standard that defines a convergent digital home network for both wireless and wireline technologies.

The technologies include IEEE 802.11 (Wi-Fi), IEEE 1901 (HomePlug, HD-PLC) powerline networking, IEEE 802.3 Ethernet, and Multimedia over Coax (MoCA).

The 1905.1-2013 was published in April 2013. The IEEE 1905.1 Standard Working Group is sponsored by the IEEE Power Line Communication Standards Committee (PLCSC).

The idea behind the 1905.1 technology standards is simple setup, configuration, and operation of home networking devices using both wired and wireless technologies.

This will take advantage of the performance, coverage, and mobility benefits of multiple interfaces (Ethernet, Wi-Fi, Powerline, and MoCA), which enables better coverage and throughput in every room for both wireless and fixed devices.

#

### Ethernet over Power Line

In February 2011, the IEEE finally published a standard for Broadband over Power Line (BPL) called IEEE 1901, also referred to as Power Line Communication (PLC) or even Power Line Digital Subscriber Line (PDSL).

Although this technology has been available for decades in theory, without an IEEE standard it was just not adopted as an alternative to other high-speed media.

However, it is highly likely that this technology will really start to see some traction, especially from the power companies who will be able to gather data from every device in your house and specifically tell you how much power is being used by your refrigerator, washers and dryers, and especially your computer and televisions, among all the other devices plugged into a wall power outlet.

In the future, BPL will allow you to just plug a computer into a wall power socket and have more than 500 Mbps for up to 1,500 meters.

![image](https://github.com/user-attachments/assets/3782a665-8537-42ca-a5ab-4a57f106a7c0)

This technology can be used to deliver Internet access to the home as well. For a computer (or any other device), you would simply need to plug a BPL modem into any outlet in an equipped building to have high-speed Internet access.

![image](https://github.com/user-attachments/assets/6977c8be-55de-42c0-bc0d-606036627ece)

After the gateway is connected through the coupler to the meter bank for the building, any electrical outlet can be used with the BPL modem to receive the ISP connection to the Internet.

The following challenges still exist:

- The fact that power lines are typically noisy.
- 
- The frequency at which the information is transmitted is used by shortwave, and the unshielded power lines can act as antennas, thereby interfering with shortwave communications.

#

### Ethernet over HDMI

HDMI Ethernet Channel technology consolidates video, audio, and data streams into a single HDMI cable, combining the signal quality of HDMI connectivity with the power and flexibility of home entertainment networking

![image](https://github.com/user-attachments/assets/681ce056-bf70-4baf-8da0-2af4cf71ef5d)

It incorporates a dedicated data channel into the HDMI link, enabling high-speed, bidirectional networking at up to 100 Mbps.

### Bidirectional Wavelength-Division Multiplexing (WDM)

Modern optical networks can support multiple optical wavelengths down a single fiber-optical cable. This reduces the number of fiber cables required to interconnect locations.

By implementing wavelength-division multiplexing, optical networks can support multiple optical wavelengths down a single fiber-optical cable.

Optical multiplexing is used in carrier and service provider networks to maximize the use of buried fiber. (WDM) is a technology that multiplexes a number of optical carrier signals onto a single optical fiber by using different wavelengths (i.e., colors) of laser light.

### Course Wavelength-Division Multiplexing (CWDM)

CWDM allows up to 18 channels to be transported over a single dark fiber. Wavelengths are commonly 1310 nm and 1550 nm. CWDM can support distances of up to 70 km.

### Dense Wavelength-Division Multiplexing (DWDM)

With DWDM, more than 80 individual wavelengths can share a single fiber. 

DWDM can handle higher speeds than CWDM, with up to 400 Gbps per channel. Each channel is 0.8 nm apart instead of the 20 nm you would find in a CWDM system. 

Dense wavelength-division multiplexing is a very similar technology to CWDM but has a higher channel capacity. It can also be amplified to support much longer distances than CWDM but with DWDM achieving 1000 m using amplification.
