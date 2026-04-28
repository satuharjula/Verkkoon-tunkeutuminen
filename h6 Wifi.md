## 

sudo su
cat /root/flag.txt

<img width="601" height="201" alt="Näyttökuva 2026-04-27 233459" src="https://github.com/user-attachments/assets/c93cd2a7-86b6-4ebf-aad8-543412596591" />


Loin Wifi-kansion komennolla mkdir ~/wifi




Skannasin kaikki kanavat löytääkseni "wifi-global" -verkon ja sen kanavan

sudo airmon-ng start wlan0
sudo airodump-ng wlan0mon -w ~/wifi/scan --manufacturer --wps --band abg

Pysäytin skannauksen ja etsin tallennetusta tiedostosta

<img width="692" height="114" alt="Näyttökuva 2026-04-27 234451" src="https://github.com/user-attachments/assets/f7cf9fb8-71ad-4246-85fd-8da980cb1ec0" />

Wifi-global käyttää kanavaa 11.


### 03 03. What is the probe of 78:C1:A7:BF:72:46 that follows the format of the other networks in the range (wifi-)?

Komennolla sudo airodump-ng wlan0mon -w scan --manufacturer --wps --band abg

<img width="866" height="248" alt="image" src="https://github.com/user-attachments/assets/7d5e6ae5-6ae1-4f05-8f2c-6d6c038833a3" />

STATION-osiossa näkyy rivi 78:C1:A7:BF:72:46, jonka Probes-sarakkeessa näkyy verkkonimi "wifi-offices, Jason".


### 04. What is the ESSID of the hidden AP (mac F0:9F:C2:6A:88:26)?

Komennolla:

cat ~/rockyou-top100000.txt | awk '{print "wifi-" $1}' > ~/wifi-rockyou.txt

iwconfig wlan0mon channel 11

mdk4 wlan0mon p -t F0:9F:C2:6A:88:26 -f ~/wifi-rockyou.txt

<img width="871" height="233" alt="image" src="https://github.com/user-attachments/assets/b33503e3-5de4-4b44-9e93-f775219cf777" />

Piilotetun AP:n ESSID on: wifi-free

### 05. What is the flag in the hidden AP router behind default credentials?














