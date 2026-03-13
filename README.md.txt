# Credential Guardian 🔐

An air-gapped hardware password vault built on ESP32.

## Features
- XOR encryption for password storage
- Morse code pattern authentication
- 10 password slots in EEPROM
- Offline LCD display — anti keylogger
- Physical button authentication
- Anti screenshot — passwords only on LCD

## Hardware Used
- ESP32 DevKit V1
- LCD 16x2 I2C (SSD1306)
- 3 Push buttons (DOT / DASH / CONFIRM)
- Passive Buzzer

## How It Works
1. First boot asks you to set username and secret pattern
2. Passwords saved via Serial Monitor — encrypted immediately
3. To view — enter physical morse pattern on buttons
4. Password shown ONLY on LCD for 5 seconds then locks

## Security Concept
Passwords never stored in plain text.
Only revealed on physical LCD — not on computer screen.
Pattern authentication required for view and delete.

## Simulation
Run on Wokwi: [Click Here](YOUR-WOKWI-LINK)

## Built By
Your Name — BE CSE Cybersecurity, Sem 2
```
5. Save it

---

**Final folder should look like this:**
```
credential-guardian/
│
├── src/
│   └── main.cpp
│
├── diagram.json
├── wokwi.toml
└── README.md