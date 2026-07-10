# h2 Favorite color: Purple

## Pyramid of Pain

The Pyramid of Pain illustrates how difficult it is for an attacker to change different indicators of an attack. The higher up the pyramid you are, the harder it is for the attacker to change the indicators, and therefore the more useful they are for defense. (Bianco 17.1.2014)  

## Diamond Model

Describes a cyberattack through the attacker, the victim, the infrastructure, and the tools used. It helps in understanding the attack as a whole and the connections between its different parts. (Caltagirone, Pendergast & Betz 2020)  

## Apache log

I installed Apache on my virtual machine using the following commands:  

sudo apt-get update  

sudo apt-get install apache2  

sudo systemctl start apache2  

I navigated to http://localhost over an unencrypted HTTP connection, then I looked for the log entry matching my request using the command sudo tail -F /var/log/apache2/access.log  

<img width="654" height="77" alt="image" src="https://github.com/user-attachments/assets/7a51cdf3-0722-4e58-9d91-11f8d71787f0" />

::1 is the IPv6 loopback address, corresponding to the IPv4 address 127.0.0.1. (Dhandala 20.3.2026) So the request comes from my own PC.  

--The first refers to the identd identifier, meaning which user made the connection. The second refers to the logged-in user for the page, which is not available. (Apache, 2026)  

[11/Apr/2026:14:42:59 -0400] is the timestamp when the request was made.  

"GET / HTTP/1.1" is the HTTP request that curl sent to the server.  

200 is the server's response to the request, indicating that it was successful.  

10958 is the size of the response.  

"-" means that there is no referrer page.  

"curl/8.18.0" indicates the program used to make the request. (Apache 2026)  

## Nmapped

I disconnected my virtual machine from the internet for the duration of the tests.  

I scanned my own web server's port 80 using the command sudo nmap -A -p 80 127.0.0.1, and the results were as follows:  

<img width="717" height="380" alt="image" src="https://github.com/user-attachments/assets/f61722e8-2ccf-46ee-81ce-aa1554395674" />

80/tcp indicates the port used by HTTP and the TCP protocol.  

open means that the port is open.  

http means that the web service is running on that port.  

Apache httpd 2.4.66 (Debian) indicates the Apache web server and its version.  

In addition to this, nmap identified the operating system and its version, as well as the fact that the target is the local machine.  


## Scripts

Automatically enabled scripts:  

http-title: Apache2 Debian Default Page: It works, which indicates the page title.  
http-server-header: Apache/2.4.66 (Debian), which indicates the server software and version.  

## Traces in the log

I searched for traces of the port scan using the command sudo grep -i nmap /var/log/apache2/access.log  

The log contained entries with "Nmap Scripting Engine", indicating that the requests came from nmap.  

<img width="718" height="149" alt="image" src="https://github.com/user-attachments/assets/9bdc9388-c744-41b4-a819-f2082b52e826" />

You can identify a port scan, for example, by searching the log for the text "nmap" and examining the User-Agent. A large number of requests from the same IP address, multiple 404 errors, and unusual URL requests suggest a scan.  

## Wire sharking

I opened Wireshark and selected lo (loopback), then started the capture by pressing start. At the same time, I ran the command sudo nmap -A -p 80 127.0.0.1, after which I stopped the capture in Wireshark.  
I searched for packets in Wireshark using the filter frame contains "nmap".  
A large number of different HTTP requests are sent to the same target in a short period of time.  
Among the packets, various HTTP requests were visible, such as GET, POST, OPTIONS, and PROPFIND, as well as requests to unusual paths, for example /nmaplowercheck ja /robots.txt.  

<img width="1231" height="247" alt="image" src="https://github.com/user-attachments/assets/eb72e4ea-ec7d-414c-8702-d25c14dd4cae" />

<img width="883" height="102" alt="image" src="https://github.com/user-attachments/assets/c0a60a0f-3f75-4196-9c21-2afca40f723d" />

## Net grep

sudo nmap -A -p 80 127.0.0.1.

I ran the command sudo ngrep -d lo -i nmap in one terminal, and in another terminal the command  sudo nmap -A -p 80 127.0.0.1.  

<img width="807" height="649" alt="image" src="https://github.com/user-attachments/assets/953f4b2f-aa09-434b-ab4c-e1ff4f1aeb19" />

## Agent & Smaller Traces

I changed nmap's user-agent using the command sudo nmap -A -p 80 --script-args http.useragent="Mozilla/5.0" 127.0.0.1

I verified that it had changed using the command sudo tail -n 10 /var/log/apache2/access.log. 

<img width="784" height="166" alt="image" src="https://github.com/user-attachments/assets/106539d7-07ee-4b89-93c8-0bb3f6680f41" />

The change in the user-agent was also visible in the captured network traffic.

<img width="658" height="53" alt="image" src="https://github.com/user-attachments/assets/8e8c423e-0960-4c1d-a86b-573b5ad1c6ca" />


## LoWeR ChEcK

<img width="661" height="70" alt="image" src="https://github.com/user-attachments/assets/71eb43ca-4e42-4d4a-8656-646c9acea08c" />

I started editing the file using the command sudo nano nselib/http.lua

<img width="543" height="91" alt="image" src="https://github.com/user-attachments/assets/120345c0-29e3-4e72-b57b-ebe6d2914706" />

<img width="535" height="80" alt="image" src="https://github.com/user-attachments/assets/9d15ff61-38c3-4e6e-ac4c-2801a71ec5dc" />

I saved the changes and started the port scan again.

Wireshark:

<img width="942" height="365" alt="image" src="https://github.com/user-attachments/assets/dbc0d041-b4b5-4871-966f-4ba76fb7a5b1" />

## FCC ID

I chose the JBL Tune Beam headphones as the device. (FCC ID: APIJBLTUNEBEAM) and looked up their information in the FCC database. I found internal images of the headphones, and it turned out that the device operates on the 2.4 GHz frequency and uses a Bluetooth connection.

## Sources:

Apache 2026. Log Files. URL: https://httpd.apache.org/docs/current/logs.html. Accessed: 11.4.2026.

Bianco, D. 17.1.2014. The Pyramid of Pain. URL: https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html. Accessed: 11.4.2026.

Caltagirone, S., Pendergast, A & Betz, C. 2020. The Diamond Model of Intrusion Analysis. URL: https://www.threatintel.academy/wp-content/uploads/2020/07/diamond-model.pdf. Accessed: 11.4.2026.

Dhandala, N. 20.3.2026. How to Use the IPv6 Loopback Address (::1). OneUptime blog. URL: https://oneuptime.com/blog/post/2026-03-20-use-ipv6-loopback-address/view. Accessed: 11.4.2026.

FCC-raport 2026. APIJBLTUNEBEAM. URL: https://fcc.report/FCC-ID/APIJBLTUNEBEAM. Accessed: 11.4.2026.
