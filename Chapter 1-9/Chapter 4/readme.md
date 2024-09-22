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



