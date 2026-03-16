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

| Key | Function |
|---|---|
| 0-9 | Type input |
| # | Confirm / Enter |
| * | Cancel / Back |
| B | Backspace |
| C | Clear all |
| 1/2/3 | Menu selection |

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

▶️ [Run on Wokwi] https://wokwi.com/projects/458398359029079041

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