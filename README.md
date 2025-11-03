
# 💡 ESP8266-Based IoT Notice Board

A **Wi-Fi-enabled digital notice board** that displays real-time scrolling messages on an LED matrix, powered by the **ESP8266** microcontroller.  
This project offers a smart, dynamic, and remotely updatable alternative to traditional notice boards — ideal for schools, offices, or smart homes.

---

## 🚀 Project Overview

This project implements a **dynamic IoT Notice Board** using an ESP8266 Wi-Fi module and an LED matrix display.  
The device connects to the internet to retrieve **real-time scrolling messages** from an online API.  
If the internet connection is lost, the board automatically **switches to a backup message**, ensuring continuous operation.

It’s designed to be robust, efficient, and modular — with clear separation between Wi-Fi, API, and display logic.

---

## ✨ Key Features

- **Remote Updates:** Fetches scrolling messages via an online HTTP API.  
- **Wi-Fi Connectivity:** Uses ESP8266 for reliable wireless communication.  
- **Offline Mode:** Displays preconfigured messages when Wi-Fi is unavailable.  
- **Smooth Display:** Flicker-free, continuous scrolling text on LED matrix.  
- **Modular Architecture:** Separate code modules for Wi-Fi, API, and display.

---

## 🛠️ Hardware & Components

| Component | Description |
|------------|-------------|
| **Microcontroller** | ESP8266-based board (NodeMCU / Wemos D1 Mini) |
| **Display** | MAX7219-based 8x8 LED Matrix (cascaded modules) |
| **Power Supply** | Stable 5V DC (essential for LED stability) |
| **Wiring** | Jumper wires via SPI connection |

### 🔌 Wiring Instructions

| MAX7219 Pin | ESP8266 Pin (NodeMCU Example) | Description |
|--------------|-------------------------------|-------------|
| VCC | 5V | Power Supply |
| GND | GND | Ground |
| DIN | D7 (GPIO 13) | Data In (MOSI) |
| CS | D8 (GPIO 15) | Chip Select (SS) |
| CLK | D5 (GPIO 14) | Clock (SCK) |

---

## 💻 Software Setup

### 🔧 Requirements

- [Arduino IDE](https://www.arduino.cc/en/software) or [PlatformIO IDE](https://platformio.org/)  
- ESP8266 board package installed  
- Required libraries:

| Library | Type | Description |
|----------|------|-------------|
| `ESP8266WiFi` | Built-in | Manages Wi-Fi connectivity |
| `ESP8266HTTPClient` | Built-in | Handles HTTP requests |
| `Max72xxPanel` | External | Controls LED matrix display |
| `ArduinoJson` | External | Parses API JSON responses |

---

## ⚙️ Configuration

Before uploading, open `main.cpp` (or `APIManager.h`) and set your Wi-Fi and API details:

```cpp
#define WIFI_SSID       "YourWiFiName"
#define WIFI_PASSWORD   "YourWiFiPassword"
#define API_ENDPOINT    "https://your.api.endpoint/message"

#define NUM_MATRICES    4     // Number of cascaded LED modules
#define SCROLL_SPEED    50    // Lower = faster scroll
#define BRIGHTNESS      5     // LED brightness (0–15)
````

---

## 📂 Repository Structure

```
.
├── README.md               <-- This documentation file
├── LICENSE                 <-- License information
├── .gitignore              <-- Ignore build files
├── platformio.ini          <-- PlatformIO project config
├── src/
│   ├── main.cpp            <-- Main program (setup & loop)
│   ├── WiFiManager.h       <-- Handles Wi-Fi connection
│   ├── APIManager.h        <-- Fetches and parses API data
│   └── DisplayController.h <-- Controls LED matrix display
├── data/
│   └── backup_message.txt  <-- Local message if offline
└── hardware/
    └── BOM.md              <-- Bill of Materials
```

---

## 🔍 How It Works

1. The ESP8266 connects to the Wi-Fi network on startup.
2. It sends a GET request to the specified API endpoint.
3. The API returns a JSON message (e.g., `{ "message": "Welcome to IoT Notice Board!" }`).
4. The message is parsed and displayed as scrolling text on the LED matrix.
5. If the network or API fails, a local backup message is displayed instead.

---

## 🧠 Example API Response

```json
{
  "message": "Welcome to the IoT Notice Board!"
}
```

---

## 🐛 Known Issues & Solutions

| Issue                    | Cause                              | Solution                                      |
| ------------------------ | ---------------------------------- | --------------------------------------------- |
| Unreliable API responses | Network timeouts or invalid data   | Added error handling and local fallback       |
| HTTP client leaks        | Missing `http.end()` in loop       | Fixed by closing client after each request    |
| Text flickering          | Incorrect delay in scroll function | Adjusted timing and spacing for smooth scroll |

---

## 🧩 Future Improvements

* Web dashboard for easy message updates
* Multiple message rotation or scheduling
* Real-time clock integration for time/date display
* MQTT protocol support for instant message updates

---

## 📸 Example Output

> LED Matrix Display shows:
> “Welcome to the Smart Notice Board!”
> Smooth scrolling across all modules — even during network loss.

---

## 📜 License

This project is released under the **MIT License**.
You are free to use, modify, and distribute it for educational or commercial purposes.

---

## 👨‍💻 Author

**Developer:** [Ramisa Fariha Mridha]
**Email:** [Ramisa.Mridha@student.oulu.fi}
**Version:** 1.0
**Date:** November 2025

---

⭐ If you found this project helpful, please consider giving it a **star** on GitHub!

