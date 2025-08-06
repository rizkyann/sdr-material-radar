# sdr-material-radar
An FMCW radar system using HackRF One and GNU Radio to differentiate materials (aluminum, wall, styrofoam) based on the amplitude of the reflected signal.

# FMCW Radar for Material Characterization using SDR

**(PERANCANGAN SISTEM DETEKSI SINYAL PANTUL RADAR PADA FREKUENSI 4300 MHZ BERDASARKAN AMPLITUDO DENGAN BERBAGAI JENIS BAHAN)**

A Final Project by Rizky Akbar Nugraha (211344026) from Politeknik Negeri Bandung.

---

## 📖 Overview

This project presents the design and implementation of a Frequency Modulated Continuous Wave (FMCW) radar system built on a Software Defined Radio (SDR) platform. [cite_start]The system operates at **4300 MHz** with a **10 MHz** sweep bandwidth[cite: 115, 204, 205].

[cite_start]Unlike conventional FMCW radars that focus on estimating distance or velocity, this research focuses on analyzing the **amplitude (relative power)** of the *beat frequency* signal[cite: 116]. [cite_start]The primary goal is to demonstrate that this amplitude analysis can be used for the basic differentiation of various materials[cite: 122].

[cite_start]The entire system was implemented using two **HackRF One** units for transmitting and receiving, with all signal generation, acquisition, and processing controlled by **GNU Radio Companion**[cite: 117]. [cite_start]Testing was performed in an outdoor environment using an aluminum plate, a wall, and styrofoam as targets at distances ranging from 30 cm to 200 cm[cite: 118, 129].

---

## ✨ Key Features

* [cite_start]**FMCW Radar Implementation**: A fully functional FMCW radar system operating at 4.3 GHz[cite: 808].
* [cite_start]**Material Differentiation**: Demonstrates a clear correlation between the target material and the amplitude of the reflected beat frequency signal[cite: 119, 811].
* [cite_start]**SDR-Based**: Built entirely with affordable and flexible SDR hardware (HackRF One) and open-source software (GNU Radio)[cite: 117].
* [cite_start]**Real-Time Analysis**: Provides real-time spectrum visualization of the beat frequency signal for direct analysis[cite: 587, 589].

---

## 🛠️ System Architecture

[cite_start]The system uses a bistatic radar configuration, where one HackRF One acts as the transmitter (TX) and a second one acts as the receiver (RX)[cite: 224, 358]. [cite_start]The process is controlled entirely within a single GNU Radio flowgraph[cite: 558].

[cite_start]*Diagram Blok Sistem Radar FMCW [cite: 357]*

**Workflow:**
1.  [cite_start]**Signal Generation (TX Path)**: GNU Radio generates a digital FMCW *chirp* signal[cite: 359].
2.  [cite_start]**Transmission**: The signal is sent to the first HackRF One (TX), which converts it to an analog RF signal at 4300 MHz and transmits it via an antenna[cite: 361, 362].
3.  [cite_start]**Reflection**: The RF signal hits a target object and is reflected[cite: 363].
4.  [cite_start]**Reception (RX Path)**: The reflected signal is captured by the second HackRF One's (RX) antenna[cite: 364].
5.  **Beat Frequency Generation**: In GNU Radio, the received signal is digitally mixed with a copy of the transmitted signal. [cite_start]This mixing process produces the low-frequency **beat signal**[cite: 367].
6.  [cite_start]**Amplitude Analysis**: The spectrum of the beat signal is analyzed using an FFT, and the amplitude of the resulting peak is measured to characterize the target's material[cite: 368].

---

## ⚙️ Requirements

### Hardware
* [cite_start]**2 x HackRF One SDRs**: One for the transmitter (`hackrf=0`) and one for the receiver (`hackrf=1`)[cite: 224, 580].
* [cite_start]**2 x Antennas**: Commercial antennas suitable for operation at 4300 MHz[cite: 233].
* **Computer**: A PC or laptop capable of running GNU Radio Companion.

### Software
* [cite_start]**GNU Radio**: Developed and tested with GNU Radio Companion v3.10.10.0[cite: 926].
* **`gr-osmosdr` Driver**: The Osmocom SDR source/sink blocks are required for HackRF One support.
* [cite_start]**Python**: The execution environment for GNU Radio flowgraphs[cite: 926].

---

## 🚀 How to Run

1.  **Hardware Setup**:
    * Connect the two HackRF One devices to your computer via USB.
    * Attach an antenna to the TX port of the first HackRF One and to the RX port of the second.
    * [cite_start]Position the antennas in a bistatic configuration, pointing towards the target area, to minimize direct crosstalk[cite: 598].

2.  **Software Execution**:
    * Clone this repository:
        ```bash
        git clone [https://github.com/rizkyann/sdr-material-radar.git](https://github.com/rizkyann/sdr-material-radar.git)
        cd sdr-material-radar
        ```
    * Open the `untitled.grc` file in GNU Radio Companion.
    * Ensure your HackRFs are correctly identified. [cite_start]The flowgraph is configured for the transmitter as `hackrf=0` and the receiver as `hackrf=1` in the Osmocom blocks[cite: 580].
    * Click the **"Generate the flowgraph"** button, followed by the **"Execute the flowgraph"** button.
    * The QT GUI Frequency Sink window will appear, showing the real-time spectrum of the beat frequency signal.

---

## 📊 Results

[cite_start]The project successfully demonstrated that different materials produce distinct beat signal amplitudes[cite: 811].

[cite_start]At a fixed distance of 30 cm, the measured amplitudes were[cite: 652]:
* **Plat Aluminium**: **-31,28 dB**
* **Tembok (Wall)**: **-35,55 dB**
* **Styrofoam**: **-42,85 dB**

[cite_start]This confirms the hypothesis that conductive materials (like aluminum) reflect the signal most strongly, followed by standard dielectrics (wall), and low-permittivity dielectrics (styrofoam)[cite: 746].

[cite_start]The results also consistently showed that for all materials, the signal amplitude decreases as the distance to the target increases, which aligns with the fundamental principles of radar propagation[cite: 749, 799].

[cite_start]*Grafik Perbandingan Amplitudo Sinyal vs Jarak untuk Berbagai Material [cite: 699]*

---

## 📜 Citation

If you use this work in your research, please cite the original thesis:

> Nugraha, R. A. (2025). *Perancangan Sistem Deteksi Sinyal Pantul Radar pada Frekuensi 4300 MHz Berdasarkan Amplitudo dengan Berbagai Jenis Objek* [Final Project Report]. Politeknik Negeri Bandung.

---

## ⚖️ License

This project is licensed under the **MIT License**. See the `LICENSE` file for details.
