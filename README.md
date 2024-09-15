#Step-by-Step Configuration Guide 

##Objective 
The objective of the configuration proccess of setting up the network system is to allow two seperate local area networks (LANs) to communicate with each other through a router

##Use Cases
- A corporation needs to create a network to connect the in-office departmental LAN with the guest/extended LAN.
  The in-office LAN allows for efficent data sharing between the different departments such as Finance and Marketing. The guest/extended LAN provides accees to the network for remote-workers or guests who need to communicate with the in-office LAN.
- A university needs to provide a LAN for it's academic buildings that can communicate with the LAN for staff office buildings and student dormitories. This will allow students and staff to accees needed university platforms when in other locations besides classrooms.
  This will allow for students in their dorms to access online academic platforms and administration to update grades from their offices or even remotely.

  ##System Setup Steps

  ###1. Chose the software and hardware
- The first LAN will be using three PCs and the second LAN will need 3 servers. We will also need two switches, a router, and ethernet cables.
- It is also needed to have a wireless access point (WAP) and an ethernet cable as well.
- Any personal and mobile devices that will want to be added to the network wirelessly should also be chosen. For example, a tablet, smartphone, laptop will be used. 
- Both local area networks need a switch that they will connect to using an ethernet cable and then both switches will be plugged into the router using ethernet cables as well. Include this???

  ###2. IP assignments
  - The first LAN that will be PCs will be under the network 192.168.0.0/24 which means the PCs can be within that range except for the first avilable option is saved for the router which will also serve as the default gateway for all the PCs (192.168.0.1). Since this network will be supporting PCs we will be a Class C network since the size of the network that will be supported is not very large. This network will be denoted 192.168.0.0/24 and has 254 usable Ips and will have the default subnetwork mask 255.255.0.0.
  - The second LAN will be three servers that use the network 172.26.0.0/16 and again the first available option of 172.26.0.1 will be saved for the router and also will be used as the default gateway for the servers. Since these servers need more network support this will be a Class B network that is denoted 172.16.0.0/16 and has 65,534 usable IPs and the default subnet mask is 255.255.255.0.
 
###3. Add end devices 
- Next, the three PCs must be taken out for the the first LAN and then the 3 servers for the second LAN we will set up.

###4. Add switch 
- Then take out two switches for each local area network.

###5. Connect end devices to the switch with ethernet cables
- Take the LAN with three PCs and connect each PC with an ethernet cables to the switch in ports next to each other.

###6. Add wireless access point (WAP)
- A WAP is a wireless device that allows wireless devices to connect to a wired network such as our LAN with PCs.

###7. Connect WAP to a switch 
- Using an ethenet cable, connect our switch to the WAP.

###8. Add mobile devices
- Since WAP is present and connected to switch, personal/moible devices can be added to the network. We will connect a tablet, laptop, and mobile phone. IP ADDRESSES???!?!?!?!?!?

###9. Set IP addresses on 
  

  
