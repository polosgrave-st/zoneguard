# ZoneGuard: Machine Zone Safety Monitor

Built at **HowdyHack 2026** (Hardware Track), Texas A&M University.

Workers get hurt walking too close to running machines, and most near-misses never get recorded. ZoneGuard watches the area in front of a machine, warns people before they get too close, and logs every near-miss.

## What it does
- **Distance sensing:** an ultrasonic sensor measures how close someone is to the machine
- **Stack light:** green (safe), yellow (warning, under 50 cm), red (danger, under 20 cm)
- **Alarm:** a chirp in the warning zone, fast beeping in the danger zone
- **Barrier arm:** a servo drops a gate arm when someone enters the danger zone
- **OLED screen:** shows the zone, distance, and near-miss count
- **Phone dashboard:** live status and a near-miss log over the device's own Wi-Fi

## Hardware
| Part | Purpose |
|---|---|
| ESP32-S3 dev board | Controller + Wi-Fi |
| HC-SR04 ultrasonic sensor | Distance |
| Red, yellow, green LEDs + 220Ω resistors | Stack light |
| SSD1306 OLED (128x64, I2C) | Display |
| SG90 servo | Barrier arm |
| Audio amplifier + speaker | Alarm |

## Pin map
| ESP32 pin | Connected to |
|---|---|
| 4 | Sensor Trig |
| 5 | Sensor Echo |
| 6 | Servo signal |
| 8 / 9 | OLED SDA / SCL |
| 15 / 16 / 17 | Red / yellow / green LED |
| 18 | Amplifier input (aux) |
| 3V3 / GND | Power rails |

All parts run from the ESP32's 3.3V pin. Connections to the ESP32 use male-to-female jumpers directly on its pins.

## Run it
1. Open `zoneguard.ino` in Arduino IDE (board: ESP32S3 Dev Module, esp32 core 3.x).
2. Install the **Adafruit SSD1306** library (and Adafruit GFX).
3. Upload to the ESP32-S3.
4. On your phone, join Wi-Fi **SafetyMonitor** (password `howdyhack26`) and open **http://192.168.4.1**.

## What's next
- Multiple sensors and one dashboard for a whole warehouse floor
- Shift reports for safety managers
- Automatic machine shutoff
- 3D-printed enclosure
