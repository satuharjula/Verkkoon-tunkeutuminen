# h2 Lempiväri: Violetti

## Pyramid of Pain
rgijer

## Diamond Model
grojdf

## Apache log

Asensin Apachen virtuaalikoneelleni seuraavilla komennoilla:

sudo apt-get update

sudo apt-get install apache2

sudo systemctl start apache2

Siirryin salaamattomalla HTTP-yhteydellä osoitteeseen http://localhost, jonka jälkeen etsin lataustani vastaavan lokirivin komennolla sudo tail -F /var/log/apache2/access.log

<img width="654" height="77" alt="image" src="https://github.com/user-attachments/assets/7a51cdf3-0722-4e58-9d91-11f8d71787f0" />

::1 On IPv6 loopback-osoite, joka vastaa IPv4-osoitetta 127.0.0.1. (Dhandala 20.3.2026) Eli pyyntö tulee koneeltani.

- - Ensimmäinen tarkoittaa identd-tunnusta, eli kuka käyttäjä teki yhteyden. Toinen tarkoittaa kirjautunutta käyttäjää sivulle, joka ei ole saatavilla. (Apache 2026)

[11/Apr/2026:14:42:59 -0400] On aikaleima, jolloin pyyntö tehtiin.

"GET / HTTP/1.1" On HTTP-pyyntö, jonka curl lähetti palvelimelle.

200 On palvelimen vastaus pyyntöön, joka kertoo, että se onnistui. 

10958 On vastauksen koko.

"-" Tarkoittaa, että edellistä sivua ei ole.

"curl/8.18.0" On tieto siitä, millä ohjelmalla pyyntö tehtiin. (Apache 2026)

## Nmapped

Irrotin virtuaalikoneeni Internetistä testien ajaksi.

Skannasin oman web-palvelimeni portin 80 komennolla sudo nmap -A -p 80 127.0.0.1 ja tulokset olivat seuraavat:

<img width="717" height="380" alt="image" src="https://github.com/user-attachments/assets/f61722e8-2ccf-46ee-81ce-aa1554395674" />

80/tcp Tarkoittaa HTTP:n käyttämää porttia ja TCP-protokollaa.

open Tarkoittaa, että portti on auki.

http Tarkoittaa, että web-palvelu toimii portissa.

Apache httpd 2.4.66 (Debian) Tarkoittaa Apache-web-palvelinta ja sen versiota.

Näiden lisäksi nmap tunnisti käyttöjärjestelmän ja sen version sekä, että kohteena on oma kone.


## Skriptit

Automaattisesti päällä olevat skriptit:

http-title: Apache2 Debian Default Page: It works, joka kertoo sivun otsikon.
http-server-header: Apache/2.4.66 (Debian), joka kertoo palvelimen ohjelmiston ja version.

## Jäljet lokissa

Etsin porttiskannauksen jälkiä komennolla sudo grep -i nmap /var/log/apache2/access.log

Lokista löytyi kohtia “Nmap Scripting Engine”, mikä tarkoittaa että pyynnöt tulivat nmap:ilta.

 Selitä osumat. Millaisilla hauilla tai säännöillä voisit tunnistaa porttiskannauksen jostain muusta lokista, jos se on niin laaja, että et pysty lukemaan itse kaikkia rivejä?

<img width="718" height="149" alt="image" src="https://github.com/user-attachments/assets/9bdc9388-c744-41b4-a819-f2082b52e826" />


## Wire sharking

Avasin Wiresharkin ja valitsin lo (loopback), jonka jälkeen aloitin kaappauksen painamalla start. Samaan aikaan ajoin komennon sudo nmap -A -p 80 127.0.0.1, jonka jälkeen lopetin kaappauksen Wiresharkissa.
Etsin Wiresharkissa paketit suodattimella frame contains "nmap".
Lyhyessä ajassa lähtee paljon erilaisia HTTP-pyyntöjä samaan kohteeseen.
Pakettien joukossa näkyi erilaisia HTTP-pyyntöjä, kuten GET, POST, OPTIONS ja PROPFIND, sekä pyyntöjä epätavallisiin polkuihin, esimerkiksi /nmaplowercheck ja /robots.txt.

<img width="1231" height="247" alt="image" src="https://github.com/user-attachments/assets/eb72e4ea-ec7d-414c-8702-d25c14dd4cae" />

<img width="883" height="102" alt="image" src="https://github.com/user-attachments/assets/c0a60a0f-3f75-4196-9c21-2afca40f723d" />

## Net grep

Ajoin komennon sudo ngrep -d lo -i nmap ja toisessa terminaalissa komennon sudo nmap -A -p 80 127.0.0.1.

<img width="807" height="649" alt="image" src="https://github.com/user-attachments/assets/953f4b2f-aa09-434b-ab4c-e1ff4f1aeb19" />

## Agentti & Pienemmät jäljet

Vaihdoin nmap:n user-agent:n komenolla sudo nmap -A -p 80 --script-args http.useragent="Mozilla/5.0" 127.0.0.1

Tarkistin, että se vaihtui komennolla sudo tail -n 10 /var/log/apache2/access.log. Tekstijonoa "nmap" ei enää löydy.

<img width="784" height="166" alt="image" src="https://github.com/user-attachments/assets/106539d7-07ee-4b89-93c8-0bb3f6680f41" />

Myös siepatussa verkkoliikentessä näkyi user-agentin muuttuneen.

<img width="658" height="53" alt="image" src="https://github.com/user-attachments/assets/8e8c423e-0960-4c1d-a86b-573b5ad1c6ca" />


## LoWeR ChEcK






















## Lähteet:

Dhandala, N. 20.3.2026. How to Use the IPv6 Loopback Address (::1). OneUptime blog. Luettavissa: https://oneuptime.com/blog/post/2026-03-20-use-ipv6-loopback-address/view. Luettu: 11.4.2026.
Apache 2026. Log Files. Luettavissa: https://httpd.apache.org/docs/current/logs.html. Luettu: 11.4.2026.
