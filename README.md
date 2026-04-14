# Pong-Beta-CPU-ISA

## 📌 Overview
This project is a hardware-based implementation of the classic Pong game, developed using **Lucid** and deployed on an FPGA.

The system is built around a fully custom-designed **Beta CPU architecture**, including core components such as the ALU, Control Unit, Register File, RAM, and motherboard-level integration. The game logic is executed through a **custom 32-bit Instruction Set Architecture (ISA)**, written in low-level assembly.

---

## 🧠 System Architecture
The project implements a complete processor-based system consisting of:

- Custom **Beta CPU**
- **ALU (Arithmetic Logic Unit)**
- **Control Unit**
- **Register File**
- **Memory Unit (RAM)**
- **Instruction ROM**
- FPGA-level integration (top module)

Instead of using a large finite state machine, the game is executed as a sequence of instructions on the CPU, making the system modular and scalable.

---

## 🎮 Gameplay
- The game is a **2-player Pong game**
- Each player controls a paddle using **2 buttons**:
  - Move Up
  - Move Down
- Total of **4 input buttons**
- The ball moves across the display and bounces based on collision logic implemented in the instruction set

---

## 🔌 Input Handling (game_io_hub)
User inputs are processed through a dedicated module called **`game_io_hub`**:

- Takes in **4 button inputs**
- Applies conditioning (to avoid erratic signals)
- Packs inputs into a **32-bit value**
- Stores the value into a register (memory-mapped I/O)

The CPU continuously reads this value using a **polling mechanism**, ensuring that real-time player input is reflected in the game logic.

---

## ⚙️ Instruction Set (ISA)
The Pong game logic is implemented using a **custom 32-bit ISA**, which enables:

- Ball movement calculations
- Paddle position updates
- Collision detection
- Branching and control flow

This approach allows the game to be executed entirely through instruction-level programming rather than hardcoded hardware logic.

---

## 🛠️ Technologies Used
- **Lucid (Hardware Description Language)**
- **FPGA Development (Alchitry platform)**
- Custom CPU Design
- Low-level Assembly Programming

---

## 🧪 Testing
The project includes multiple test modules for verifying individual components such as:
- ALU
- Control Unit
- Register File
- CPU functionality

---

## 🚀 How to Run (FPGA Setup)
1. Connect the FPGA board (Alchitry)
2. Map the 4 buttons to the input pins defined in the constraint files (`.acf`)
3. Upload the bitstream to the FPGA
4. Use buttons to control paddles during gameplay

> Note: Button mapping depends on your specific FPGA board configuration.

---

## 💡 Key Design Decisions
- Used **polling instead of interrupts** for simplicity and predictable timing
- Avoided large FSM design to reduce hardware complexity
- Used memory-mapped I/O for clean CPU–hardware interaction

---

## 📈 Future Improvements
- Add scoring system
- Improve rendering/display
- Optimize instruction pipeline
- Introduce interrupt-based input handling

---

## 👨‍💻 Author
This project was developed as a first hardware-software integration project to explore:
- Computer architecture
- Digital design
- Embedded systems
