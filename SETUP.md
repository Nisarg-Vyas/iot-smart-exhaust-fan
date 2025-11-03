# 🛠️ Project Setup Guide

Welcome! 👋  
This guide will walk you through everything you need to **build, configure, and run** this IoT project using **ESP32** and the **Blynk platform**.

---

## ⚙️ 1. Hardware Requirements
You will need the following components:
- ESP32 Dev Module  
- MQ135 Air Quality Sensor  
- DHT11 Temperature & Humidity Sensor  
- 5V DC Fan / LED (for demonstration)  
- Jumper Wires  
- Breadboard  
- USB Cable for ESP32  

---

## 💻 2. Software Requirements and Prequisites
- [Arduino IDE](https://www.arduino.cc/en/software)  
- [Blynk IoT App](https://blynk.io/) (available on Android/iOS)  
- Required Arduino Libraries:
  - `Blynk`
  - `DHT`
  - `WiFi`
- You shall be knowing how to write/use basic codes of Arduino and ESP32 in order to make this project

> You can certainly take help of AI such as ChatGPT if you are struct somewhere, or even contact me, I would be really happy to help. Find my contact from my profile!
> You can install libraries in Arduino IDE by going to  
> **Sketch → Include Library → Manage Libraries → Search and Install**

---

## 🔌 3. Circuit Connections
| Component | ESP32 Pin |
|------------|------------|
| DHT11 VCC  | 3.3V       |
| DHT11 GND  | GND        |
| DHT11 Data | D4         |
| MQ135 AO   | A0         |
| Fan/LED (via transistor or relay) | D5 |

📝 *Double-check your connections before powering on the board.*

---

## ☁️ 4. Blynk App Setup
1. Install **Blynk IoT** from Play Store / App Store **OR** cabn even use Bylnk Web Interface.
2. First Sign-In/Log-In
3. Create a new project — select **ESP32** as the device and **Wi-Fi** as the connection type.  
4. Copy the **Auth Token** from the Blynk app (you’ll need it in your code).  
5. Add the following widgets:
   - **Button** – to turn the fan/LED ON or OFF  
   - **Gauge or Label** – to display temperature  
   - **Value Display** – to show air quality (MQ135)  
6. Assign Virtual Pins as per your code (e.g., V0 for DHT, V1 for MQ135, V2 for fan) **OR** connect the same pins as stated in the code.

---

## 🧠 5. Code Setup
1. Open the `.ino` file from this repository in **Arduino IDE**.  
2. Replace the following lines in the code with your details (as these things will be differnt for all people):
   ```cpp
   #define BLYNK_AUTH_TOKEN "YourAuthToken"
   const char* ssid = "YourWiFiName";
   const char* password = "YourWiFiPassword";
3. Select Tools → Board → ESP32 Dev Module.
4. Connect your ESP32 to your computer via USB.
5. Click Upload.

---

🌐 6. Running the Project
1. Once uploaded, open the Serial Monitor (115200 baud) to see connection logs.
2. When connected, open the Blynk app and start the project.
3. You’ll now see:
   - Live temperature and humidity updates
   - Air quality readings
   - Fan turning ON/OFF automatically or manually

---

🎥 7. Demonstration Video
📺 Watch the full setup and working demo on YouTube:  
https://youtu.be/Vq6aPo1krZI?si=ukcDjkZ7IksO_es_

---

🔗 8. References and Useful Links
- Official Blynk Documentation:   https://docs.blynk.io/en/
- ESP32 Pinout Reference:   https://randomnerdtutorials.com/esp32-pinout-reference-gpios/

---

🧑‍💻 Author:  
Nisarg Vyas  
Made with ❤️ for learning and building cool IoT projects!

---

⚠️ Notes
- Ensure stable Wi-Fi connection for best results.
- Avoid connecting sensors incorrectly — it may damage your ESP32.
- If using a relay for the fan, ensure you use a 5V or 3.3V compatible module.
