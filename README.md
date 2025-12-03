# Add Output to a Shift Register Using Arduino & Dual 74HC595

### Expanding Digital Output Capacity in Computer Architecture

This project demonstrates how to increase the digital output capacity of an Arduino by cascading **two 74HC595 shift registers**. It’s a hands-on application of **Computer Architecture concepts**, including serial communication, register operations, bit shifting, and digital logic control.

---

## 📘 Project Overview

Microcontrollers like Arduino have limited digital output pins.
This project expands the outputs by using:

* **1 × Arduino UNO**
* **2 × 74HC595 Shift Registers (Serial-In Parallel-Out)**
* **LED indicators** to visualize shifting results

By daisy-chaining two shift registers, the Arduino can control **16 outputs using only 3 pins**.

---

## 🧠 Connection to Computer Architecture

This project mirrors real CPU and digital logic operations:

* **Register operations** similar to CPU internal registers
* **Serial-to-parallel conversion**, fundamental in data buses
* **Clock pulse synchronization**
* **Bit shifting**, a key ALU operation
* **Data flow control and timing**
* **Memory organization** using cascaded registers

Applications include:

* CPU instruction pipelines
* I/O port expansion
* Memory addressing
* Hardware-level data transfer

---

## 🎯 Objectives

* Expand Arduino’s output capacity with 74HC595 registers
* Implement serial communication & bit shifting
* Control multiple LEDs with minimal wiring
* Visualize binary output patterns
* Demonstrate practical register cascading

---

## 🛠 Components Used

| Component              | Quantity |
| ---------------------- | -------- |
| Arduino UNO            | 1        |
| 74HC595 Shift Register | 2        |
| Breadboard             | 1        |
| LEDs                   | 16       |
| Jumper Wires           | Many     |
| Resistors              | 16       |
| Power Supply           | 5V       |
| Arduino IDE            | —        |

---

## ⚡ Features

* Expands Arduino outputs using 74HC595
* Controls 16+ outputs with only 3 pins
* Low-cost, simple, and scalable
* Ideal for LEDs, relays, and other digital devices

---

## 🔗 Circuit Diagram

### TinkerCAD Design

![TinkerCAD Design](https://drive.google.com/uc?export=view\&id=1RwbR8MEosHfdNBOiKQnpS_w4OATOm-vu)

### Add Output to Shift Register

![Add Output to Shift Register](https://drive.google.com/uc?export=view\&id=17OB9ARiXhqWIwJ_BQRCNJiAWTMNPACPV)

---

## ⚙️ Working Principle

1. Arduino sends bits **serially** to the first shift register.
2. Bits shift on each clock pulse.
3. After 8 bits, the next 8 cascade to the second register.
4. Latch pin updates outputs → LEDs display the binary pattern.
5. Loop continues to create a shifting effect.

---

## 🧩 Arduino Code

```cpp
int clearPin = 5;
int serialData = 6;
int shiftClock = 7;
int latchClock = 8;

void setup() {
  pinMode(clearPin, OUTPUT);
  pinMode(shiftClock, OUTPUT);
  pinMode(latchClock, OUTPUT);
  pinMode(serialData, OUTPUT);

  digitalWrite(clearPin, LOW);  
  digitalWrite(clearPin, HIGH);
}

void loop() {
  for (int shiftCount = 0; shiftCount < 256; shiftCount++) {
    digitalWrite(latchClock, LOW);
    shiftOut(serialData, shiftClock, MSBFIRST, shiftCount);
    digitalWrite(latchClock, HIGH);
    delay(500);
  }
}
```

---

## 📊 Performance Testing

* Tested in TinkerCAD simulation
* LEDs visually represent binary shifting
* Output shifts left-to-right smoothly
* Cascaded registers work without timing issues

---

## 📝 Results

* Successfully controlled 16 LEDs using 3 pins
* Stable binary shifting demonstrated
* Serial-to-parallel conversion verified
* Reinforced understanding of register-level data manipulation

---

## 📚 Applications

* LED matrix control
* Display boards
* Robotics output control
* Home automation
* CPU-like register simulation
* IoT projects with limited GPIO pins

---

## ⚠️ Limitations

* More cascaded registers increase propagation delay
* Precise timing required
* Noise may appear with long wiring
* Limited by Arduino 5V current capacity

---

## 🚀 Future Improvements

* Expand to 32–64 outputs
* Use latch control for LED animations
* Integrate sensors & real-time inputs
* Build 7-segment or dot-matrix displays
* Wireless control (Bluetooth / Wi-Fi)
* Create a custom library for ease of use

---

## 🙌 Acknowledgment

Developed as part of the **Computer Architecture (CSE-211)** course at **Green University of Bangladesh (GUB)**.
Special thanks to **Mahbubur Rahman** for guidance and support.

---

## 💡 Final Note

This project demonstrates how shift registers efficiently expand Arduino output capacity while reinforcing digital logic and computer architecture concepts.
Whether exploring embedded systems or designing hardware projects, this provides strong foundational understanding.

⭐ Feel free to **star this repository** and explore improvements!

---

## 📩 Contact

**Md. Zehadul Islam**
Email: [gg.solve.zehadul999@gmail.com](mailto:gg.solve.zehadul999@gmail.com)
GitHub: [github.com/mdzehadulislam8](https://github.com/mdzehadulislam8)
