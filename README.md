# Arduino Output Expansion Using Dual 74HC595

## 🔍 Overview
This project expands the output capability of an Arduino by cascading two 74HC595 shift registers. Using serial-to-parallel conversion, the Arduino can control many outputs using only a few pins—ideal for LEDs, displays, and automation tasks.

## ⚡ Features
- Expands Arduino outputs using 74HC595
- Controls 16+ outputs with only 3 Arduino pins
- Simple, low-cost, and scalable
- Suitable for LEDs, relays, and digital devices

## 🛠️ Components
- Arduino UNO / Nano
- 2 × 74HC595 Shift Registers
- Breadboard & jumper wires
- LEDs + resistors
- Arduino IDE
## Implementation Details
### TinkarCad Design
![Implementation Details](https://drive.google.com/uc?export=view&id=1RwbR8MEosHfdNBOiKQnpS_w4OATOm-vu)
###  Add Output to Shift Register
![Add Output to Shift Register](https://drive.google.com/uc?export=view&id=17OB9ARiXhqWIwJ_BQRCNJiAWTMNPACPV)

## 📌 Arduino Code (Example)
```cpp
int clearPin = 5;
int serialData = 6;
int shiftClock = 7;
int latchClock = 8;

void setup() {
  pinMode(clearPin, OUTPUT);
  pinMode(serialData, OUTPUT);
  pinMode(shiftClock, OUTPUT);
  pinMode(latchClock, OUTPUT);

  digitalWrite(clearPin, LOW);
  digitalWrite(clearPin, HIGH);
}

void loop() {
  for (int i = 0; i < 256; i++) {
    digitalWrite(latchClock, LOW);
    shiftOut(serialData, shiftClock, MSBFIRST, i);
    digitalWrite(latchClock, HIGH);
    delay(500);
  }
}
