# Introduction to Networks

### What is a Network?

The dictionary defines the word network as “a group or system of interconnected people or things.” 

Similarly, in the computer world, the term network means two or more connected computers that can share resources such as data and applications, office machines, an Internet connection, or some combination of these.

![image](https://github.com/rw9999/Network-Plus-Notes/assets/134976895/27071395-79aa-498f-9792-a6e8a4d4e617)

A really basic network made up of only two host computers connected; they share resources such as files and even a printer hooked up to one of the hosts.

These two hosts “talk” to each other using a computer language called **binary code**, which consists of lots of 1s and 0s in a specific order that describes exactly what they want to “say.”

#

### Local Area Network

Just as the name implies, a local area network (LAN) is usually restricted to spanning a particular geographic location such as an office building, a single department within a corporate office, or even a home office.

Back in the day, you couldn’t put more than 30 workstations on a LAN, and you had to cope with strict limitations on how far those machines could actually be from each other.

Because of technological advances, all that’s changed now, and we’re not nearly as restricted in regard to both a LAN’s size and the distance a LAN can span. 

Even so, it’s still best to split a big LAN into smaller logical zones known as **workgroups** to make administration easier.

The meaning of the term workgroup in this context is slightly different than when the term is used in contrast to domains. In that context, a workgroup is a set of devices with no security association with one another (whereas in a domain they do have that association). In this context, we simply mean they physically are in the same network segment.

In a typical business environment, it’s a good idea to arrange your LAN’s workgroups along department divisions; for instance, you would create a workgroup for Accounting, another one for Sales, and maybe another for Marketing.

![image](https://github.com/rw9999/Network-Plus-Notes/assets/134976895/cd0ae42d-8565-445a-98db-9202b08ed165)


Notice that there’s a Marketing workgroup and a Sales workgroup. These are LANs in their most basic form.

Any device that connects to the Marketing LAN can access the resources of the Marketing LAN—in this case, the servers and printer.

There are two problems with this:

- You must be physically connected to a workgroup’s LAN to get the resources from it.

- You can’t get from one LAN to the other and use the server data and printing resources remotely.

This is a typical network issue that’s easily resolved by using a cool device called a router to connect the two LANs.

![image](https://github.com/rw9999/Network-Plus-Notes/assets/134976895/72048b22-229b-4b8f-ac66-a0974125dbff)

Even though you can use routers for more than just connecting LANs, the router shown is a great solution because the host computers from the Sales LAN can get to the resources (server data and printers) of the Marketing LAN, and vice versa.

Now, you might be thinking that we don’t really need the router—that we could just physically connect the two workgroups with a type of cable that would allow the Marketing and Sales workgroups to hook up somehow.

Well, we could do that, but if we did, we would have only one big, cumbersome workgroup instead of separate workgroups for Marketing and Sales, and that kind of arrangement just isn’t practical for today’s networks.

This is because with smaller, individual-yet-connected groups, the users on each LAN enjoy much faster response times when accessing resources, and administrative tasks are a lot easier too. 

Larger workgroups run more slowly because there’s a legion of hosts within them that are all trying to get to the same resources simultaneously. So the router shown, which separates the workgroups while still allowing access between them, is a really great solution.

## Common Network Components

There are a lot of different machines, devices, and media that make up our networks. 

Let’s talk about three of the most common:

- Workstations

- Servers

- Hosts

### Workstations

Workstations are often seriously powerful computers that run more than one central processing unit (CPU) and whose resources are available to other users on the network to access when needed.

Workstations are often employed as systems that end users use on a daily basis.

Don’t confuse workstations with client machines, which can be workstations but not always. People often use the terms **workstation** and **client** interchangeably. But technically speaking, they are different. A client machine is any device on the network that can ask for access to resources like a printer or other hosts from a server or powerful workstation.

The terms workstation, client, and host can sometimes be used interchangeably. Computers have become more and more powerful and the terms have become somewhat fuzzy because hosts can be clients, workstations, servers, and more! The term host is used to describe pretty much anything that takes an IP address.

### Servers

Servers are also powerful computers. They get their name because they truly are “at the service” of the network and run specialized software known as the network operating system to maintain and control the network.

In a good design that optimizes the network’s performance, servers are highly specialized and are there to handle one important labor-intensive job. This is not to say that a single server can’t do many jobs, but more often than not, you’ll get better performance if you dedicate a server to a single task. 

Here’s a list of common dedicated servers:

**File Server**&emsp;&emsp;Stores and dispenses files

**Mail Server**&emsp;&emsp;The network’s post office; handles email functions

**Print Server**&emsp;&emsp;Manages printers on the network 

**Web Server**&emsp;&emsp;Manages web-based activities by running Hypertext Transfer Protocol Secure (HTTPS) for storing web content and accessing web pages

**Fax Server**&emsp;&emsp;The “memo maker” that sends and receives paperless faxes over the network

**Application Server**&emsp;&emsp;Manages network applications

**Telephony Server**&emsp;&emsp;Handles the call center and call routing and can be thought of as a sophisticated network answering machine

**Proxy Server**&emsp;&emsp;Handles tasks in the place of other machines on the network, particularly an Internet connection

Servers are usually dedicated to doing one specific important thing within the network. Not always, though—sometimes they have more than one job

They can maintain the network’s data integrity by backing up the network’s software and providing redundant hardware (for fault tolerance)

Servers must have considerably superior CPUs, hard-drive space, and memory—a lot more than a simple client’s capacity—because they serve many client machines and provide any resources they require.

You should always put your servers in a very secure area. they really pricey workhorses, they also store huge amounts of important and sensitive company data, so they need to be kept safe from any unauthorized access.

![image](https://github.com/rw9999/Network-Plus-Notes/assets/134976895/ebd268c6-91e0-446f-adb9-5385139dc9de)

One server can provide resources to what can sometimes be a huge number of individual users at the same time but workstations don’t

#

### Hosts

When people refer to hosts, they really can be referring to almost any type of networking devices—including workstations and servers.

