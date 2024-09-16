# Step-by-Step Configuration Guide 


## Objective 

- The objective of the configuration proccess of setting up the network system is to allow two seperate local area networks (LANs) to communicate with each other through a router

## Use Cases

- A corporation needs to create a network to connect the in-office departmental LAN with the guest/extended LAN.
  The in-office LAN allows for efficent data sharing between the different departments such as Finance and Marketing. The guest/extended LAN provides accees to the network for remote-workers or guests who need to communicate with the in-office LAN.
- A university needs to provide a LAN for it's academic buildings that can communicate with the LAN for staff office buildings and student dormitories. This will allow students and staff to accees needed university platforms when in other locations besides classrooms.
  This will allow for students in their dorms to access online academic platforms and administration to update grades from their offices or even remotely.

## System Setup Steps

  ### 1. Chose the software and hardware
- We will need two laptops, a switche, a router, and ethernet cables.
- If you wanted to connect wireless devices to the network, it would also be needed to have a wireless access point (WAP) and another ethernet cable.
- Any personal and mobile devices that will want to be added to the network wirelessly should also be chosen. For example, a tablet, smartphone, laptop will be used. 
- The set up will require Apple Mac computers and the software MAMP, NAMO, TextEdit and have access to the mac operating system Terminal. 


### 2. IP assignments

  - The LAN will use the IP address range of `192.168.0.0/26` which is Class C since it supports a smaller network and that is all we need for this set up. A subnetwork (subnet) defines the specicifc segment of our network and gives us a ranage of 64 IP addresses. The number 64 comes from an IPv4 IP address which is 32 bits long and the /26 represents bits reserved for the network portion so the leftover 6 bits available are used for available host addresses (32-26=6). The number of avialble IP addresses for hosts is determined by the 6 bits which we take the number two and sqare it by 6 and 2^6 = 64 addresses in total. The subnet mask is `255.255.255.192` for this IP address since this is how the binary form of the subnet trasnlates into decimal. 
  - A second LAN will be using the IP address range of `176.16.0.0/24` is a Class B address since it supports a larger network. 
 
### 3. Add end devices 
- Next, the three PCs must be taken out for the the first LAN and then the 3 servers for the second LAN we will set up.

### 4. Add switch 
- Then take out two switches for each local area network.

### 5. Connect end devices to the switch with ethernet cables
- Take the LAN with three PCs and connect each PC with an ethernet cables to the switch in ports next to each other.

### 6. Add wireless access point (WAP)
- A WAP is a wireless device that allows wireless devices to connect to a wired network such as our LAN with PCs.

### 7. Connect WAP to a switch 
- Using an ethenet cable, connect our switch to the WAP.

### 8. Add mobile devices
- Since WAP is present and connected to switch, personal/moible devices can be added to the network. We will connect a tablet, laptop, and mobile phone. IP ADDRESSES???!?!?!?!?!?

### 9. Set IP addresses on end devices (mobile device help)
- In our LAN with three PCs, the IP addresses will be 192.168.0.2, 192.168.0.3, and 192.168.0.4. Since this LAN is Class C the default subnet mask will be 255.255.0.0. The other LAN with three servers will be 172.16.0.2, 172.16.0.3, and 172.16.0.4 and the subnet mask will be 255.255.255.0.

### 10. Add a router to talk to different networks
- Adding a router to connect the two seperate local area networks will allow them to be able to communicate with each other and share data.

### 11. Connect the switches to router using ethernat cables
- To enable the router to do its job, both switches must be connected to the router using ethernet cables.

### 12. Configure IPs on a router
- Configuring the IP addresses on a router to the default gatway of each LAN is imperative for network communication.
- If a device on one LAN wants to communicate to a device on another LAN, it sends the data to its default gateway which will now be the router since the IP addresses have been configured.
- Therefore; the router will have have two IP addresses and subnet masks entered since there are two switches connected by ethernet cables.
- The IP address will be 192.168.0.1 which is the default gateway of out first LAN.
- The next IP address will be 172.16.0.1 which is the default gateway of our second LAN.
  
### 13. Set port status to ON on router. what this mean???

### 14. Set default gateway on all end devices hosts.
- Default gateway for a LAN should be the first avilable IP in the network.
- Default gateway for first LAN with three PCs will be 192.168.0.1.
- Default gateway for second LAN with three servers will be 172.16.0.1.
- mobile devices default gateway????



# FAQ

## 1. Question: What to do if within a LAN, one PC can not communicate with another?
**Answers** 
- It is important to check and make sure all PCs have their IP addresses and subnet masks entered. The PCs communicate through pinging the IP address of another so if this does not work then there is a good chance an IP address is missing.
- There could also be a typo in one of the input IP addresses or subnet masks.
- It is important to also make sure that the ethernet cables that are connecting the PCs to the switch are fully plugged in and correctly working 
## 2. Question: What if my PC on one LAN can not communicate with the server on the other LAN?
**Answers**
- Either the PC or the server is missing their needed default gateway. When the PC wants to communcate with the server in another LAN, it is sent to the default gateway (the router's IP on the same LAN as the PC). The router then forwards it to the appropriate server, with the IP address that was specified by the PC. So if there is a missing default gateway the message will not make it to the intended server.
- The router could be missing one of the default gateways from either LAN. Rememeber, the router holds the default gateway of both LANs in order to allow them to communicate so if one is missing it will not work.
- Make sure all ethernet cables are fully connected and working.
## 3. Question: What if my network system can not reach a web server connected through the router?
**Answers**
- Ensure all firewalls on devices and router are disabled. Firewalls can disable web traffic to temporarily diabling these can fix the problem.
- Verify that the web server is running and its IP address is correct.
## 4. Question: What do I do when my router has stopped the communication between the networks even though all numbers are input correct?






