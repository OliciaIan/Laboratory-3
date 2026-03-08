<details>
<summary>Experiment 15: Amplitude Shift Keying (ASK)</summary>

## Introduction
Amplitude Shift Keying (ASK) is a digital modulation technique where the amplitude of a carrier signal changes according to the digital data. The carrier is switched **on for binary 1** and **off for binary 0** (or between two amplitude levels). ASK allows **Frequency Division Multiplexing (FDM)** but is highly susceptible to noise because the information is carried in the signal amplitude.

## Objectives
- Generate an ASK signal using a switching method.
- Recover the digital data using an envelope detector.
- Restore the digital signal using a comparator.

## Materials Used
- Emona Telecoms-Trainer 101  
- Dual-channel 20MHz oscilloscope  
- Sequence Generator module  
- Dual Analog Switch module  
- Tuneable Low-pass Filter  
- Utilities module (Rectifier)

## Procedures
1. **ASK Generation:** Connect a **2kHz SINE carrier** to the Dual Analog Switch controlled by the Sequence Generator.
2. **Frequency Adjustment:** Replace the 2kHz carrier with a **100kHz carrier from the VCO**.
3. **Demodulation:** Pass the ASK signal through a **Rectifier** then a **Tuneable Low-pass Filter** to detect the envelope.
4. **Restoration:** Connect the filter output to a **Comparator** and adjust the reference voltage to recover the digital pulses.

## Answers to Questions

**Q1:** What is the relationship between the digital signal and the presence of the carrier?  
**Answer:** The carrier appears when the digital signal is **logic-1** and disappears when it is **logic-0**.

**Q2:** What is the ASK signal voltage when the digital signal is logic-0?  
**Answer:** **0V**.

**Q3:** What feature suggests that ASK behaves like an AM signal?  
**Answer:** The **upper and lower envelopes follow the digital data pattern**.

## Overall Conclusion
ASK converts digital data into an analog signal for transmission. Envelope detection recovers the signal, but pulse edges become rounded, requiring a comparator to restore clean digital data.

</details>

---

<details>
<summary>Experiment 16: Binary Phase Shift Keying (BPSK) – Introduction</summary>

## Introduction
Binary Phase Shift Keying (BPSK) is a modulation technique where the **phase of a constant-amplitude carrier shifts by 180°** to represent binary values. Because the amplitude remains constant, BPSK is **much more resistant to noise** than ASK.

## Objectives
- Generate a BPSK signal using a **Balanced Modulator**.
- Observe **180° phase reversals** during digital transitions.

## Materials Used
- Emona Telecoms-Trainer 101  
- Balanced Modulator module  
- Sequence Generator  
- Master Signals module (sine carrier)

## Procedures
1. Connect the **digital data from the Sequence Generator** to the Balanced Modulator.
2. Apply the **sinewave carrier** from the Master Signals module.
3. Observe the **BPSK output** on the oscilloscope.
4. Focus on points where the digital data changes state to observe the **phase reversals**.

## Answers to Questions

**Q1:** How does the carrier change when data switches from 0 to 1?  
**Answer:** The carrier undergoes a **180° phase reversal**.

**Q2:** Why is BPSK more robust than ASK?  
**Answer:** Because **information is encoded in phase instead of amplitude**, making it less sensitive to amplitude noise.

## Overall Conclusion
BPSK provides reliable digital transmission in noisy environments by encoding information in **phase changes** instead of amplitude variations.

</details>

---

<details>
<summary>Experiment 17: Binary Phase Shift Keying (Generation & Recovery)</summary>

## Introduction
BPSK signals use **suppressed carrier modulation (DSBSC)**, meaning the carrier is not directly transmitted. Therefore, **envelope detection cannot be used**. Instead, a **product detector with a synchronized carrier** is required.

## Objectives
- Generate a BPSK signal using a Multiplier module.
- Recover digital data using a product detector.
- Restore the signal using a comparator.

## Materials Used
- Emona Telecoms-Trainer 101  
- Two Multiplier modules  
- Tuneable Low-pass Filter  
- Utilities module (Comparator)

## Procedures
1. **Modulation:** Multiply a **100kHz carrier** with the digital data to generate the BPSK signal.
2. **Demodulation:** Feed the BPSK signal and original carrier into a second **Multiplier**.
3. **Filtering:** Pass the output through a **Tuneable Low-pass Filter**.
4. **Restoration:** Use a **Comparator** to clean up the digital signal.

## Answers to Questions

**Q1:** What happens during logic transitions?  
**Answer:** The carrier **phase reverses by 180°**.

**Q2:** What feature suggests BPSK is DSBSC?  
**Answer:** Alternating halves of the signal envelope resemble the digital message.

**Q3:** Why is the recovered signal imperfect?  
**Answer:** Filtering **rounds the edges of pulses**.

**Q4:** What is used to clean up the recovered signal?  
**Answer:** A **Comparator**.

## Overall Conclusion
BPSK recovery requires **synchronous detection**. Although more complex than ASK, it provides improved noise immunity.

</details>

---

<details>
<summary>Experiment 18: Quadrature Phase Shift Keying (QPSK)</summary>

## Introduction
Quadrature Phase Shift Keying (QPSK) transmits **two bits per symbol** by splitting the data into **I (In-phase)** and **Q (Quadrature)** channels. Each stream modulates orthogonal carriers (sine and cosine), producing two BPSK signals that are combined.

## Objectives
- Generate a QPSK signal from two BPSK signals.
- Understand phase discrimination in demodulation.
- Observe the constant amplitude of QPSK.

## Materials Used
- Emona Telecoms-Trainer 101  
- Dual-channel 20MHz oscilloscope  
- Sequence Generator module  
- Serial-to-Parallel Converter module  
- Phase Shifter module  
- Multiplier modules  
- Adder module

## Procedures
1. **Data Split:** Use the Serial-to-Parallel converter to create **I and Q channels**.
2. **Carrier Setup:** Use **100kHz sine and cosine carriers**.
3. **Modulation:** Generate two BPSK signals using Multiplier modules.
4. **Summing:** Combine them using the **Adder module** to form the QPSK signal.
5. **Demodulation Demo:** Use a Phase Shifter and Multiplier to isolate one BPSK signal.

## Answers to Questions

**Q4:** What type of transmission is present at the Adder output?  
**Answer:** A **Quadrature Phase Shift Keying (QPSK)** signal.

**Q5:** Why is only one sinewave visible even though two BPSK signals exist?  
**Answer:** Because both signals share the **same frequency**, and their sum appears as a single waveform with varying phase.

## Overall Conclusion
QPSK combines two BPSK signals on orthogonal carriers, **doubling bandwidth efficiency** compared to BPSK.

</details>

---

<details>
<summary>Experiment 19: DSSS Modulation & Demodulation</summary>

## Introduction
Direct Sequence Spread Spectrum (DSSS) spreads a signal across a wide bandwidth using a **Pseudo-Noise (PN) sequence**. This provides **jamming resistance and security**, as only receivers with the same PN sequence can decode the signal.

## Objectives
- Understand spread spectrum principles.
- Explore interference resistance and encryption properties.
- Recover a DSSS signal using despreading.

## Materials Used
- Emona Telecoms-Trainer 101  
- Sequence Generator (PN code)  
- Multiplier module  
- Tuneable Low-pass Filter

## Procedures
1. **Spreading:** Multiply the digital message by a **fast PN sequence**.
2. **Despreading:** Multiply the received signal by the **same PN sequence**.
3. **Recovery:** Use a **low-pass filter** to obtain the original message.

## Answers to Questions

**Q1:** Why is DSSS difficult to jam?  
**Answer:** Because the signal is spread across a **wide bandwidth**.

**Q2:** What happens if the receiver uses the wrong PN sequence?  
**Answer:** The signal appears as **noise** and cannot be decoded.

**Q3:** How does DSSS provide encryption?  
**Answer:** Only receivers with the **correct synchronized PN sequence** can recover the message.

## Overall Conclusion
DSSS improves **security, interference resistance, and robustness**, making it widely used in modern wireless systems.

</details>

---

<details>
<summary>Experiment 20: Understanding Software Defined Radio (SDR)</summary>

## Introduction
Software Defined Radio (SDR) replaces traditional hardware radio components with **software implementations** running on computers or embedded systems. This allows flexible signal processing using platforms like **GNU Radio**.

## Objectives
- Learn SDR software and hardware interfaces.
- Explore sampling and resampling in software.
- Demonstrate FM and IQ modulation/demodulation.

## Materials Used
- Emona Telecoms-Trainer 101/C  
- PC with SDR software (GNU Radio or PicoScope)  
- SDR interface device (RTL-SDR)  
- Patch leads and Master Signals module

## Procedures
1. **Familiarization:** Connect ETT-101 hardware to the PC.
2. **Loop-back Test:** Run a software loop-back to confirm communication.
3. **Sampling Study:** Adjust sampling rates and observe aliasing effects.
4. **Hybrid Demo:** Use ETT-101 hardware for modulation and SDR software for demodulation and analysis.

## Answers to Questions

**What is Software Defined Radio?**  
A radio system where signal processing components are implemented using **software instead of dedicated hardware**.

**What is the advantage of SDR?**  
It is **flexible and reconfigurable**, allowing one device to support multiple communication standards.

## Overall Conclusion
SDR demonstrates the transition from fixed hardware radios to **programmable signal processing systems**, enabling rapid development and versatile communication experiments.

</details>
