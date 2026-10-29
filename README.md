# 🏠 Smart Home Automation System Using ESP32

An IoT-based smart home prototype using an **ESP32**, **PIR motion sensor**, **DHT11 temperature and humidity sensor**, and **two LEDs**. The system detects movement, monitors room temperature and humidity, and uses LEDs to demonstrate automated home responses.

🔗 Project Link:https://mokxi.com/p/6tqXDmpP2F2wnm3W?utm_source=share&utm_medium=link&ref=_qdiKxHlpajCU2W2

## ✨ Features

- **Motion detection:** Detects movement using a PIR sensor.
- **Automatic light:** Turns LED 1 on when motion is detected.
- **Motion indicator:** LED 2 indicates the detected-motion state.
- **Environment monitoring:** Reads temperature and humidity using the DHT11.
- **Serial monitoring:** Displays sensor readings and motion status in the Arduino IDE Serial Monitor.
- **Low-cost prototype:** Demonstrates basic smart-home automation without switching mains-voltage appliances.

## 🧰 Components Required

| Component | Quantity |
|---|---:|
| ESP32 development board | 1 |
| PIR motion sensor (e.g., HC-SR501) | 1 |
| DHT11 temperature and humidity sensor/module | 1 |
| LEDs | 2 |
| Current-limiting resistors (typically 220–330 Ω) | 2 |
| Breadboard | 1 |
| Jumper wires | As needed |
| USB cable / suitable power source | 1 |

## 🔌 Example Pin Connections

The following is an example pin mapping. Change the GPIO numbers in your sketch if your circuit uses different pins.

| Component pin | ESP32 connection |
|---|---|
| DHT11 VCC | 3V3 (check your module specifications) |
| DHT11 GND | GND |
| DHT11 DATA | GPIO 4 |
| PIR VCC | Supply required by your PIR module (often 5V; check its specifications) |
| PIR GND | GND |
| PIR OUT | GPIO 27 |
| LED 1 anode (+) through a resistor | GPIO 18 |
| LED 1 cathode (−) | GND |
| LED 2 anode (+) through a resistor | GPIO 19 |
| LED 2 cathode (−) | GND |

**Important:** ESP32 GPIO pins are 3.3 V logic and are not 5 V tolerant. Verify that the PIR module's OUT signal does not exceed 3.3 V before connecting it to an ESP32 input. Connect all grounds together. Never connect an LED directly to a GPIO without a current-limiting resistor.

## ⚙️ How It Works

1. The ESP32 starts the PIR sensor and DHT11 sensor.
2. The PIR sensor detects movement in its field of view.
3. When motion is detected, the ESP32 turns on the two indicator LEDs.
4. When the PIR output returns to LOW, the LEDs turn off (subject to the PIR module's hold-time setting).
5. The DHT11 periodically measures room temperature and relative humidity.
6. Motion status and sensor readings are printed to the Serial Monitor.

> In this basic version, the LEDs demonstrate automation locally. Wi-Fi, a mobile app, and cloud monitoring are not included unless implemented separately.

## 💻 Software Requirements

- [Arduino IDE](https://www.arduino.cc/en/software)
- ESP32 board support installed in Arduino IDE
- DHT sensor library (for example, the Adafruit DHT Sensor Library)
- Adafruit Unified Sensor library, if required by the installed DHT library

## 🚀 Setup and Run

1. Install Arduino IDE.
2. Add ESP32 board support and select the correct ESP32 board and port.
3. Install the required DHT sensor libraries through **Tools → Manage Libraries**.
4. Connect the components according to the pin table.
5. Open the project's `.ino` sketch.
6. Confirm that the GPIO constants in the code match your wiring.
7. Upload the code to the ESP32.
8. Open **Tools → Serial Monitor** and set the baud rate to the value used in the sketch (commonly `115200`).
9. Move in front of the PIR sensor and observe the LEDs and Serial Monitor output.

## 🧪 Expected Results

| Condition | Expected behavior |
|---|---|
| Motion detected | LED 1 and LED 2 turn ON |
| No motion detected | LEDs turn OFF after the PIR output goes LOW |
| DHT11 reading succeeds | Temperature and humidity appear in the Serial Monitor |
| DHT11 reading fails | Check the DATA connection, power, library, and sensor type |

Actual PIR response time and LED hold time depend on the sensor module's settings. DHT11 readings are relatively slow and intended for basic environmental monitoring.

## 📁 Suggested Project Structure

```text
Smart-Home-Automation/
├── README.md
├── smart_home_automation.ino
└── circuit_diagram.png
```

Add your Arduino sketch and a circuit diagram or project photos to the repository when available.

## 🔮 Future Improvements

- Add Wi-Fi-based monitoring through a web dashboard or mobile app.
- Send motion alerts to a phone.
- Add a relay module to control a suitable low-voltage load.
- Store temperature and humidity readings for later analysis.
- Add a light sensor to switch the light on only when the room is dark.

## 🔒 Safety Notes

- Use LEDs for demonstration before connecting any real appliance.
- Do not connect household AC mains directly to the ESP32 or a breadboard.
- Use a properly rated, isolated relay module and safe enclosure if appliance control is added.
- Verify each module's voltage requirements before powering it.

## 📚 Learning Outcomes

This project demonstrates ESP32 GPIO input/output, sensor interfacing, conditional logic, basic automation, and serial debugging.
