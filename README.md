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

### 2. Assign LAN IP addresses

  - The LAN that I will describe the set up for will use the IP address range of `192.168.0.0/26` which is Class C since it supports a smaller network and that is all we need for this set up. A subnetwork (subnet) defines the specicifc segment of our network and gives us a ranage of 64 IP addresses. The number 64 comes from an IPv4 IP address which is 32 bits long and the /26 represents bits reserved for the network portion so the leftover 6 bits available are used for available host addresses (32-26=6). The number of avialble IP addresses for hosts is determined by the 6 bits which we take the number two and sqare it by 6 and 2^6 = 64 addresses in total. The subnet mask is `255.255.255.192` for this IP address since this is how the binary form of the subnet trasnlates into decimal. The first usable address is `192.168.0.1` and is reserved as our default gateway which is the device that acts as an acceess point for a network to communicate with devices or networks outside of its own LAN which in our case will be a router. All devices on the LAN will need to have this default gateway set into its configuration.
  - There is a second LAN will be using the IP address range of `176.16.0.0/24` is a Class B address since it supports a larger network. Our subnet gives us a range of 256 usabke IP addresses since we take the 32-24=8 bits usable for hosts addresses then 2^8=256. Our subnet mask is `255.255.255.0` because this is the decimal from of the /24 subnet. The default gateway IP will be 176.16.0.1 which will be input into router and all devices on the LAN.
 
### 3. Connect end devices to switch
- We will have two MAC computers that we connect to the switch using ethernet cables in ports next to each other.
- As shown there are 2 rectangle areas with 12 ports in each one, either rectangle is fine but insert ethernet cables in ports next to each other.
<img width="471" alt="Screenshot 2024-09-16 at 4 53 12 PM" src="https://github.com/user-attachments/assets/b6f33abd-cacf-4a06-b9fa-b2207a974901">

### 4. Configure devices on LAN 
- The first device we will call MAC1 and will also act as our Web Server for this set up. A web server stores and provides website content when requested by browsers. HTTPS is Hypertext Transfer Protocal Secure which is used for transmitting data such as web pages between client and server. MAC1 will be the web servr that served website content when a browser requests HTTP/HTTPS content. Go to the System Settings, Network, and select the USB 10/100/1000 LAN in "Other Services." Next, go to the "TCP/IP" tab and in the "Configure IPv4" area select the "Using DHCP" and change it to the "Manually" option. Enter `192.168.0.2` and the subnet mask `255.255.255.192`. Now go to the DNS tab and delete any servers that may be listed already and in the DNS Servers area input `10.96.8.66` as this will be the DNS server we configure next.
- The second device we will call MAC2 and will act as our DNS server. A Domaine Name Server (DNS) will translate human-friendly domains into IP addresses and vice verse. This allows for clients to search easy to remember and type website names instead of a long IP address. Go to System Settings, then Network, then "Configure IPv4" and select "Manually" and input the IP address `192.168.0.3` and the Subnet mask `255.255.255.0`. 

### Ensure both MACs can communicate with each other successfuly
In the MAC1 search bar look up the Terminal application and enter "Ping 192.168.0.3" and in the Terminal application for MAC2, enter "ping 192.168.0.2". For this to be successful it will say there was a Reply from the IP address and a 0% loss. If the Reply from IP address message will not stop hit control then c buttons on keyboard.

<img width="31" alt="Screenshot 2024-09-16 at 6 17 27 PM" src="https://github.com/user-attachments/assets/fd743e3d-004a-4050-b3a7-d0cda428e6a0">
<img width="272" alt="Screenshot 2024-09-16 at 6 17 38 PM" src="https://github.com/user-attachments/assets/be04d64c-4b4e-4fc3-9b89-0bcb4dc56d33">

### Set up Network Web Server Requirements
- For MAC1, open the MAMP applications folder, Seelect Nginx as the Web server. Now go into preferences and select Ports then edit both the Nginx Port and Apache Port to 80 then click OK. Then start the web server by clicking the start button. It may already say stop in that area which means it is already running. Just to be sure, click Stop then Start again.
- Now we will create an index.html in the directory of our operating system. Since macOS is our operating system we will go into Applications, click MAMP, click htdocs, then index.html.
- Next, open the TextEdit application and input "Welcome to Capstone Consulting02"

### Set up the Network DNS Server Requirments 
- In our MAC2, open and start the NAMO application. Create a new Host record for capstoneconsulting02.com. Click the + to add a new host and put in capstoneconsulting02.com. Then set the IP address to `192.168.0.3` since that is the IP address of MAC2 which is designated as the DNS server and hit save.
- Now go into Web server and change setting to put in DNS IP

### 11. Connect the switches to router using ethernat cables
- Download the application "driver".
- Turn on physically the router.
- Adding a router to connect the two seperate local area networks will allow them to be able to communicate with each other and share data.
- To enable the router to do its job, both switches must be connected to the router using ethernet cables.
- Then connect a serial console cable from the router to the MAC2. 

### 12. Configure IPs on a router and turn port status on
- Configuring the IP addresses on a router to the default gatway of each LAN is imperative for network communication.
- There will be two addresses input and the first IP address will be 192.168.0.1 with the subnet mask 255.255.255.192 which is the default gateway of out first LAN and the next IP address will be 172.16.0.1 with the subnet mask 255.255.0.0 which is the default gateway of our second LAN.
- Now that MAC2 has the serial console cable plugged in, it can configure the IPs and turn the port status. Do not include the quote marks in the terminal code, it is there to seperate code from explanation.
- Type "router enable" to enter EXEC mode to make changes. The first thing that soulg now pop up is Router#
- Type after Router#, "configure terminal", hit enter
- then type "hostname router01", and hit enter
- now type "interface gigabitEthernet 0/0", enter
- then "ip address 192.168.0.1 255.255.255.192", enter
- then type "description ##to switch 01##", hit enter. This is to describe the connection we are creating from router to switch.
- then Type "no shutdown"
- Then type "exit"
- Then type "wr" to write the configuration into memory.
- to confirm config was permanantly saved, type and enter "show startup-config"
- Now we will do the same process for the other LAN's IP address but now using shortcuts.
- Tyoe "config t", which is a shortcut to what we typed earlier
- now type "int g0/1", enter
- "ip add 172.16.0.1 255.255.0.0", enter
- "description ##switch 01"
- "no shut"
- then enter "exit" and then "wr" to write it into memory
- To check that our IP addresses have been configured, type and enter "show ip interface brief" and it should look similar to this image but the numbers should be 0/0 and 0/1 instead of 0/0/0 and 0/0/1"

  <img width="390" alt="Screenshot 2024-09-17 at 10 54 34 AM" src="https://github.com/user-attachments/assets/34ca4122-ea6a-4e2d-a207-d0fbdec0164e">

### Ping the other LAN we are connected to throught the router
- Since our router is set up with both LAN default gateways, we can ping the other LAN.
- In terminal, type "172.16.0.2" which is one of IP addresses of the other LAN devices.
- 

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
## 4. Question: What do I do when my router has stopped the communication between the networks even though my router is turned on?
**Answers**
- Try turning on off the router and turning it back on. Once back on, give it a couple minutes to fully reboot.
- Make sure the IP addresses and subnet masks are correcly entered into the router. You can check using the "show ip interface brief" in terminal. If needed to go back into and fix, type and enter these commands: router>enable, configure terminal, interface GigabitEthernet 0/0 (if that is the IP that needs to be changed).
- Now it is time to remove what is wrong so type in "no ip address" then the address that needs to be changed and enter. Then type "ip address" with the correct numbers.
- Type and enter "no shutdown", "exit", then "wr" to write the correct IP into memory 






