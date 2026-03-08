<details>
<summary>Experiment 15: Amplitude Shift Keying (ASK)</summary>

## Introduction
Amplitude Shift Keying (ASK) is the digital equivalent of **Amplitude Modulation (AM)**. In this scheme, a binary data stream acts as the modulating signal, switching a high-frequency carrier wave between two distinct amplitude levels—typically a specific voltage for logic **'1'** and **0V for logic '0'** (also known as **On-Off Keying**). This allows digital data to be transmitted over analog mediums like **radio waves or fiber optics**.

## Objectives
- **Carrier Modulation:** Successfully switch a sine wave carrier using a unipolar digital signal.  
- **Asynchronous Demodulation:** Recover the original bitstream using non-coherent envelope detection.  
- **Pulse Shaping:** Observe filtering effects on square pulses and use a comparator to restore digital integrity.

## Materials Used
- Emona Telecoms-Trainer 101  
- Oscilloscope (Dual Channel, 20MHz)  
- Modules: Sequence Generator, Dual Analog Switch, VCO (100kHz carrier), Utilities (Rectifier), Tuneable LPF  

## Procedures

### Part A – Generation
A **2kHz digital signal** controls a Dual Analog Switch.  
A **100kHz sine carrier** is applied to the switch input.  
- Data = High → Carrier passes through  
- Data = Low → Output = 0V

### Part B – Detection
The ASK signal passes through a **diode rectifier**, converting negative cycles into positive ones.

### Part C – Filtering
The rectified signal enters the **Tuneable LPF**. Adjusting the cut-off removes carrier ripples and produces a **rounded digital waveform**.

### Part D – Restoration
The filtered signal is sent to a **Comparator**. A threshold reference voltage restores a **clean digital signal**.

## Questions

**Why is the carrier frequency much higher than the data frequency?**  
To ensure multiple carrier cycles occur within one bit period, making envelope detection reliable.

**What is the main disadvantage of ASK?**  
ASK is highly susceptible to **noise**, which can create false pulses.

## Overall Conclusion
ASK demonstrates simple digital modulation. However, filtering rounds the recovered pulses, so a **comparator stage is necessary to restore the digital waveform**.

</details>

---

<details>
<summary>Experiment 16: Binary Phase Shift Keying (BPSK)</summary>

## Introduction
Binary Phase Shift Keying (**BPSK**) is a digital modulation scheme where information is encoded by **shifting the carrier phase by 180°**. Unlike ASK, the **amplitude remains constant**, making BPSK more resistant to amplitude noise.

## Objectives
- **Phase Manipulation:** Map logic **0 → 0° phase** and **1 → 180° phase**.  
- **Balanced Modulation:** Use a Balanced Modulator to create a **suppressed-carrier signal**.

## Materials Used
- Emona Telecoms-Trainer 101  
- Sequence Generator  
- Balanced Modulator  
- Master Signals module (100kHz sine carrier)

## Procedures

### System Setup
Connect the **100kHz carrier** to the Balanced Modulator carrier input.  
Connect the **digital data stream** to the message input.

### Phase Observation
Use the oscilloscope’s **zoom/sweep magnification** to observe transitions.

### Analysis
Observe the **phase jump** whenever the digital signal changes state.

## Overall Conclusion
BPSK successfully encodes digital information using **phase changes rather than amplitude changes**, producing a **suppressed-carrier signal** and improving noise immunity.

</details>

---

<details>
<summary>Experiment 17: Binary Phase Shift Keying (Generation & Recovery)</summary>

## Introduction
This experiment introduces **BPSK demodulation** using a **Product Detector**. Because BPSK is a **suppressed carrier signal**, envelope detection cannot be used. The receiver must generate a **coherent carrier synchronized with the transmitter**.

## Objectives
- Implement **coherent demodulation** using a product detector.  
- Understand the need for **carrier synchronization**.

## Procedures

### Generation
Follow the **BPSK generation process from Experiment 16**.

### Product Detection
Feed the BPSK signal into a **Multiplier** and apply the original **100kHz carrier** to the other input.

### Baseband Extraction
Use a **Tuneable LPF** to remove the high-frequency components, leaving the baseband signal.

### Restoration
Use a **Comparator** to recover the digital pulses.

## Questions

**What happens if the local carrier phase shifts by 90°?**  
The output drops to **zero**, since orthogonal signals multiply to zero.

**Why is BPSK better than ASK?**  
It achieves a **lower Bit Error Rate (BER)** in noisy environments.

## Overall Conclusion
BPSK provides **better noise immunity**, but the receiver must maintain **precise synchronization** with the carrier.

</details>

---

<details>
<summary>Experiment 18: Quadrature Phase Shift Keying (QPSK)</summary>

## Introduction
Quadrature Phase Shift Keying (**QPSK**) is a multi-level modulation technique that **transmits two bits per symbol**, doubling the data rate within the same bandwidth. It uses **four phase states**: 45°, 135°, 225°, and 315°.

## Objectives
- **Bit Splitting:** Separate a serial bitstream into **I (In-phase)** and **Q (Quadrature)** streams.  
- **Orthogonal Modulation:** Modulate sine and cosine carriers independently.

## Materials Used
- Serial-to-Parallel Converter  
- Phase Shifter module  
- Two Multiplier modules  
- Adder module  

## Procedures

### Serial-to-Parallel Conversion
Split the Sequence Generator output into **I and Q streams**.

### Carrier Generation
Generate a **cosine carrier** by passing a sine wave through a **90° Phase Shifter**.

### I/Q Modulation
- I stream → Sine carrier  
- Q stream → Cosine carrier

### Vector Summation
Combine both signals using the **Adder module** to create the **QPSK signal**.

## Overall Conclusion
QPSK effectively combines **two BPSK systems**, allowing **twice the data rate within the same bandwidth**, forming the basis of many modern wireless communication systems.

</details>

---

<details>
<summary>Experiment 19: DSSS Modulation & Demodulation</summary>

## Introduction
Direct Sequence Spread Spectrum (**DSSS**) multiplies the message signal by a **fast Pseudo-Noise (PN) sequence**, spreading the signal across a wide bandwidth. This improves **interference resistance and security**.

## Objectives
- Observe how PN sequences **increase bandwidth**.  
- Recover signals even with **narrow-band interference**.

## Procedures

### Spreading
Multiply a **slow digital signal (2kHz)** with a **faster PN sequence**.

### Despreading
At the receiver, multiply the spread signal by the **same PN sequence**.

### Filtering
Use a **Low-Pass Filter** to recover the original message.

## Overall Conclusion
DSSS enhances **security and interference immunity**. Without the correct PN sequence, the signal appears as **random noise**.

</details>

---

<details>
<summary>Experiment 20: Understanding Software Defined Radio (SDR)</summary>

## Introduction
Software Defined Radio (**SDR**) moves radio signal processing from hardware circuits into **software algorithms**. This allows one hardware device to support multiple communication systems simply by changing the software.

## Objectives
- Interface the **ETT-101 hardware with a PC-based SDR system**.  
- Observe **digital signal processing in software**.

## Procedures

### Hardware Interface
Connect the **ETT-101 output** to a PC sound card or SDR interface.

### Software Configuration
Use software such as **GNU Radio** to configure demodulator blocks.

### Analysis
Generate a signal using the ETT-101 and analyze it using **FFT spectrum visualization** and software demodulation.

## Overall Conclusion
SDR demonstrates the evolution of communication systems from **fixed hardware implementations to flexible software-based radio platforms**, enabling advanced signal processing and reconfigurable communications.

</details>
