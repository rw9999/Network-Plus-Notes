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

