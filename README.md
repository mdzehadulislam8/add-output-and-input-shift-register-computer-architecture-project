# Add Output to a Shift Register Using Arduino & Dual 74HC595  
### Expanding Digital Output Capacity in Computer Architecture

This project demonstrates how to increase the digital output capacity of an Arduino by cascading **two 74HC595 shift registers**. It is a hands-on application of **Computer Architecture concepts**, especially serial communication, register operations, data shifting, and digital logic control.

---

## 📘 Project Overview
Microcontrollers like Arduino have limited digital output pins.  
To overcome this limitation, this project uses:

- **1 Arduino UNO**
- **2× 74HC595 Shift Registers (Serial-In Parallel-Out Register)**  
- **LED Indicators to show shifting results**

By daisy-chaining two shift registers, the Arduino can control **16 output devices using only 3 Arduino pins**.

---

## 🧠 Why This Project Relates to Computer Architecture

This project directly connects with **computer architecture** because it involves:

- **Register operations** (similar to CPU internal registers)
- **Serial-to-parallel conversion**, an important concept in data buses
- **Clock pulse synchronization**
- **Bit shifting** (fundamental in ALU & digital logic)
- **Data flow control and timing**
- **Memory organization with cascaded registers**

Shift registers are frequently used in:

✔ CPU instruction pipelines  
✔ I/O port expansion  
✔ Memory addressing  
✔ Hardware-level data transfer  

So this project reflects real-world architectural design principles.

---

## 🎯 Objectives

- Expand Arduino’s output capacity using 74HC595 shift registers  
- Implement serial communication & bit shifting  
- Control multiple LEDs through optimized wiring  
- Visualize stored binary output  
- Demonstrate a practical use-case of register cascading  

---

## 🛠 Components Used

| Component | Quantity |
|----------|----------|
| Arduino UNO | 1 |
| 74HC595 Shift Register | 2 |
| Breadboard | 1 |
| LEDs | 16 |
| Jumper Wires | Many |
| Resistors | 16 |
| Power Supply | 5V |
| Arduino IDE | — |

---

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
## 🔗 Circuit Diagram  

### TinkerCAD Design  
![TinkerCAD Design](https://github.com/USERNAME/REPO_NAME/blob/main/images/tinkercad_design.png)

### Full Circuit Overview  
![Full Circuit](https://github.com/USERNAME/REPO_NAME/blob/main/images/full_circuit.png)

### Arduino with Dual 74HC595  
![Shift Register Setup](https://github.com/USERNAME/REPO_NAME/blob/main/images/shift_register_setup.png)

### TinkarCad Design
![Implementation Details](https://drive.google.com/uc?export=view&id=1RwbR8MEosHfdNBOiKQnpS_w4OATOm-vu)
###  Add Output to Shift Register
![Add Output to Shift Register](https://drive.google.com/uc?export=view&id=17OB9ARiXhqWIwJ_BQRCNJiAWTMNPACPV)


---

## ⚙️ Working Principle (Workflow)

1. Arduino sends bits **serially** to the first shift register.  
2. Bits are shifted on each clock pulse.  
3. When 8 bits are filled, the next 8 bits cascade to the second register.  
4. Latch pin updates output → LEDs display the binary pattern.  
5. Loop continues, showing shifting effect from left-to-right.

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
---
📊 Performance Testing
- Tested in TinkerCAD Simulation
- LEDs visually represent binary shifting
- Output shifts from left to right, confirming correct timing and storage
- Cascade registers work smoothly without delay issues
---
📝 Results
- Successfully controlled 16 LEDs using only 3 Arduino pins
- Demonstrated stable binary shifting
- Verified serial-to-parallel conversion
- Enhanced understanding of register-level data manipulation
---
📚 Applications
- LED Matrix Control
- Display Boards
- Robotics Output Control
- Home Automation
- CPU-like register operations simulation
- IoT projects with limited GPIO pins
---
⚠️ Limitations
- Cascading more registers increases propagation delay
- Requires precise timing
- Noise issues may appear if wiring is long
- Limited by Arduino’s 5V current capacity
---
🚀 Future Improvements
- Add more shift registers (32 or 64 output system)
- Use latch control for animations
- Integrate with sensors & real-time input
- Build a 7-segment or dot-matrix display
- Wireless control (Bluetooth / Wi-Fi)
- Create custom libraries for ease of use
---

## 🙌 Acknowledgment
This project was developed as part of the **Computer Architecture (CSE-211)** course at  
**Green University of Bangladesh (GUB)**.  
Special thanks to our course instructor **Mahbubur Rahman** for guidance and support.

---

## 💡 Final Note
This project demonstrates how shift registers can efficiently expand Arduino's output capacity while reinforcing key concepts of digital logic and computer architecture.  
Whether you're exploring embedded systems, designing hardware-based projects, or learning how registers operate in real processors — this work provides a strong foundational understanding.

If you found this project helpful, feel free to ⭐ **star this repository** and explore further improvements!

---

## 📩 Contact
**Md. Zehadul Islam**  
Email: gg.solve.zehadul999@gmail.com*  
GitHub: [github.com/mdzehadulislam8](https://github.com/mdzehadulislam8)

---

### 🔚 End of Document  
Thank you for exploring this project!  
Happy Coding & Keep Building 🚀
