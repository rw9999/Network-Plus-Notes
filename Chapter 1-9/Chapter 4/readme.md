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



