# Networking Connectors and Wiring Standards

### Physical Media

A lot of us rely on wireless networking methods that work using technologies like radio frequency and infrared, but even wireless depends on a physical media backbone in place somewhere.

The majority of installed LANs today communicate via some kind of cabling, so let’s take a look at the three types of popular cables used in modern networking designs:

- Coaxial
- Twisted-pair
- Fiber optic

### Coaxial Cable

Coaxial cable, referred to as coax, contains a center conductor made of copper that’s surrounded by a plastic jacket with a braided shield over it.

A plastic such as polyvinyl chloride (PVC) or fluoroethylenepropylene (FEP, commonly known as Teflon) covers this metal shield.

The Teflon-type covering is frequently referred to as a **plenum-rated coating**, and it’s definitely expensive but often mandated by local or municipal fire code when cable is hidden in walls and ceilings.

Plenum rating applies to all types of cabling and is an approved replacement for all other compositions of cable sheathing and insulation like PVC-based assemblies.

The difference between plenum and non-plenum cable comes down to how each is constructed and where you can use it.

Many large multistory buildings are designed to circulate air through the spaces between the ceiling of one story and the floor of the next; this space between floors is referred to as the **plenum**. And it just happens to be a perfect spot to run all the cables that connect the legions of computers that live in the building.

Unless there’s a fire—if that happens, the non-plenum cable becomes a serious hazard because its insulation gives off poisonous smoke that gets circulated throughout the whole building. Plus, non-plenum cables can actually become “wicks” for the fire, helping it quickly spread from room to room and floor to floor.

The National Fire Protection Association (NFPA) demands that cables run within the plenum have been tested and guaranteed as safe.

They must be fire retardant and create little or no smoke and poisonous gas when burned.

This means you absolutely can’t use a non-plenum-type cable in the plenum, but it doesn’t mean you can’t use it in other places where it’s safe. And because it’s a lot cheaper, you definitely want to use it where you can.

**Thin Ethernet**, also referred to as **thinnet** or 10Base2, is a thin coaxial cable. It is basically the same as thick coaxial cable except it’s only about 5 mm, or 2/10″, diameter coaxial cable.

Thin Ethernet coaxial cable is Radio Grade 58, or just RG-58.

![image](https://github.com/user-attachments/assets/da1065b2-f236-4aff-a397-5db862e57cda)

This connector resembles the coaxial connector used for cable TV, which is called an F-type connector.

If you use thinnet cable, you’ve got to use BNC connectors to attach stations to the network, as shown in Figure 3.2, and you have to use 50 ohm terminating resistors at each end of the cable in order to achieve the proper performance.

![image](https://github.com/user-attachments/assets/ab5eed04-3572-4d6d-9d39-7c39ece4283b)

You don’t have to know much about most coax cable types in networks anymore, especially the thinnet and thicknet types of coaxial cable. Thicknet was known as RG-8 and was about 1/2″ in diameter, also requiring 50 ohm terminating resistors on each end of the cable.

Nowadays, we use 75-ohm coax for cable TV; using coax in the Ethernet LAN world is pretty much a thing of the past, but we do use them for high-bandwidth runs in our data centers. RG-6, or CATV coax, is used in our broadband world.

You can attach a BNC connector to the cable with a crimper that looks like a weird pair of pliers and has a die to crimp the connector. A simple squeeze crimps the connector to the cable. You can also use a screw-on connector, but I avoid doing that because it’s not very reliable. You can use a BNC coupler to connect two male connectors together or two female connectors together.

### F-type

The F connector, or F-type connector, is a form of coaxial connector that is used for cable TV.

It has an end that screws to tighten the connector to the interface. 

It resembles the RG-58 mentioned earlier in this section.

![image](https://github.com/user-attachments/assets/89e99d08-3928-44ec-8723-b9d3428c86d3)

An advantage of using coax cable is the braided shielding that provides resistance to electronic pollution like electromagnetic interference (EMI), radio frequency interference (RFI), and other types of stray electronic signals that can make their way onto a network cable and cause communication problems.

### Twisted-Pair Cable

Twisted-pair cable consists of multiple individually insulated wires that are twisted together in pairs. 

Sometimes a metallic shield is placed around them, hence the name shielded twisted-pair (STP). 

Cable without outer shielding is called unshielded twisted-pair (UTP), and it’s used in twisted-pair Ethernet (10BaseT, 100BaseTX, 1000BaseTX, and 10GBaseT) networks.

### Twinaxial Cable

Twinaxial cabling is used for short-distance high-speed connections such as 10G Ethernet connections in a data center.

The advantage of using Twinax is that there is a significant cost savings over fiber-optic cabling since Twinaxial cables are copper-based.

### Ethernet Cable Descriptions

Ethernet cable types are described using a code that follows this format: N <Signaling> X.

The N refers to the signaling rate in megabits per second.

<Signaling> stands for the signaling type—either baseband or broadband—and the X is a unique identifier for a specific Ethernet cabling scheme.

Here’s a common example: 100BaseX. The 100 tells us that the transmission speed is 100 Mb, or 100 megabits. The X value can mean several different things; for example, a T is short for twisted-pair.

This is the standard for running 100-megabit Ethernet over two pairs (four wires) of Category 5, 5e, 6, 6a, 7, and 8 UTP.

When electromagnetic signals are conducted on copper wires in close proximity—like inside a cable—it causes interference called **crosstalk**.

Twisting two wires together as a pair minimizes interference and even protects against interference from outside sources.

This cable type is the most common today for the following reasons:

- It’s cheaper than other types of cabling.

- It’s easy to work with.

-  It allows transmission rates that were impossible 10 years ago.

UTP cable is rated in these categories:

Category is often shortened to Cat. Today, any cable installed should be a minimum of Cat 5e because some cable is now certified to carry bandwidth signals of 350 MHz or beyond. This allows unshielded twisted-pair cables to exceed speeds of 1 Gbps—fast enough to carry broadcast-quality video over a network.

**Category 1** Two twisted wire pairs (four wires). It’s the oldest type and is only voice grade—it isn’t rated for data communication. People refer to it as plain old telephone service (POTS). Before 1983, this was the standard cable used throughout the North American telephone system. POTS cable still exists in parts of the public switched telephone network (PSTN) and supports signals limited to the 1 MHz frequency range.

**Category 2** Four twisted wire pairs (eight wires). It handles up to 4 Mbps, with a frequency limitation of 10 MHz, and is now obsolete.

**Category 3** Four twisted wire pairs (eight wires) with three twists per foot. This type can handle transmissions up to 16 MHz. It was popular in the mid-1980s for up to 10 Mbps Ethernet, but it’s now limited to telecommunication equipment and, again, is obsolete for networks.

**Category 4** Four twisted wire pairs (eight wires), rated for 20 MHz; also obsolete.

**Category 5** Four twisted wire pairs (eight wires), used for 100BaseTX (two pair wiring) and rated for 100 MHz. But why use Cat 5 when you can use Cat 5e for the same price? Using Cat 6 is an option but it’s slightly harder to install due to its size compared to 5e.

**Category 5e (Enhanced)** Four twisted wire pairs (eight wires), recommended for 1000BaseT (four pair wiring) and rated for 100 MHz but capable of handling the disturbance on each pair that’s caused by transmitting on all four pairs at the same time—a feature that’s needed for Gigabit Ethernet. Any category below 5e shouldn’t be used in today’s network environments.

**Category 6** Four twisted wire pairs (eight wires), used for 1000BaseTX (two pair wiring) and rated for 250 MHz. Cat 6 became a standard back in June 2002. You would generally use it as riser cable to connect floors together. If you’re installing a new network in a new building, there’s no reason to use anything but Category 6 UTP cabling as well as using fiber runs between floors.

**Category 6A (Augmented)** Basic Category 6 cable has a reduced maximum length when used for 10GBaseT; however, Category 6A cable, or Augmented Category 6, is characterized to 500 MHz and has improved crosstalk characteristics, which allows 10GBaseT to be run for up to 100 meters. The most important point is a performance difference between Electronic Industries Alliance and Telecommunications Industry Association (EIA/TIA) component specifications for the NEXT (near-end crosstalk) transmission parameter. Running at a frequency of 500 MHz, an ISO/IEC Cat 6A connector provides double the power (3db) of a Cat 6A connector that conforms with the EIA/TIA specification. Note that 3 dB equals a 100 percent increase of a near-end crosstalknoise reduction.

**Category 7** Category 7 cable, Cat 7, allows 10 Gigabit Ethernet over 100 meters of copper cabling. The cable contains four twisted copper wire pairs, just like the earlier standards.

**Category 8** Cat 8 cable was developed to address the ever-increasing speed of Ethernet and added support for 25G and 40G transmission with a distance of 30 meters, which is perfect for data center deployments.

#

### Connecting UTP

BNC connectors won’t fit very well on UTP cable, so you need to use a registered jack (RJ) connector, which you’re familiar with because most telephones connect with them. The connector used with UTP cable is called RJ-11 for phones that use four wires; RJ-45 has four pairs (eight wires)

![image](https://github.com/user-attachments/assets/d68c9d68-77e1-4e4b-942b-91df1b626df0)

![image](https://github.com/user-attachments/assets/faecbcbb-6f89-457c-b1b0-7070186fb887)

Most of the time, UTP uses RJ connectors, and you use a crimper to attach them to a cable, just as you would with BNC connectors. 

The only difference is that the die that holds the connector is a different shape. Higher-quality crimping tools have interchangeable dies for both types of cables. 

We don’t use RJ-11 for local area networks (LANs), but we do use them for our home Digital Subscriber Line (DSL) connections.

There’s one other type of copper connector, called the RJ-48c, which looks exactly like an RJ-45 connector. This plug is very similar to the RJ-45 in that it has four wire pairs, but they are wired differently and used for different circumstances. 

RJ-45 is mainly used in LANs with short distances (typically up to 100 meters), where the RJ-48c wiring type would be used with a T1 connection, which is a long-distance wide area network (WAN). In addition, to protect the signal in an RJ-48c, the wires are typically shielded, whereas the RJ-45 uses unshielded wiring.

#

### Category 5e Cabling Tips

Since you want data rates faster than 10 Mbps over UTP, ensure that all components are rated to deliver this and be really careful when handling all components.

If you yank on Cat5e cable, it will stretch the number of twists inside the jacket, rendering the Cat 5e label on the outside of the cable invalid.

Also, be certain to connect and test all four pairs of wire.

Although today’s wiring generally uses only two pairs (four wires), the standard for Gigabit Ethernet over UTP requires that all four pairs (eight wires) be in good condition.

Also be aware that a true Cat 5e cabling system uses rated components from end to end, patch cables from workstation to wall panel, cable from wall panel to patch panel, and patch cables from patch panel to hub.

So, if any components are missing, or if the lengths don’t match the Category 5e specification, you just don’t have a Category 5e cabling installation. And certify that the entire installation is Category 5e compliant. Requires some pretty pricey test equipment 

#

### Fiber-Optic Cable

Because fiber-optic cable transmits digital signals using light impulses rather than electricity, it’s immune to EMI and RFI.

Fiber cable allows light impulses to be carried on either a glass or a plastic core.

Glass can carry the signal a greater distance, but plastic costs less

Whichever the type of core, it’s surrounded by a glass or plastic cladding with a different refraction index that reflects the light back into the core.

Around this is a layer of flexible plastic buffer that can be wrapped in an armor coating that’s usually Kevlar, which is then sheathed in PVC or plenum.

The cable itself comes in either single-mode fiber (SMF) or multimode fiber (MMF); the difference between them is in the number of light rays (the number of signals) they can carry.

Multimode fiber is most often used for shorter-distance applications and single-mode fiber for spanning longer distances.

Although fiber-optic cable may sound like the solution to many problems, it has its pros and cons just like the other cable types.

Pros: 

- It’s completely immune to EMI and RFI.

- It can transmit up to 40 kilometers (about 25 miles).

Cons:

- It’s difficult to install.

- It’s more expensive than twisted-pair.

- Troubleshooting equipment is more expensive than twisted-pair test equipment.
  
- It’s harder to troubleshoot.

### Single-Mode Fiber

Single-mode fiber-optic cable (SMF) is a very high-speed, long-distancemedia that consists of a single strand—sometimes two strands—of glass fiber that carries the signals.

Light-emitting diodes (LEDs) and laser are the light sources used with SMF.

The light source is transmitted from end to end and pulsed to create communication

This is the type of fiber cable employed to span really long distances because it can transmit data 50 times farther than multimode fiber at a faster rate.

Clearly, because the transmission media is glass, the installation of SMF can be a bit tricky. Yes, there are outer layers protecting the glass core, but the cable still shouldn’t be crimped or pinched around any tight corners.

### Multimode Fiber

Multimode fiber-optic cable (MMF) also uses light to communicate a signal, but with it, the light is dispersed on numerous paths as it travels through the core and is reflected back.

A special material called **cladding** is used to line the core and focus the light back onto it.

MMF provides high bandwidth at high speeds over medium distances (up to about 3,000 feet), but beyond that it can be really inconsistent.

This is why MMF is most often used within a smaller area of one building; SMF can be used between buildings.

MMF is available in glass or in a plastic version that makes installation a lot easier and increases the installation’s flexibility.

### APC vs. UPC

The choice between angled physical contact (APC) and ultra physical contact (UPC) can make a pretty big difference on how your network will perform.

The ultra-polished connector looks like what you’d expect to find in a fiber-optic end. The cut is perfectly straight.

With the UPC, the light is reflected back down to the core of the fiber cable, which causes a loss of dB called a return loss because the angled connector causes the light to reflect back into the cladding—the thick sides of the glass instead of the core. But the APC doesn’t cause nearly as much dB loss when using this type of connector.

![image](https://github.com/user-attachments/assets/395e38c9-2b92-4ae9-80f4-ab16dee66db1)

### Fiber-Optic Connectors

A whole bunch of different types of connectors are available to use with fiber-optic cables, but the two most popular are the straight tip (ST) and the subscriber (or square) connector (SC).

The ST fiber-optic connector (developed by AT&T) is one of the most widely used fiber-optic connectors; it uses a BNC attachment mechanism similar to thinnet’s that makes connections and disconnections fairly frustration free. In fact, this is the feature that makes this connector so popular.

![image](https://github.com/user-attachments/assets/4f6781a8-2602-47a1-8626-c5ea9309b720)

SC connectors are latched—a mechanism holds the connector in securely and prevents it from falling out.

![image](https://github.com/user-attachments/assets/ded7124d-f36e-4954-9221-03d2b6e21508)

SC connectors work with both single-mode and multimode optical fibers and will last for around 1,000 mattings. They’re being used more now but still aren’t nearly as popular as ST connectors for LAN connections.

### Fiber Distribution Panel

Fiber distribution panels (FDPs) are termination and distribution systems for fiber-optic cable facilities. 

They consist of a cable management tray and a splice drawer. 

They are designed for central offices, remote offices, and LANs using fiber-optic facilities.

### Fiber-Optic Transceivers

Fiber-optic transceivers can be either unidirectional (simplex) or bidirectional (duplex).

**Bidirectional** communication is possible if the cable used is following the EEE 802.3ah 1000BASE-BX10-D and 1000BASE-BX10-U standards. 

The communication over a single strand of fiber is achieved by separating the transmission wavelength of the two devices.

![image](https://github.com/user-attachments/assets/0cf29fdb-4c7d-47d2-9cbd-ac3f472bbea1)

### Small Form Factor Fiber-Optic Connectors

Allows more fiber-optic terminations in the same amount of space than its standard-sized counterparts.

The two most popular versions are the mechanical transfer registered jack (MT-RJ or MTRJ), designed by AMP, and the local connector (LC), designed by Lucent.

The MT-RJ fiber-optic connector was the first small form factor fiber-optic connector to be widely used, and it’s only one-third  the size of the SC and ST connectors it most often replaces. 

It offers these benefits:

- Small size

- TX and RX strands in one connector

- Keyed for single polarity

- Pre-terminated ends that require no polishing or epoxy

- Easy to use

![image](https://github.com/user-attachments/assets/4e6554d3-6496-4844-a45e-39d8750dc983)

LC is a newer style of SFF fiber-optic connector that’s pulling ahead of the MT-RJ. It’s especially popular for use with Fibre-Channel adapters (FCs) and is a standard used for fast storage area networks and Gigabit Ethernet adapters.

![image](https://github.com/user-attachments/assets/d969bc7b-15fc-404e-8911-74eeb8f5ca0d)

It has similar advantages to MT-RJ and other SFF-type connectors but it’s easier to terminate. It uses a ceramic insert just as standard-sized fiber-optic connectors do.

### Should I Use Copper or Fiber?

If your data runs are measured in miles, fiber optic is your cable of choice because copper just can’t give you more than about 1,500 feet without electronics regenerating the signal.

The standards limit UTP to 328 feet.

Another good reason to opt for fiber is if you require high security because it doesn’t create a readable magnetic field.

Although fiber-optic technology was initially super expensive and nasty to work with, it’s now commonly used for Gigabit, 10 GB, or 40 GB Internet backbones.

Ethernet running at 10 Mbps over fiber-optic cable to the desktop is designated 10BaseFL; the 100 Mbps version of this implementation is 100BaseFX. 

The L in the 10 Mbps version stands for link. Other designations are B for backbone and P for passive.

#

### Transceivers

A transceiver is a device made up of both a transmitter and a receiver, which are combined and share common circuitry or a single housing.

The term applies to wireless communications devices such as cellular telephones, cordless telephone sets, handheld two-way radios, and mobile two-way radios. Occasionally, the term is used in reference to transmitter and receiver devices in cable or optical fiber systems.

**SFP+** The small form-factor pluggable (SFP) is a compact pluggable optical module transceiver used for both telecommunication and data communications applications. The enhanced small form-factor pluggable (SFP+) transceiver is an enhanced version of the SFP that supports data rates up to 16 Gbit/s.

**QSFP** The quad small form-factor pluggable (QSFP) is another compact, hot-pluggable transceiver used for data communications applications. It interfaces networking hardware (such as servers and switches) to a fiber-optic cable or active or passive electrical copper connection. It allows data rates from 4x1 Gb/s for QSFP and 4x10 Gbit/s for QSFP+ to the highest rate of 4x28 Gbit/s known as QSFP28 used for 100 Gbit/s links.

#

### Media Converters

Sometimes, you’ll need to convert from one media type to another. Maybe you need to go from one mode of fiber to another mode, or in an even more extreme case, you need to go from fiber to Ethernet.

If you’re faced with situations like these, you’ll need to be familiar with some of the more common media converters:

**Single-Mode Fiber to Ethernet** These devices accept a fiber connector and an Ethernet connector and convert the signal from Ethernet and single-mode fiber

![image](https://github.com/user-attachments/assets/3c5fd57a-014c-4b4a-ac89-71dc85b36d27)

**Multimode Fiber to Ethernet** These devices accept a fiber connector and an Ethernet connector and convert the signal from Ethernet and multimode fiber

![image](https://github.com/user-attachments/assets/282dab03-0cb1-49f2-9ac4-dcd46c62c784)

**Fiber to Coaxial** These devices accept a fiber connector and a coaxial connector and convert digital signals from optical to coax

![image](https://github.com/user-attachments/assets/f9c25477-f6cc-430b-8a24-b43136a91c19)

**Single-Mode to Multimode Fiber** These devices accept a single-mode fiber connector and a multimode fiber connector and convert the signals between the two

![image](https://github.com/user-attachments/assets/2755580e-acff-4457-8a2e-c2b58ec6e136)

#

### Serial Cables

Except for multimode fiber, all the cable varieties so far are considered serial cable types.

In network communications, **serial** means that one bit after another is sent out onto the wire or fiber and interpreted by a network card or other type of interface on the other end.

Each 1 or 0 is read separately and then combined with others to form data.

This is very different from parallel communication, where bits are sent in groups and have to be read together to make sense of the message they represent. A good example of a parallel cable is an old printer cable—which has been replaced by USB

### RS-232

Recommended Standard 232 (RS-232) was a cable standard commonly used for serial data signals connecting the DTE and the DCE, such as a computer’s serial port to an external modem.

These cables normally connect to a connector on the device called a DB-9.

![image](https://github.com/user-attachments/assets/d5769bec-6210-4449-8eec-e2b1077acaac)

Because laptops don’t even come with these types of connectors anymore, they’ve pretty much been replaced by things like USB and USB-C.

### DB-25

The D series of connectors was invented by ITT Cannon in 1952, and the D was followed by A, B, C, D, or E, which described the shell size, and then the numbers of pins or sockets.

DB-25 tells us we have 25 pins in a “B” size shell. 

RS-232  devices generally used the DB-25 connector, but today we don’t use RS-232 or DB-25, and we rarely use a DB-9, which was used for Cisco console cables but has mostly been replaced by USB.

### Universal Serial Bus

Universal Serial Bus (USB) is now the built-in serial bus used on most motherboards.

You usually get a maximum of 4 external USB interfaces, but add-on adapters can take that up to as many as 16 serial interfaces. USB can actually connect a maximum of 127 (7-bit address slots) external devices, and it’s a much more flexible peripheral bus than either serial or parallel.

We use USB to connect printers, scanners, and a host of other input devices like keyboards, joysticks, and mice. When connecting USB peripherals, you’ve got to connect them either directly to one of the USB ports on the PC or to a USB hub that is connected to one of those USB ports.

Hubs can be chained together to provide multiple USB connections, but even though you can connect up to 127 devices, it’s really not practical to go there.

#

### Cable Properties

The reason we use so many different types of cables in a network is that each type has its own set of properties that specifically make it the best to use for a particular area or purpose.

Different types vary in transmission speeds, distance, duplex, noise immunity, and frequency.

### Transmission Speeds

Based on the type of cable or fiber you choose and the network that it’s installed in, network administrators can control the speed of a network to meet the network’s traffic demands.

Admins usually permit, or would like to have, transmission speeds of up to 10 Gbps or higher on the core areas of their networks that connect various network segments.

In the distribution and access areas, where users connect to switches, it’s typically 100 Mbps per connection, but transmission speeds are creeping up because the traffic demand is getting higher. 

### Distance

Deciding factors used in choosing what cable type to use often come down to the topology of a network and the distance between its components.


