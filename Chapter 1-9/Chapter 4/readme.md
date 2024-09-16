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
