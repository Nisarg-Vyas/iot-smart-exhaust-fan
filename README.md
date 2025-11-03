# 🌬️ IoT Smart Exhaust Fan (Semester 1 Project)

## 📘 Overview
This project is an **IoT-enabled Smart Exhaust Fan** built using **ESP32**, **DHT11**, and **MQ135** sensors.  
It monitors temperature, humidity, and air quality in real time and automatically turns the exhaust fan **ON** when any reading exceeds a defined threshold.  
Additionally, the fan can also be **manually controlled** via the **Blynk IoT Dashboard**.

> 🕒 Originally built in **Semester 1 (2023)** and documented in **Semester 3 (2025)**.

This was my **first IoT project**, and it truly **sparked the fire in me** — the excitement of seeing code and hardware come together motivated me to build more and more projects in the fields of IoT, automation, and robotics.

---

## 🎯 Features
- Real-time temperature, humidity, and air quality monitoring  
- Automatic fan control when thresholds are exceeded  
- Manual control of the fan using the Blynk IoT app  
- Real-time dashboard display for all sensor data  
- Wi-Fi-enabled system based on ESP32  

---

## 🧰 Components Used
| Component | Quantity | Description |
|------------|-----------|-------------|
| ESP32 Dev Module | 1 | Wi-Fi-enabled microcontroller |
| DHT11 Sensor | 1 | Measures temperature and humidity |
| MQ135 Sensor | 1 | Detects air quality and gas concentration |
| Relay Module | 1 | Controls the fan ON/OFF mechanism |
| Fan (5V or 12V) | 1 | Exhaust fan controlled via relay |
| Power Supply | 1 | Provides required DC voltage |
| Blynk IoT App | - | Used for monitoring and control |

---

## ⚙️ Circuit Diagram
*(Attach your circuit diagram or a simple hand-drawn image here)*  
![Circuit Diagram](images/circuit_diagram.jpg)

---

## 💻 Working Principle
1. **Data Collection:** The DHT11 and MQ135 sensors continuously measure temperature, humidity, and gas quality.  
2. **Decision Making:** If any parameter exceeds its threshold, the ESP32 activates the relay to turn the fan ON automatically.  
3. **Dashboard Visualization:** The Blynk IoT Dashboard displays live sensor readings.  
4. **Manual Control:** Users can manually switch the fan ON or OFF using the Blynk app, overriding the automatic control.

---

## 📱 Blynk IoT Dashboard
*(Attach screenshots of your Blynk dashboard here)*  
![Blynk Dashboard](images/blynk_dashboard.png)

---

## 🧩 Code
Your Arduino code goes in `code/smart_exhaust_fan.ino`.

### Example Code Snippet:
```cpp
#include <WiFi.h>
#include <BlynkSimpleEsp32.h>
#include "DHT.h"

#define DHTPIN 4
#define DHTTYPE DHT11
#define MQ135_PIN 34
#define RELAY_PIN 5

char auth[] = "Your_Blynk_Auth_Token";
char ssid[] = "Your_WiFi_SSID";
char pass[] = "Your_WiFi_Password";

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(115200);
  Blynk.begin(auth, ssid, pass);
  dht.begin();
  pinMode(RELAY_PIN, OUTPUT);
}

void loop() {
  Blynk.run();
  
  float temp = dht.readTemperature();
  float hum = dht.readHumidity();
  int gas = analogRead(MQ135_PIN);

  Blynk.virtualWrite(V0, temp);
  Blynk.virtualWrite(V1, hum);
  Blynk.virtualWrite(V2, gas);

  if (temp > 35 || hum > 70 || gas > 400) {
    digitalWrite(RELAY_PIN, HIGH);
    Blynk.virtualWrite(V3, 1);
  } else {
    digitalWrite(RELAY_PIN, LOW);
    Blynk.virtualWrite(V3, 0);
  }

  delay(2000);
}
