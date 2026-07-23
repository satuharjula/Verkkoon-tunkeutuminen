### h7

## Summary

Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs

- A Spectrum Analyzer is used to verify that the correct frequency is being used. 
- The transmission can be recorded on the selected frequency.
- URH can be used to verify that the received bits are correct.
- The signal can be displayed in bit form, hexadecimal, or ASCII format. (Hubacek 2019)

Decode 433.92 MHz weather station data

- Devices operating on the 433 MHz frequency can be decoded using the rtl_433 program. 
- rtl_433 displays useful information about devices and the signals they transmit. 
- The URH program can be used to record and analyze signals in more detail.
- Recorded signals can be examined as raw bits. (Cornelius 2022)

## rtl_433

rtl_433 installation: 

I installed rtl_433 with the command sudo apt install rtl-433

I tested that rtl_433 was working with the command rtl_433 (Tero Karvinen 2026)

<img width="586" height="123" alt="image" src="https://github.com/user-attachments/assets/e05ed25a-fbb5-471e-aae8-5fd16a01ff07" />

## Automatic analysis

I downloaded the sample Converted_433.92M_2000k.cs8 to my virtual machine.

I moved into the directory with the command cd ~/Downloads and located the sample with the command ls.

I analyzed the file with the command rtl_433 -r Converted_433.92M_2000k.cs8.

<img width="649" height="820" alt="image" src="https://github.com/user-attachments/assets/4a249e92-0c68-4eea-b9a8-e08cc9056bbb" />

<img width="637" height="244" alt="image" src="https://github.com/user-attachments/assets/99d9da2a-7039-4158-bac3-9824bcf0e0f1" />

The same identifier (ID) 8785315 appeared in all of them.

Channel: 3  

Model: Nexa-Security, KlikAanKlikUit-Switch, and Proove-Security

Command: Off. Unit: 3.  


## Too compex 16?  

I downloaded the file Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s to the /Downloads folder.

I moved into the /Downloads folder.

With the commands:  
cd ~/Downloads  
ls  

I copied it under the name rtl_433 with the command:

cp Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s Recorded_433.92M_2000k.cs8  

I analyzed the file with the command:

rtl_433 -r Recorded_433.92M_2000k.cs8  

<img width="650" height="145" alt="image" src="https://github.com/user-attachments/assets/70473309-b1b0-43a4-9963-1f5b23cfe088" />  

<img width="659" height="445" alt="image" src="https://github.com/user-attachments/assets/e607aebf-d4c2-4626-8e32-67247321263f" />  

<img width="648" height="484" alt="image" src="https://github.com/user-attachments/assets/3f1f6cd8-ce42-4331-b1b7-92f3973224a8" />  

<img width="633" height="80" alt="image" src="https://github.com/user-attachments/assets/5926cb35-06ea-4c3b-ac5f-d4cd327bc669" />  

The file looks the same as in the previous task.

## Ultimate

I installed URH, Universal Radio Hacker, with the commands:

sudo apt-get update  
sudo apt-get -y install pipx  
pipx install urh  
pipx ensurepath  (Tero Karvinen 2026)

<img width="647" height="332" alt="image" src="https://github.com/user-attachments/assets/e0039bf1-b53c-482a-8fa1-5b3e2bfaa275" />  

I downloaded the file 1-on-on-on-HackRF-20250412_113805-433_912MHz-2MSps-2MHz.complex16s to my computer.

After the installation and downloading the file, I closed the terminal and reopened it. Then I entered the command urh and the URH graphical interface opened.

I opened the file 1-on-on-on-HackRF-20250412_113805-433_912MHz-2MSps-2MHz.complex16s in the interface.

## Overview


<img width="1481" height="621" alt="image" src="https://github.com/user-attachments/assets/9545c75b-11ca-49e0-915f-f6eb28a7d341" />

Length: 5.49 s
Frequency: 433.912 MHz  
When recorded: 12.4.2025 klo: 11:38:05  
Three points can be seen in the frequency where a signal was transmitted.

## BitS

I examined

<img width="920" height="597" alt="image" src="https://github.com/user-attachments/assets/6c7df555-0001-40e9-90b3-ba0c1fd9723b" />  

Samples/Symbol: 500  
Bits/Symbol: 1  
Modulation: ASK  

1 bit is 250 microseconds. An extremely short time, for example compared to human perception ability. 


## Sources:


Cornelius. 4 January 2022. Decode 433.92 MHz weather station data. One transistor. URL: https://www.onetransistor.eu/2022/01/decode-433mhz-ask-signal.html. Accessed: 8.5.2026.

Hubacek. 2019. Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs. URL: https://youtu.be/sbqMqb6FVMY?t=199. Accessed: 9 May 2026.

Tero Karvinen 2026. h7. Aaltoja harjaamassa. URL: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/. Accessed: 9 May 2026.
