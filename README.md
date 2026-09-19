# GNU Radio – FM Communication & SDR Experiments

This repository contains a collection of **GNU Radio Companion (GRC)** experiments focused on **FM transmission, FM reception, SDR-based signal analysis, and USRP/RTL-SDR integration**. The experiments progress from generating and transmitting FM signals using audio sources to receiving real RF signals using an RTL-SDR and analyzing them in the time and frequency domains.

---

## 🛠️ Setup

These experiments were developed using **GNU Radio** with SDR hardware such as **USRP** and **RTL-SDR**.

For the Radioconda-based GNU Radio installation and SDR driver setup, refer to:

**[📄 Radioconda Installation Guide](./radioconda-installation-guide.pdf)**

The setup guide covers:

- Radioconda installation on Windows
- GNU Radio setup
- UHD installation
- USRP device configuration
- Zadig / WinUSB driver installation
- RTL-SDR Blog V4 configuration
- USRP device verification
- RTL-SDR verification

### Hardware

- Ettus USRP
- RTL-SDR
- Antenna
- Computer running GNU Radio

---

# 📡 Experiments

## 1. FM Audio Transmitter — `fm_audio_transmit.grc`

This experiment implements an **FM audio transmitter using a USRP**. An audio signal is obtained from the system audio source, filtered using a band-pass filter, scaled and combined with a signal source before being resampled and passed to a Wideband FM transmitter block. The resulting complex FM signal is visualized using frequency and waterfall displays and transmitted through a **UHD USRP sink**. The flowgraph uses a configurable tuning frequency, RF gain, sample rate, and audio volume, with the current configuration using a **2.4 MS/s sample rate and 435 MHz tuning frequency**.

---

## 2. FM Transmitter Using WAV File — `FM_Transmitter_Wavfile.grc`

This experiment demonstrates **FM transmission of a prerecorded WAV audio file**. The WAV file is read using a file source and passed through a rational resampler before being processed by a Wideband FM transmitter. The generated FM signal is simultaneously visualized using frequency and waterfall displays and sent to a **USRP through the UHD USRP Sink** for RF transmission. The flowgraph provides configurable parameters for transmission frequency, RF gain, sample rate, and audio level, with the configured transmission frequency set to **65 MHz**.

---

## 3. FM Stereo Receiver — `FM_sterio_Reciever_exp.grc`

This experiment implements an **FM stereo receiver using an RTL-SDR**. The RTL-SDR captures an RF signal at a tunable frequency and passes it through a low-pass filter and rational resampler before FM stereo demodulation. A PLL-based FM receiver block separates the stereo audio channels, which are independently scaled and sent to the two channels of an audio sink. Time-domain, frequency-domain, and waterfall displays are also used to observe the received RF signal. The flowgraph is configured with an RTL-SDR sample rate of approximately **2 MS/s** and a default tuning frequency of **435 MHz**.

---

## 4. RTL-SDR FM Spectrum Analyzer — `RTLFMSPECTRUMANALYSER.grc`

This experiment uses an **RTL-SDR as a real-time RF spectrum analyzer and FM receiver**. The received complex RF samples are processed through a throttle block and displayed using time-domain, frequency-domain, waterfall, and constellation visualizations. An FM demodulator is also included to recover audio from an FM signal, with the recovered audio scaled and sent to the system audio output. The center frequency, bandwidth, RF gain, and audio volume can be adjusted through GUI controls, making the flowgraph useful for exploring FM signals across different RF frequencies.

---

## 5. RTL-SDR Radio Capture — `Radiocapture.grc`

This experiment extends the RTL-SDR-based FM receiver by providing a configurable **radio signal capture and monitoring flowgraph**. RF samples from the RTL-SDR are routed through a selector and throttle stage before being analyzed using time-domain, frequency-domain, waterfall, and constellation displays. The signal can also be passed through an FM demodulator and sent to an audio sink, allowing an FM broadcast signal to be both visualized and listened to. The flowgraph provides adjustable center frequency, bandwidth, RF gain, and audio volume controls for interactive SDR experimentation.

---
