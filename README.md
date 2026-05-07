# RFID-ATTENDANCE-SYSTEM

## Project Overview

This project presents a **simple, efficient, and automated attendance system** using **RFID technology** and an **ESP8266 (NodeMCU)** microcontroller.

Each user is assigned a unique RFID card. When scanned:

* The system reads the card UID
* Displays the user’s name on an LCD
* Gives buzzer feedback
* Sends attendance data to Google Sheets via WiFi

This eliminates manual errors, reduces time, and improves accuracy.

---

## Abstract

Traditional attendance systems are time-consuming and prone to errors. This project uses RFID technology to automate attendance marking.

The RFID reader (RC522) scans a card and sends its UID to the ESP8266. The system verifies the user and logs attendance instantly. A 16×2 LCD displays confirmation, and a buzzer provides feedback.

This system is fast, reliable, and suitable for schools, colleges, and offices.

---

## Aim

To design and implement an **RFID-based attendance system** that automatically records attendance using RFID cards.

---

## Components Used

* ESP8266 (NodeMCU)
* RC522 RFID Reader
* RFID Tags/Cards
* 16x2 I2C LCD Display
* Buzzer
* Jumper Wires
* Breadboard

---

## Software Used

* Arduino IDE

---

## Theory

### What is RFID?

RFID (Radio Frequency Identification) is a wireless communication technology used to identify objects using radio waves.

Each RFID tag contains a **unique identifier (UID)**.

### Working Principle

1. RFID card is brought near the reader
2. Reader scans UID using radio waves
3. Microcontroller processes UID
4. System verifies user
5. Attendance is recorded

### Key Features

* Contactless identification
* Unique authentication
* Real-time logging
* Fast processing
* Easy integration with cloud

---

## Circuit Diagram

<p align="center">
  <img src="images/circuitdiagram.png" width="500"/>
</p>


---

## Hardware Connections
<p align="center">
  <img src="images/hardware.png" width="500"/>
</p>

### RFID RC522 → NodeMCU

* SDA → D4
* SCK → D5
* MOSI → D7
* MISO → D6
* RST → D3
* GND → GND
* 3.3V → 3.3V

### LCD (I2C)

* SDA → D2
* SCL → D1

### Buzzer

* Signal → D8

---

## Working Flow

1. System initializes
2. WiFi connects
3. LCD shows “Scan your Card”
4. RFID card is detected
5. UID is read
6. Name is displayed
7. Buzzer beeps
8. Data sent to Google Sheets
9. System waits for next card

---

## Flowchart
<p align="center">
  <img src="images/flowchart.png" width="500"/>
</p>*(Add flowchart image here)*

---

## Code Overview

Main libraries used:

```cpp
#include <SPI.h>
#include <MFRC522.h>
#include <ESP8266WiFi.h>
#include <ESP8266HTTPClient.h>
#include <LiquidCrystal_I2C.h>
```

### Key Functional Parts

#### 1. Initialization

* LCD setup
* WiFi connection
* SPI communication

#### 2. Card Detection

```cpp
if (!mfrc522.PICC_IsNewCardPresent()) return;
if (!mfrc522.PICC_ReadCardSerial()) return;
```

#### 3. Data Reading

Reads RFID memory block:

```cpp
mfrc522.MIFARE_Read(blockNum, readBlockData, &bufferLen);
```

#### 4. Output

* LCD display
* Serial monitor
* Buzzer feedback

#### 5. Cloud Upload

```cpp
https.GET();
```

---

## SWOT Analysis

### Strengths

* Fast and contactless
* Accurate attendance
* Easy to use
* Real-time data logging

### Weaknesses

* Requires hardware setup
* Limited range
* Depends on WiFi
* Cards can be lost

### Opportunities

* Can integrate mobile apps
* Expand to hostel/library systems
* Cloud dashboard integration

### Threats

* RFID cloning
* Hardware failure
* Signal interference

---

## Observations

* System works reliably when WiFi is connected
* Fast response time (milliseconds)
* Accurate UID detection
* LCD and buzzer improve usability

---

## Conclusion

The RFID-based attendance system successfully automates attendance recording using contactless technology.

It improves:

* Accuracy
* Efficiency
* Speed

The system is cost-effective and scalable, and can be enhanced with:

* Mobile apps
* Biometrics
* Cloud databases

---

## Precautions

* Ensure proper wiring
* Avoid damaged RFID cards
* Keep system away from interference
* Maintain stable power supply

---

## References

* RFID Technology Basics
* Arduino Documentation
* MFRC522 Datasheet
* Google Sheets API

---

## Authors

* Titiksha Gupta (24DEC023)
* Arush Dakhera (24DEC045)

---

## Institution

The LNM Institute of Information Technology, Jaipur

---

## Future Improvements

* Mobile app integration
* Face recognition system
* Database storage
* Enhanced security

---
