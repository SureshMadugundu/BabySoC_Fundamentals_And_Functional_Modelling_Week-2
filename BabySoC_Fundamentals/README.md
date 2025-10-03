# 🔹 Part 1 – BabySoC Fundamentals  

## 📖 Introduction to System-on-Chip (SoC) Design  
A **System-on-Chip (SoC)** integrates all the essential components of a computer system onto a single chip. Instead of having separate chips for CPU, memory, and peripherals, an SoC combines them into one unit, improving **performance, power efficiency, and compactness**.  

SoCs are widely used in smartphones, embedded systems, and high-performance processors because they provide a **cost-effective and scalable solution** for modern computing needs.  

---

## 🧩 Components of an SoC  

1. **CPU (Processing Core)**  
   - The brain of the SoC, responsible for executing instructions.  
   - Can be based on architectures such as **RISC-V, ARM, or x86**.  

2. **Memory**  
   - Stores program instructions and data for the CPU.  
   - Can include **SRAM, DRAM, ROM, or Flash memory**.  

3. **Peripherals**  
   - Input/Output interfaces and controllers (UART, GPIO, SPI, I2C, USB, etc.).  
   - Enable communication with external devices and sensors.  

4. **Interconnect**  
   - The communication backbone of the SoC.  
   - Connects CPU, memory, and peripherals using a **bus or network-on-chip (NoC)**.  


<img src = "./images/simple_soc.png">
---

## 🎯 Why BabySoC?  
The **BabySoC** is a simplified model that allows students and beginners to understand SoC design concepts without overwhelming complexity.  

- It demonstrates the **interaction between CPU, memory, and peripherals** in a minimal design.  
- Helps learners gain confidence before moving into **RTL-level design** and **physical implementation**.  
- Serves as a **practical entry point** into SoC architecture and simulation.  

---
## 🏗️ VSDBabySoC Architecture  

<img src = "./images/vsd_babySoc.png">

### 🔹 Components  

1. **RVMYTH (RISC-V CPU)**  
   - The central processor core of BabySoC.  
   - Based on the open-source RISC-V ISA.  
   - Executes instructions, processes data, and communicates with peripherals.  
   - Uses registers like **r17** to hold and update values for the DAC.  

2. **Phase-Locked Loop (PLL)**  
   - Provides a **stable and synchronized clock** for the SoC.  
   - Ensures that the CPU and peripherals operate in harmony, avoiding timing mismatches.  
   - Scales the reference clock (8× PLL in BabySoC) to meet the SoC’s timing requirements.  

   **Why not rely on external clocks?**  
   - Off-chip clocks suffer from **distribution delays, jitter, and frequency instability**.  
   - Different modules require different frequencies.  
   - Crystal oscillators introduce errors (tolerance, temperature variation, and aging).  
   - PLL ensures **on-chip frequency stability and synchronization**.  

3. **Digital-to-Analog Converter (DAC)**  
   - Converts **10-bit digital values** from RVMYTH into an **analog signal**.  
   - Enables BabySoC to interface with analog devices like **speakers or displays**.  
   - Demonstrates **digital-to-analog integration** in a real-world SoC.  

   **Types of DACs:**  
   - Weighted Resistor DAC  
   - R-2R Ladder DAC (commonly used for scalability and simplicity)  

   In BabySoC, the DAC output is saved in a file called **OUT**, which can then be interpreted by external devices.  

---

## ⚙️ Role of Functional Modelling  
Before moving to RTL coding and physical design, **functional modelling** plays a critical role in validating and understanding the overall system behavior.  

- **Early Validation of Design:**  
  Functional models are used to check whether the system architecture and data flow meet the intended specifications before diving into detailed RTL implementation.  

- **Abstraction from Hardware Complexity:**  
  At this stage, the design is modeled at a higher level of abstraction, focusing on **functionality** rather than low-level hardware details. This helps avoid getting stuck in implementation issues too early.  

- **Faster Simulation and Debugging:**  
  Functional models run much faster than gate-level or RTL models. This allows designers to quickly test and debug high-level features of the SoC.  

- **CPU–Peripheral Interaction:**  
  By simulating modules like the CPU, memory, and basic peripherals, designers can ensure correct **data exchange and communication protocols** within the SoC.  

- **Helps in Architectural Exploration:**  
  Designers can explore different configurations (e.g., memory size, interconnect structure, peripheral inclusion) and evaluate trade-offs **before committing to hardware implementation**.  

- **Bridging the Gap to RTL Design:**  
  Functional modelling provides a **reference behavior** against which RTL implementation can be validated. This ensures consistency and reduces the chances of functional mismatches later.  

- **Cost and Time Savings:**  
  Detecting architectural errors at this stage avoids expensive redesigns in later RTL, physical design, or silicon stages.  

In short, **functional modelling is like a “blueprint simulation”** of the SoC—it verifies the design intent and guides the transition to RTL and physical design with confidence.  

