# h1 Sniff

## Tiivistelmä

### Wireshark - Aloittaminen

-Wireshark on verkon kaappaamiseen sekä analysointiin käytettävä työkalu.
-Kaappaus aloitetaan valitsemalla haluttu verkkoliitäntä ja painamalla Start.
-Tilastoista näkee yleiskuvan liikenteestä. Esimerkiksi protokollat ja laitteet.
-Suodattimilla voi rajata liikennettä. Esimerkiksi dns, http ja tls. (Karvinen 28.3.2025)

### Verkkoliitäntöjen nimet Linuxissa

- Verkkoliitännät nimetään Linuxissa systemd:n mukaan. Esimerkiksi enp1s0 ja wlp4s0.
- Tyypit:
  en = langallinen ethernet
  lo = loopback (localhost)
  wl = langaton (WiFi)
-Verkkoliitännän voi tarkistaa komennolla ip a. (Karvinen 28.3.2025)


## Kali Linuxin asennus

Aloitin tehtävän asentamalla Kali Linuxin VirtualBox:iin. Wireshark oli valmiina Kali:ssa, joten sitä ei tarvinut erikseen asentaa tehtävää varten.

## Internet-yhteyden katkaisu ja palautus 

Yhteys päällä

<img width="201" height="141" alt="image" src="https://github.com/user-attachments/assets/6a67c02a-c7b3-4adc-a825-4ce22871ade6" />

Yhteys pois päältä

<img width="438" height="175" alt="image" src="https://github.com/user-attachments/assets/e9889cc0-0e02-48dd-9ab9-cdc22c3adbe6" />

## TCP/IP-malli

Neljä kerrosta yhdestä sieppaamastani paketista:

### Linkkikerros (Link Layer)
Ethernet II
Source MAC (lähettäjä) ja Destination MAC (vastaanottaja)

<img width="645" height="59" alt="image" src="https://github.com/user-attachments/assets/8aabaa3c-811d-4b0f-9d47-734bbc94ffa4" />

### Internet-kerros

Source IP (lähettäjä) 10.0.2.15 ja Destination IP (vastaanottaja) 142.251.150.119.

<img width="527" height="207" alt="image" src="https://github.com/user-attachments/assets/abb8b5c1-3f11-4ba7-874f-b0ee3f661dbd" />

### Kuljetuskerros (Transport Layer)

Koneeni lähdeportti 54072 ja palvelimen kohdeportti 443 HTTPS.

<img width="640" height="241" alt="image" src="https://github.com/user-attachments/assets/8acdcae8-3de7-44da-8239-278546e151b7" />

### Sovelluskerros (Application Layer)



<img width="470" height="79" alt="image" src="https://github.com/user-attachments/assets/c8a86ebb-3405-4d97-b39b-a596b15e5d40" />

## Kaappauksen kuvailu

- Paketteja 283.
- Kaappauksen kesto 28.3.2025 klo 11:28:09-11:28:16, eli noin 7 sekunin ajan.
- Laitteita kaksi kappaletta osoitteilla 192.168.122.7 ja 192.168.122.1.
- Protokollat: DNS, TCP, QUIC ja ARP.

## Verkkokortin merkki

Syötin MAC-osoitteen MAC Address Lookup:iin, mutta en saanut varmaa tulosta. Lähde-MAC-osoite 52:54:00:2f:e1:e5 ensimmäiset kolme tavua viittaa locally administered -osoitteeseen, eli osoite ei todennäköisesti ole valmistajan antama. (MAC Address Lookup)
  
<img width="646" height="35" alt="image" src="https://github.com/user-attachments/assets/8654976f-f4d3-4acc-8b03-b090bb898c6c" />


## Käyttäjän käyttämät web-palvelimet

SNI, eli Server Name Indication kertoo, että käyttäjä on mennyt osoitteeseen terokarvinen.com. Vaikka liikenne on salattua SNI näyttää palvelimen nimen. (Cloudflare 2026)

<img width="644" height="14" alt="image" src="https://github.com/user-attachments/assets/3dc1775c-565b-45da-a909-b7bc1c0051d1"/>


## Oman liikenteen kaappaaminen

Kaappasin pienen määrän omaa liikennettäni, kun koneeni yhdisti HTTPS-yhteyden Googlen palvelimeen. 

### TCP 3-Way Handshake 

SYN: Koneeni 10.0.2.15 lähdeportista 43008 lähettää palvelimelle 142.251.152.119 kohdeporttiin 443 paketin käyttäen TCP-protokollaa.
SYN, ACK: Palvelin vastaa paketilla portista 443 porttiin 43008, eli hyväksyy yhteyspyynnön.
ACK: Koneeni lähettää takaisin portista 43008 porttiin 443, jonka jälkeen TCP-yhteys on muodostettu.

<img width="627" height="35" alt="image" src="https://github.com/user-attachments/assets/4d74f740-93f0-4dcb-9808-0151dce82909" />












## Lähteet

Cloudflare 2026. What is SNI (Server Name Indication)? Luettavissa: https://www.cloudflare.com/learning/ssl/what-is-sni/. Luettu: 28.3.2026.
MAC Address Lookup. Luettavissa: https://maclookup.app/search/result?mac=5254.00. Luettu: 28.3.2026.
Karvinen, T. 28.3.2025. Verkkoliitäntöjen nimet Linuxissa. Luettavissa: https://terokarvinen.com/network-interface-linux/. Luettu: 28.3.2026.
Karvinen, T. 28.3.2025. Wireshark - Aloittaminen. Luettavissa: https://terokarvinen.com/wireshark-getting-started/. Luettu: 28.3.2026.













