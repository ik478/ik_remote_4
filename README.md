# ik_remote_4
# ESP8266 OLED Menu System with WiFi, NTP, Remote Control & Oscilloscope

This project implements a **multi-function menu-driven interface** on an ESP8266 with an SSD1306 OLED display.  
It supports **WiFi connectivity, NTP time synchronization, remote device control, and an oscilloscope mode** using the built-in ADC.

## ✨ Features
- 📡 **WiFi Connection** — Connects to a predefined SSID and shows IP address.
- ⏱ **NTP Time Sync** — Fetches and displays the current time from an NTP server.
- 📋 **Menu Navigation** — Simple button-controlled UI with nested menus.
- 💻 **Laptop Remote Control** — Scans the local network to find a laptop server and sends control commands via HTTP.
- 💡 **LED Control** — Toggle the built-in LED from the menu.
- 📊 **Oscilloscope Mode** — Displays a live waveform on the OLED, calculates amplitude and frequency.
- 🔋 **Power Management** — Sleep and shutdown modes to save power.
- 💾 **EEPROM Storage** — Stores last known IP octet for quicker reconnection.

## 🛠 Hardware Requirements
- **ESP8266 Board** (e.g., NodeMCU, Wemos D1 mini)
- **0.96" SSD1306 OLED Display** (I²C, 128x64)
- **Two Push Buttons** for navigation
- Breadboard & jumper wires
- Optional: Laptop server running on port `9090` for remote control feature

## 📦 Library Dependencies
Install the following libraries via the Arduino Library Manager:
- `ESP8266WiFi`
- `Wire`
- `Adafruit GFX`
- `Adafruit SSD1306`
- `NTPClient`
- `ESP8266HTTPClient`
- `EEPROM`

## ⚙️ Pin Configuration
| Function          | ESP8266 Pin |
|-------------------|-------------|
| Button Up         | D5 (GPIO14) |
| Button Down       | D6 (GPIO12) |
| ADC Input         | A0          |
| OLED SDA          | D2 (GPIO4)  |
| OLED SCL          | D1 (GPIO5)  |
| Built-in LED      | GPIO2       |

## 📋 Menu Structure
### Main Menu
1. **WiFi** — View connection details
2. **Control** — Access remote control menu
3. **Settings** — *(Not implemented yet)*
4. **About** — Project info & MAC address
5. **Oscilloscope** — View live waveform
6. **Back** — Return to clock view

### Control Menu
1. Remote (Laptop)
2. LED Toggle
3. Back

### Back Menu (Power Options)
1. Switch Off
2. Sleep
3. Back

## 🚀 Getting Started
1. Clone this repository:
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
````

2. Open the `.ino` file in Arduino IDE.
3. Install required libraries.
4. Update your WiFi SSID and password in:

   ```cpp
   const char* ssid = "YourWiFiName";
   const char* password = "YourWiFiPassword";
   ```
5. Select the correct board and port in Arduino IDE.
6. Upload the code to your ESP8266.

## 📷 Screenshots

*(You can add pictures of your OLED menus and oscilloscope output here)*

## 📡 Remote Control Setup

* Run a simple HTTP server on your laptop listening on port `9090` that responds to `/control?cmd=<command>`.
* Supported commands: `left_arrow`, `right_arrow`.
* The ESP8266 will scan your network to find the server and send commands.

## 📝 Notes

* Oscilloscope mode is limited by the ADC sampling rate of the ESP8266.
* Power management features use `ESP.deepSleep()` — your wiring must allow wake-up if you want to resume.

## 📄 License

This project is licensed under the MIT License.

---

💡 *Made by ik for ESP8266 & embedded projects.*

```

If you want, I can also prepare a **diagram of the menu system flow** so it looks professional on your GitHub page. That would make your README much more visual.
```
