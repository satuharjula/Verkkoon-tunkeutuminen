### h7

## Tiivistelmät

Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs

- Spectrum Analyzerilla tarkistetaan, että käytetty taajuus on oikea.  
- Lähetys voidaan tallentaa valitulla taajuudella.  
- URH:lla voidaan tarkistaa, että vastaanotetut bitit on oikein.
- Signaalia voidaan näyttää bittimuodossa, heksadesimaalina tai ASCII-muodossa. (Hubacek 2019)

Decode 433.92 MHz weather station data

- 433 MHz taajuudella toimivia laitteita voidaan dekoodata rtl_433-ohjelmalla.  
- rtl_433 näyttää hyödyllisiä tietoja laitteista ja niiden lähettämistä signaaleista.  
- URH-ohjelmalla voidaan tallentaa ja analysoida signaaleja tarkemmin.  
- Tallennettuja signaaleja voidaan tarkastella raakabitteinä. (Cornelius 2022)


## Lähteet ja läppä  

Tehty.

## rtl_433

rtl_433 asennus: 

Asensin rtl_433 komennolla sudo apt install rtl-433 

Testasin rtl_433 toimivuutta komennolla rtl_433 (Tero Karvinen 2026)

<img width="586" height="123" alt="image" src="https://github.com/user-attachments/assets/e05ed25a-fbb5-471e-aae8-5fd16a01ff07" />

## Automaattinen analyysi

Latasin näytteen Converted_433.92M_2000k.cs8 virtuaalikoneelleni. 

Siirryin hakemistoon komennolla cd ~/Downloads ja etsin näytteen komennolla ls. 

Analysoin tiedoston komennolla rtl_433 -r Converted_433.92M_2000k.cs8 

<img width="649" height="820" alt="image" src="https://github.com/user-attachments/assets/4a249e92-0c68-4eea-b9a8-e08cc9056bbb" />

<img width="637" height="244" alt="image" src="https://github.com/user-attachments/assets/99d9da2a-7039-4158-bac3-9824bcf0e0f1" />

Sama tunniste (ID) 8785315 esiintyi kaikissa. 

Channel: 3  

Model: Nexa-Security, KlikAanKlikUit-Switch ja Proove-Security  

Command: Off. Unit: 3.  


## Too compex 16?  

Latasin tiedoston Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s  kansioon /Downloads  

Siirryin kansioon /Downloads  

Komennoilla:  
cd ~/Downloads  
ls  

Kopioin sen rtl_433-nimelle komenolla:  

cp Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s Recorded_433.92M_2000k.cs8  

Analysoin tiedostoa komennolla:  

rtl_433 -r Recorded_433.92M_2000k.cs8  

<img width="650" height="145" alt="image" src="https://github.com/user-attachments/assets/70473309-b1b0-43a4-9963-1f5b23cfe088" />  

<img width="659" height="445" alt="image" src="https://github.com/user-attachments/assets/e607aebf-d4c2-4626-8e32-67247321263f" />  

<img width="648" height="484" alt="image" src="https://github.com/user-attachments/assets/3f1f6cd8-ce42-4331-b1b7-92f3973224a8" />  

<img width="633" height="80" alt="image" src="https://github.com/user-attachments/assets/5926cb35-06ea-4c3b-ac5f-d4cd327bc669" />  

Tiedosto näyttää samalta kuin aikaisemmassa tehtävässä.  

## Ultimate

Asensin URH:n Ultimate Radio Hacker komennoilla:  

sudo apt-get update  
sudo apt-get -y install pipx  
pipx install urh  
pipx ensurepath  (Tero Karvinen 2026)

<img width="647" height="332" alt="image" src="https://github.com/user-attachments/assets/e0039bf1-b53c-482a-8fa1-5b3e2bfaa275" />  

Latasin 1-on-on-on-HackRF-20250412_113805-433_912MHz-2MSps-2MHz.complex16s -tiedoston koneelleni.  

Asennuksen jälkeen ja tiedoston lataamisen jälkeen suljin terminaalin ja avasin sen uudestaan. Tämän jälkeen syötin komennon urh ja URH graafinen käyttöliittymä avautui.  

Avasin 1-on-on-on-HackRF-20250412_113805-433_912MHz-2MSps-2MHz.complex16s -tiedoston käyttöliittymässä.  

## Yleiskuva


<img width="1481" height="621" alt="image" src="https://github.com/user-attachments/assets/9545c75b-11ca-49e0-915f-f6eb28a7d341" />

Pituus: 5.49 s
Taajuus: 433.912 MHz  
Milloin nauhoitettu: 12.4.2025 klo: 11:38:05  
Taajuudesta näkee kolme kohtaa, jolloin signaalia on lähetetty.  

## Bittistä

Tarkastelin

<img width="920" height="597" alt="image" src="https://github.com/user-attachments/assets/6c7df555-0001-40e9-90b3-ba0c1fd9723b" />  

Samples/Symbol: 500  
Bits/Symbol: 1  
Modulaatio: ASK  

1 bitti 250 mikrosekuntia. Erittäin lyhyt aika esim. verrattuna ihmisen havainnointikykyyn.  


## Lähteet:


Cornelius. 4.1.2022. Decode 433.92 MHz weather station data. One transistor. Luettavissa: https://www.onetransistor.eu/2022/01/decode-433mhz-ask-signal.html. Luettu: 8.5.2026.

Hubacek. 2019. Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs. Katsottavissa: https://youtu.be/sbqMqb6FVMY?t=199. Katsottu: 9.5.2026.

Tero Karvinen 2026. h7. Aaltoja harjaamassa. Luettavissa: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/. Luettu: 9.5.2026.
