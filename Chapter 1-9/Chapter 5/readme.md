# Networking Devices

### Network Interface Card

A network interface card (NIC) is installed in your computer to connect, or interface, your computer to the network. 

It provides the physical, electrical, and electronic connections to the network media. 

The NIC is called a layer 2 device because the information it uses for communication, the MAC address, resides on the Data Link layer.

A NIC either is an expansion card or is built right into the computer’s motherboard.

Today, almost all NICs are built into the computer motherboard, providing 10, 100, and 1000 megabits per second (Mbps), but there was a time when all NICs were expansion cards that plugged into motherboard expansion slots.

In some notebook computers, NIC adapters can be connected to the USB port or through a PC card slot. Ethernet speeds have been steadily increasing, especially in server chassis with 25, 40 and 100 G NICs now quite common.\

![image](https://github.com/user-attachments/assets/1f4dfebe-e03a-4dbe-adc0-02972dd7b1f7)

Nowadays, most PCs and laptops of all types come with an Ethernet and wireless connector built into the motherboard, so you usually don’t need a separate card. It’s rare to find a laptop today without a built-in wireless network card, but you can buy external wireless cards for desktops and laptops if you’ve got legacy equipment that needs them.

NICs today usually have one, two, or more LEDs; one, usually green, is called a link light, indicating that an Ethernet connection has been established with the device on the other end of the cable, and it flickers when traffic is being passed back or forth.

The other, or others, usually indicates the speed of the connection: 10, 100, or 1000 Mbps. There’s no universal standard for NIC LEDs, so check the manual to familiarize yourself with the ones you are working with.

But it’s not always that cut-and-dried that a blinking LED can mean the NIC is receiving a proper signal from the hub or switch; it can also indicate connectivity to and detection of a carrier on a segment.

Another possibility is that it’s found connectivity with a router or other end device using a crossover cable.

The other LED is aptly named the activity LED, and it tends to flicker constantly. That activity indicates the intermittent transmission and reception of frames arriving at the network or leaving it.

The first LED you should verify is the link LED because if it’s not illuminated, the activity LED simply cannot illuminate.

#

### Hub

A hub is the device that connects all the segments of the network together in a star topology Ethernet network.

As a hub has no intelligence, it is a layer 1 device. Each device in the network connects directly to the hub through a single cable and is used to connect multiple devices without segmenting a network.

Any transmission received on one port will be sent out to all the other ports in the hub, including the receiving pair for the transmitting device, so that Carrier Sense Multiple Access with Collision Detection (CSMA/CD) on the transmitter can monitor for collisions.

So, basically, this means that if one station sends a broadcast, all the others will receive it; yet based on the addressing found in the frame, only the intended recipient will actually listen and process it.

This arrangement simulates the physical bus that the CSMA/CD standard was based on, and it’s why we call the use of a hub in an Ethernet environment a physical star/logical bus topology.

![image](https://github.com/user-attachments/assets/eb3e2b30-285b-4405-b5ce-5fe523b6a2ea)

A typical hub you might find it employed within a small network. Since there are only two users, there isn’t a problem in using a hub here. However, if there were 20 users, everyone would see Bob’s request to send a packet to Sally. Most of the time, hubs really aren’t recommended for corporate networks because of their limitations.

It’s important to note that hubs are nothing more than glorified repeaters that are incapable of recognizing frames and data structures—the reason they act with such a lack of intelligence.

A broadcast sent out by any device on the hub will be propagated to all devices connected to it. And just as in a physical bus topology configuration, any two or more of those connected devices have the potential of causing a collision with each other, which means that this hardware device will create a LAN with the most network traffic collisions. Hubs are not suggested for use in today’s corporate network for this reason.

#

### Bridge

A bridge—specifically, a transparent bridge—is a network device that connects two similar network segments together.

Its primary function is to keep traffic separated on either side of the bridge, breaking up collision domains.

![image](https://github.com/user-attachments/assets/2c218413-1dbc-4c72-8fe2-61262f245a58)

What we can see here is that traffic is allowed to pass through the bridge only if the transmission is intended for a station on the opposite side.

The main reasons you would place a bridge in your network would be to connect two segments together or to divide a busy network into two segments. As bridges use MAC addresses to make forwarding decisions, they are considered layer 2 devices.

Bridges are software based, so, interestingly, you can think of a switch as a hardware-based, multiport bridge..

In fact, the terms bridge and switch are often used interchangeably because the two devices used basically the same bridging technologies. The past tense is there for a reason—you’d be hard-pressed to buy a bridge today.

#

### Switch

Switches connect multiple segments of a network together much like hubs do, but with three significant differences—a switch recognizes frames and pays attention to the source and destination MAC address of the incoming frame as well as the port on which it was received.

A switch makes each of its ports a unique, singular collision domain. Hubs don’t do those things. They simply send anything they receive on one port out to all the others.

As switches use MAC addresses to make forwarding decisions, they are considered layer 2 devices.

So, if a switch determines that a frame’s final destination happens to be on a segment that’s connected via a different port than the one on which the frame was received, the switch will only forward the frame out from the specific port on which its destination is located.

If the switch can’t figure out the location of the frame’s destination, it will flood the frame out of every port except the one on which the frame port was received.

![image](https://github.com/user-attachments/assets/4af6ecd0-ed73-4a6a-802a-10b382241fcc)

It looks a lot like a hub. However, switches can come in very large, expensive sizes. Switches that can perform the basic switching process and do not allow you to configure more advanced features—like adding an IP address for telnetting to the device or adding VLANs—are called unmanaged switches.

Others, like Cisco switches that do allow an IP address to be configured for management with such applications as simple network management protocol (SNMP) and do allow special ports to be configured (as in VoIP), are called managed switches.

Switches are layer 2 devices, which means they segment the network with MAC addresses. If you see the term layer 3 switch, that means you are talking about a router, not a layer 2 switch. The terms router and layer 3 switch are interchangeable.

#

### Router

A router is a network device used to connect many, sometimes disparate, network segments together, combining them into what we call an internetwork.

A well-configured router can make intelligent decisions about the best way to get network data to its destination. It gathers the information it needs to make these decisions based on a network’s particular performance data. As routers use IP addresses to make forwarding decisions, they are considered layer 3 devices.

![image](https://github.com/user-attachments/assets/c28def12-a9da-4123-8d38-3bba1506e3ed)

A small office, home office (SOHO) router that provides wired and wireless access for hosts and connects them to the Internet without any necessary configuration.

Routers can be multifaceted devices that behave like computers unto themselves with their own complex operating systems—for example, Cisco’s IOS. You can even think of them as CPUs that are totally dedicated to the process of routing packets. And due to their complexity and flexibility, you can configure them to actually perform the functions of other types of network devices (like firewalls, for example) by simply implementing a specific feature within the router’s software.

Routers can have many different names: layer 3 switch and multilayer switch are the most common, besides the name router, of course. Remember, if you hear just the word switch, that means a layer 2 device. Routers, layer 3 switches, and multilayer switches are all layer 3 devices.

#

### Interface Configurations

When configuring interfaces on a router or switch, unless you’re doing complex configurations such as connecting up a Voice over IP (VoIP) network, the interface configurations are pretty straightforward.

There is a major difference between a router interface and a switch interface configuration, however.

On a switch, you do not add an IP address since they only read to layer 2, and most of the time, you never even need to configure a switch interface.

First, they are enabled by default, and second, they are very good at auto-detecting the speed, duplex, and, in newer switches, even the Ethernet cable type (crossover or straight-through).

A router is much different and an IP address is expected on each interface; they are not enabled by default, and a good layer 3 network design must be considered before installing a router.

Let’s start by taking a look at a basic Cisco switch configuration. First, notice by the output shown that there is no configuration on the interfaces, yet you can plug this switch into your network and it would work.

This is because all ports are enabled and there are some very basic configurations that allow the switch to run without any configuration—they can be considered plug-and- play in a small or home network:
    
    Switch#sh running-config
    [Some output cut for brevity] 
    !
    interface FastEthernet0/1
    !
    interface FastEthernet0/2
    !
    interface FastEthernet0/3
    !
    interface FastEthernet0/4
    !
    interface FastEthernet0/5
    !
    interface FastEthernet0/6
    !
    interface FastEthernet0/7
    !
    interface FastEthernet0/8
    !

Let’s take a look at a configuration of a simple switch interface. First, we’ll notice the duplex options:

    Switch(config-if)# duplex ?
      auto Enable AUTO duplex configuration
      full Force full duplex operation
      half Force half-duplex operation

All switch ports are set to duplex auto by default, and usually you can just leave this configuration alone.

However, be aware that if your network interface card is set to half-duplex and the switch port is configured for full-duplex, the port will receive errors and you’ll eventually get a call from the user. This is why it is advised to just leave the defaults on your hosts and switch ports, but it is a troubleshooting spot to check when a problem is reported from a single user.

The next configuration and/or troubleshooting spot you may need to consider is the speed of the port:

    Switch(config-if)#speed ?
    10     Force 10 Mbps operation
    100    Force 100 Mbps operation
    1000   Force 1000 Mbps operation
    auto   Enable AUTO speed configuration

This is set to auto, but you may want to force the port to be 1000 and full-duplex. Typically, the NIC will run this without a problem and you’ll be sure you’re getting the most bang for your buck on your switch port.

Let’s take a look at a router interface. We’re pretty much going to configure (or not configure) the same parameters.

