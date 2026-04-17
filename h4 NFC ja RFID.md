# h4 - NFC ja RFID

## Käytössäni olevat RFID-tuotteet

- Pankkikortti
- Salikortti
- Puhelin
- Passi

## Miten olen suojautunut RFID urkinnalta

En säilytä pankkikorttia, salikorttia tai passia irrallaan, mistä niitä voisi helposti lukea. Pidän ne lompakossa ja lompakkoa laukussa, mikä vähentää riskiä.
Puhelimessani on NFC-ominaisuus, mutta en käytä sitä. Puhelimen käyttö maksamiseen vaatii tunnistautumisen (Face ID tai pääsykoodi), jolloin sitä ei voi käyttää tai lukea ilaman lupaa.
Mahdollinen riski on pankkikortti, koska siinä on lähimaksu ominaisuus pienille summille ilman PIN-koodia. RFID-lukeminen kuitenkin vaatii hyvin pienen etäisyyden, joten en nää riskiä melko suurena.

##  APDU komentojen rakenne

APDU (Application Protocol Data Unit) on NFC-laitteiden ja älykorttien käyttämä viestimuoto. APDU-komento koostuu header (otsikko) ja data (valinnainen) osista.

### Header:

- CLA:	Class byte määrittää komennon tyypin
- INS:	Instruction, eli komento (esim. SELECT)
- P1:	Parametri 1
- P2: Parametri 2

### Data:

- Lc:	Lähetettävän datan pituus
- Data
- Le:	Vastauksen pituus

Tämän kappaleen sisällön ideoinnissa on hyödynnetty ChatGPT 5.3 -kielimallia. Syötteenä käytin: ”APDU komentojen rakenne”.

## RFID hakkerointi uutinen



