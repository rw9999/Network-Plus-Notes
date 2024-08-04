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


