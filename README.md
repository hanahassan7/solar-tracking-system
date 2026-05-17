# ☀️ Solar Tracking System — CSE271s
### Ain Shams University · Faculty of Engineering · Spring 2026

![Analog](https://img.shields.io/badge/Analog-Electronics-orange?style=flat)
![PWM](https://img.shields.io/badge/PWM-555Timer-yellow?style=flat)
![HBridge](https://img.shields.io/badge/H--Bridge-Motor--Control-blue?style=flat)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat)

> Course: **CSE271s — System Dynamics and Control Components**
> Team: **Team 31** · 10 Members

---

## 📌 Project Overview

A fully analog solar tracking system that automatically adjusts the position of a solar panel toward the sun to maximize energy efficiency. The system uses two LDR sensors to detect light intensity from different directions and drives a DC motor to rotate the panel toward the stronger light source.

A hysteresis control layer prevents unnecessary motor movement when the light difference is within a set threshold, reducing mechanical wear and optimizing power consumption.

---

## 🔁 System Pipeline

```
LDR 1 ──→ Difference Amplifier 1 ──→ Hysteresis 1 ──→ H-Bridge ──→ MOTOR
                                  ↘
LDR 2 ──→ Difference Amplifier 2 ──→ Summing Amplifier ──→ PWM (555 Timer)
                                  ↘
                                   Hysteresis 2 ──→ H-Bridge
```

---

## ⚙️ System Components

### Part A — Signal Conditioning
→ **2x LDR Sensors** — detect light intensity from opposite directions
→ **2x Difference Amplifiers** — calculate directional light gradient independently
→ **2x Hysteresis Comparators** — establish a 0.9V dead band to eliminate motor jitter
→ **Summing Amplifier** — consolidates both error signals into a unified control voltage

### Part B — Control Stage
→ **555 Timer (Astable Mode)** — generates a fixed-frequency 10kHz square wave trigger
→ **555 Timer (Monostable Mode)** — generates variable-width pulses based on the summing amplifier output
→ **PWM Output** — motor speed is directly proportional to the light intensity mismatch

### Part C — H-Bridge & DC Motor
→ **H-Bridge (L298N)** — determines motor rotation direction based on hysteresis outputs
→ **DC Motor** — physically rotates the solar panel toward the stronger light source

---

## 🔢 Key Calculations

| Parameter | Value |
|---|---|
| PWM Frequency | ~10.41 kHz |
| Hysteresis Window | 0.9V |
| Vref | 3.4V |
| Difference Amplifier Gain | 2 |
| Astable Timer (TH) | 96.76 μs |
| Astable Timer (TL) | 3.26 μs |

---

## ⚡ Challenges & Solutions

**Challenge 1 — Dual-rail power supply complexity**
Initial design used a precision rectifier requiring ±Vcc. Solved by switching to two unipolar difference amplifiers, eliminating the need for a negative supply.

**Challenge 2 — Motor jitter from ambient noise**
Solved by implementing hysteresis comparators with a 0.9V dead band, keeping the motor idle until a substantial solar shift is detected.

**Challenge 3 — Simulation vs. real-world discrepancies**
Inductive feedback from the motor caused timer circuit issues not captured in simulation. Solved through iterative manual tuning of PWM frequency and careful component characterization.

---

## 📄 Full Report

[📄 View Full Report](./Solar-Tracking-System-Report.pdf)

---



## 📫 Contact

**Hana Hassan Hamed**
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/hana-hassan-hamed/)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:hanahassan2006@gmail.com)
