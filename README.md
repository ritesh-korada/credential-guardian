# Credential Guardian 🔐
> An air-gapped hardware password vault built on ESP32

![Version](https://img.shields.io/badge/version-2.0-green)
![Platform](https://img.shields.io/badge/platform-ESP32-blue)
![Status](https://img.shields.io/badge/status-active-brightgreen)

---

## 🎯 What is this?

A standalone hardware security device that stores your passwords 
**offline and encrypted** — completely away from your computer.

Unlike browser password managers, Credential Guardian:
- Never connects to the internet
- Never shows passwords on your computer screen
- Requires physical PIN entry to unlock
- Stores everything encrypted in hardware memory

---

## 🔐 Security Layers
```
Layer 1 → Physical device    (must have ESP32)
Layer 2 → PIN authentication  (must know PIN)
Layer 3 → XOR encryption     (data unreadable in EEPROM)
Layer 4 → LCD only display   (no screenshot possible)
Layer 5 → Air gap            (zero internet connection)
```

---

## ⚡ Version History

| Version | What changed |
|---|---|
| V1.0 | Serial Monitor input — basic proof of concept |
| V2.0 | 4x4 Keypad input — zero PC dependency (current) |
| V3.0 | PS2 keyboard + AES-128 encryption (planned) |

---

## 🛠️ Hardware

| Component | Purpose |
|---|---|
| ESP32 DevKit V1 | Main microcontroller |
| LCD 16x2 I2C | Display output only |
| 4x4 Matrix Keypad | Secure input — no PC needed |
| Passive Buzzer | Audio feedback |

**Total cost: ~₹700**

---

## 📋 How It Works

**First Boot (one time only):**
```
Power on → Set username via keypad
         → Set PIN via keypad
         → Ready forever
```

**Saving a password:**
```
Press 2 (Insert) → Enter slot number
→ Type password → Press # to confirm
→ Encrypted + stored in EEPROM instantly
```

**Viewing a password:**
```
Press 1 (View) → Enter PIN via keypad
→ Select slot → Password shown on LCD only
→ Auto locks after 5 seconds
```

---

## 🎮 Keypad Controls

# 🔐 Credential Guardian – Keypad Usage Guide

## 📱 Input System Overview

The device uses a **4×4 matrix keypad with multi-tap input**, similar to old mobile phones.
It supports:

* Alphabet input (lowercase & uppercase)
* Numeric input
* Special characters
* Secure PIN entry

---

## 🎮 Keypad Layout

```
1  2  3  A
4  5  6  B
7  8  9  C
*  0  #  D
```

---

## 🔤 Input Modes

### 1. Text Mode (Default)

* Used for entering usernames and passwords
* Keys 2–9 generate alphabets using multi-tap

| Key | Characters |
| --- | ---------- |
| 2   | a b c      |
| 3   | d e f      |
| 4   | g h i      |
| 5   | j k l      |
| 6   | m n o      |
| 7   | p q r s    |
| 8   | t u v      |
| 9   | w x y z    |
| 0   | space      |

👉 Press the same key repeatedly to cycle letters.

---

### 2. Uppercase Mode

* Press **D** to toggle uppercase

| Display | Meaning   |
| ------- | --------- |
| a       | lowercase |
| A       | uppercase |

Example:

* Press `D` → uppercase ON
* `2` → A
* `22` → B

---

### 3. Number Mode

* Press **C** to toggle number mode

| Display | Meaning     |
| ------- | ----------- |
| T       | text mode   |
| N       | number mode |

In number mode:

* Keys 0–9 directly input digits

Example:

```
Press C → N
2 → 2
3 → 3
```

---

### 4. Special Characters

| Key | Characters    |
| --- | ------------- |
| 1   | 1 → @ → . → _ |
| A   | # → $ → %     |
| B   | ! → ?         |

👉 Press repeatedly to cycle symbols.

---

## 🔑 Control Keys

| Key | Function           |
| --- | ------------------ |
| #   | Confirm / Enter    |
| *   | Backspace          |
| C   | Toggle number mode |
| D   | Toggle uppercase   |
| A/B | Special characters |

---

## ✍️ Example Usage

### Example 1: Enter "ritesh"

```
777 → r
444 → i
8   → t
33  → e
7777 → s
44  → h
Press # to confirm
```

---

### Example 2: Enter "Ritesh@65"

```
Press D → uppercase
777 → R

Press D → lowercase
444 → i
8 → t
33 → e
7777 → s
44 → h

Press 1 → @

Press C → number mode
6 → 6
5 → 5

Press # to confirm
```

---

## ⚠️ Important Notes

* Press keys quickly to cycle characters
* Wait ~1 second to confirm a character before typing next
* Use `*` to correct mistakes
* Use `#` only after completing input

---

## 🎯 Summary

The keypad system provides:

* Secure offline input
* Full text + numeric + symbol support
* Efficient operation using minimal hardware
---

## 🔒 Why safer than browser passwords?

| Attack | Browser | Credential Guardian |
|---|---|---|
| Keylogger | ❌ Captures password | ✅ PIN on physical keypad |
| Screenshot malware | ❌ Captures autofill | ✅ Only shown on LCD |
| Remote hacker | ❌ Can access Chrome | ✅ Must physically have device |
| Data breach | ❌ Server can be hacked | ✅ Never sent to any server |
| Someone uses your laptop | ❌ Sees all passwords | ✅ Needs device + PIN |

---

## ⚠️ Known Limitations & Roadmap

| Current Limitation | Planned Fix | Version |
|---|---|---|
| XOR cipher (demo only) | AES-128 encryption | V3.0 |
| Keypad limited to numbers | PS2 keyboard full typing | V3.0 |
| No backup system | Encrypted export feature | V4.0 |
| Single master PIN | Multi-user support | V4.0 |
| Wokwi EEPROM resets on stop | Real hardware persistent | Hardware |

> Note: EEPROM data persists on real ESP32 hardware.
> Wokwi simulation resets on stop — this is a simulator
> limitation, not a code bug.

---

## 🖥️ Simulation

▶️ [Run on Wokwi] https://wokwi.com/projects/459670045014649857

---

## 📁 Project Structure
```
credential-guardian/
├── src/
│   └── main.cpp        ← ESP32 firmware
├── diagram.json        ← Wokwi circuit
├── wokwi.toml          ← Wokwi config
└── README.md           ← This file
```

---

## 🧠 Concepts Demonstrated

- Air-gapped security architecture
- Hardware authentication
- XOR cipher encryption
- EEPROM non-volatile storage
- IoT security design
- Threat modeling
- Anti keylogger design

---

## 👨‍💻 Built By

**Ritesh Korada**
BE CSE Cybersecurity — Semester 2
Chandigarh University

> *"Built in Sem 2 as part of my AppSec learning journey 
>  towards FAANG security engineering"*

---

## 📜 Disclaimer

This is a proof-of-concept for educational purposes.
Not recommended for production use in current form.
