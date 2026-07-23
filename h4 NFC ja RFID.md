# h4 - NFC and RFID

## RFID products I use

- Bank card
- Gym membership card
- Phone
- Passport

## How I protect myself from RFID skimming

I don't keep my bank card, gym card, or passport lying around loose, where they could easily be read. I keep them in my wallet, and the wallet in my bag, which reduces the risk.

My phone has NFC capability, but I don't use it. Using the phone for payments requires authentication (Face ID or passcode), so it can't be used or read without permission.

A possible risk is the bank card, since it has a contactless payment feature for small amounts without a PIN code. However, RFID reading requires a very short distance, so I don't consider the risk to be particularly high.

##  APDU command structure

APDU (Application Protocol Data Unit) is the message format used by NFC devices and smart cards. An APDU command consists of a header and (optional) data section.

### Header:

- CLA: Class byte defines the type of command
- INS: Instruction, i.e. the command (e.g. SELECT)
- P1:	Parameter 1
- P2: Parameter 2

### Data:

- Lc:	Length of the data being sent
- Data
- Le:	Length of the response

The content of this section was developed with the help of the ChatGPT 5.3 language model. I used the following prompt: "APDU command structure."

## RFID hacking news

URL: https://www.is.fi/digitoday/art-2000001821216.html. 

The news story described how Austrian hacker Adrian Dabrowski tested the electronic lock system of his own apartment building. He obtained an RFID reader and built a device capable of both copying and reading data from key cards. He sent the reader through the mail, allowing it to scan other people's RFID cards along the way—for example, the mail carrier's master key.

Using the collected data, he was able to create a card simulator that functioned like a real key card. With the device, he managed to open 43% of the doors in his own building, and up to 93% of doors with a certain lock system.

The total cost of the attack for Dabrowski was under 15 euros, which shows how easily and cheaply RFID-based lock systems can be compromised.

