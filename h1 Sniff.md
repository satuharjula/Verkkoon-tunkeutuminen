# h1 Sniff  

## Summary  

### Wireshark - Getting Started  

-Wireshark is a tool used for capturing and analyzing network traffic.  

-A capture is started by selecting the desired network interface and pressing Start.  

-The statistics provide an overview of the traffic, such as protocols and devices.  

-Filters can be used to narrow down the traffic, for example dns, http, and tls. (Karvinen 28.3.2025)  

### Network Interface Names in Linux

Network interfaces in Linux are named according to systemd. For example, enp1s0 and wlp4s0.  

  Types:  
  - en = wired ethernet  
  - lo = loopback (localhost)  
  - wl = wireless (WiFi)  
  
You can check the network interface using the command ip a. (Karvinen 28.3.2025)  


## Installing Kali Linux

I started the task by installing Kali Linux on VirtualBox. Wireshark was already available in Kali, so it didn't need to be installed separately for this task.  

## Disconnecting and Restoring the Internet Connection  

Connection on  

<img width="201" height="141" alt="image" src="https://github.com/user-attachments/assets/6a67c02a-c7b3-4adc-a825-4ce22871ade6" />

Connection off  

<img width="438" height="175" alt="image" src="https://github.com/user-attachments/assets/e9889cc0-0e02-48dd-9ab9-cdc22c3adbe6" />

## TCP/IP Model

Four layers from a packet I captured:  

### Link Layer

Ethernet II contains the Source MAC (sender) and Destination MAC (receiver), which are used to move the packet from the sender to the receiver.  

<img width="645" height="59" alt="image" src="https://github.com/user-attachments/assets/8aabaa3c-811d-4b0f-9d47-734bbc94ffa4" />

### Internet Layer

IPv4 contains the IP addresses Source IP (sender) 10.0.2.15 and Destination IP (receiver) 142.251.150.119, which are used to route the packet to the correct destination.  

<img width="527" height="207" alt="image" src="https://github.com/user-attachments/assets/abb8b5c1-3f11-4ba7-874f-b0ee3f661dbd" />

### Transport Layer

TCP's task is to establish a connection and provide reliable data transfer using ports.  

My machine's source port is 54072, and the server's destination port is 443 (HTTPS).  

<img width="640" height="241" alt="image" src="https://github.com/user-attachments/assets/8acdcae8-3de7-44da-8239-278546e151b7" />

### Application Layer

TLS's task is to secure the connection with encryption.  

<img width="470" height="79" alt="image" src="https://github.com/user-attachments/assets/c8a86ebb-3405-4d97-b39b-a596b15e5d40" />

## Capture Description
"Open surfing-secure.pcap. Take a quick look at it and describe what kind of capture this is."  

- 283 packets.  
- Capture duration 28.3.2025, 11:28:09-11:28:16, so approximately 7 seconds.  
- Two devices, with addresses 192.168.122.7 and 192.168.122.1.  
- Protocols: DNS, TCP, QUIC, and ARP.  

## Network Card Manufacturer  

I entered the MAC address into MAC Address Lookup, but did not get a definitive result. The first three bytes of the source MAC address 52:54:00:2f:e1:e5 indicate a locally administered address, meaning the address is most likely not manufacturer-assigned. (MAC Address Lookup)  
  
<img width="646" height="35" alt="image" src="https://github.com/user-attachments/assets/8654976f-f4d3-4acc-8b03-b090bb898c6c" />


## Web Servers Used by the User

SNI, or Server Name Indication, shows that the user visited terokarvinen.com. Even though the traffic is encrypted, the SNI reveals the server name. (Cloudflare 2026)  

<img width="644" height="14" alt="image" src="https://github.com/user-attachments/assets/3dc1775c-565b-45da-a909-b7bc1c0051d1"/>


## Capturing My Own Traffic  

I captured a small amount of my own traffic while my machine established an HTTPS connection to a Google server.  

### TCP 3-Way Handshake  

SYN: 10.0.2.15 sends a packet from source port 43008 to the server 142.251.152.119 at destination port 443, using the TCP protocol.  
SYN, ACK: The server responds with a packet from port 443 to port 43008, meaning it accepts the connection request.  
ACK: My PC sends a packet back from port 43008 to port 443, after which the TCP connection is established.  

<img width="627" height="35" alt="image" src="https://github.com/user-attachments/assets/4d74f740-93f0-4dcb-9808-0151dce82909" />












## Sources:  

Cloudflare 2026. What is SNI (Server Name Indication)? URL: https://www.cloudflare.com/learning/ssl/what-is-sni/. Accessed: 28.3.2026.
MAC Address Lookup. URL: https://maclookup.app/search/result?mac=5254.00. Accessed: 28.3.2026.
Karvinen, T. 28.3.2025. Verkkoliitäntöjen nimet Linuxissa. URL: https://terokarvinen.com/network-interface-linux/. Accessed: 28.3.2026.
Karvinen, T. 28.3.2025. Wireshark - Aloittaminen. URL: https://terokarvinen.com/wireshark-getting-started/. Accessed: 28.3.2026.













