> **Huge thanks to DevEclipse1!**  
> DevEclipse1 helped a lot with MicroByte and played a major role in the development of this project.

# MicroByte

MicroByte is a compact handheld wireless/electronics tool built around the **Waveshare ESP32-C6-LCD-1.47**. It uses the board's **1.47-inch color display** and combines **IR**, **sub-GHz RF**, Wi-Fi, Bluetooth, battery monitoring, games, and other utilities into one small device.

## Project Status

> **Hardware testing note:** MicroByte has currently been tested with the **Waveshare ESP32-C6-LCD-1.47 onboard display only**. An external display connected separately has not been tested yet.


> **MicroByte is still a work in progress.**
>
> The project will continue to get better over time. Some features are experimental, incomplete, or may behave differently depending on the hardware/build.
>
> **CC1101 functionality may not work correctly yet** and is still being worked on.
>
> **Some features will be added over time.**

Please give feedback! Bug reports, ideas, suggestions, and feature requests are very welcome.

---

# Features

## Display & UI

- **Waveshare ESP32-C6-LCD-1.47** (using its onboard 1.47-inch display; the external-display setup has not been tested)
- **1.47-inch ST7789 color display**
- Terminal-style interface
- Multiple color themes
- Adjustable display brightness
- Boot animation
- Battery percentage display
- Hardware / wiring information screens
- Credits screen
- Physical-button navigation
- Web-based controller over the ESP32 access point

## Infrared (IR)

MicroByte includes both an **IR receiver** and **IR transmitter**.

- IR signal capture
- IR protocol detection
- Raw IR capture support
- Save captured IR codes
- IR code library
- Organize codes by category
- Rename saved codes
- Delete saved codes
- Send saved IR codes
- Send captured IR codes
- Built-in NEC transmission test
- TV remote database / TV remote commands
- TV power-code sweep
- IR burst / test feature

### IR transmitter resistor

A current-limiting resistor should be used with the IR LED. For a simple setup, use **100–220Ω**, with **220Ω recommended**.



The firmware uses `INPUT_PULLUP`, so the button is active when the GPIO is pulled LOW.

---

# Wi-Fi

MicroByte can run its own Wi-Fi access point for the web controller.

The web interface provides:

- Left / previous control
- Select
- Right / next control
- Hold-to-move controls
- Current screen status

MicroByte can also scan for nearby Wi-Fi networks.

---

# Bluetooth

MicroByte includes Bluetooth Low Energy scanning.

The BLE scanner can show:

- Advertised device names
- RSSI values
- Nearby BLE devices

---

# Games

The project includes built-in games through `games.hpp`.

The current menu includes:

- Snake
- Tetris
- Pong
- Raycast
- Brick Breaker
- Space Invaders

Additional games and improvements may be added later.

---

# Settings

The settings system includes:

- Color theme selection
- Boot animation on/off
- Display brightness
- IR transmission test
- Hardware check
- Wiring guide
- Credits

Settings such as the UI theme, boot animation, and display brightness are saved using ESP32 Preferences.

---

# Hardware You Will Need

## Required

- **Waveshare ESP32-C6-LCD-1.47** (using its onboard 1.47-inch display; the external-display setup has not been tested)
- **CC1101 module** (for RF features)
- **IR receiver module**
- **IR LED / transmitter circuit**
- **100–220Ω current-limiting resistor for the IR LED** (220Ω recommended for a simple setup)
- **3.7V Li-ion battery**
- **TP4056 charging/protection module**
- **2 × 100kΩ resistors** for the battery voltage divider
- Push buttons for UP, SELECT, and DOWN
- Jumper wires
- Breadboard or your own PCB/wiring

## Optional

- Enclosure
- Antenna for the CC1101 module, if your module supports one
- Appropriate transistor/resistor driver for a higher-power IR transmitter
- Power switch
- USB-C cable for programming/charging, depending on the hardware setup

---

# Connections / Pinout

MicroByte's current external connections are listed below. The **LCD wiring is intentionally not documented** because this project has only been tested using the **onboard Waveshare ESP32-C6-LCD-1.47 display**. An external display has not been tested.

| Function | ESP32-C6 |
|---|---:|
| Battery voltage measurement | **GPIO0** |
| CC1101 GDO0 | **GPIO1** |
| CC1101 CSN / CS | **GPIO2** |
| CC1101 MISO / SO | **GPIO3** |
| CC1101 MOSI / SI | **GPIO4** |
| CC1101 SCK | **GPIO5** |
| UP / LEFT button | **GPIO9** |
| SELECT button | **GPIO18** |
| DOWN / RIGHT button | **GPIO19** |
| IR receiver | **GPIO20** |
| IR transmitter | **GPIO23** |
| CC1101 VCC | **3.3V** |
| CC1101 GND | **GND** |

### Wiring Diagram

![MicroByte wiring diagram](diagram(4).jpg)


### Battery Measurement

The battery percentage uses a **2 × 100kΩ resistor voltage divider** connected to GPIO0. The divider and the ESP32 must share the same common ground.

The battery percentage is an **estimate and is not 100% accurate most of the time**. It can change depending on battery voltage, charging, and load. The battery measurement system will be improved and made more accurate in the future.

### IR Transmitter

The IR LED uses a current-limiting resistor. A **100–220Ω resistor** is recommended, with **220Ω** being a simple safer choice for a basic direct-drive setup.

### Power

The TP4056 is used for charging the Li-ion battery. For a master power switch, switching the positive supply is preferred over disconnecting only ground.

> **Note:** The exact power path should match the power-input requirements of the Waveshare board. A single Li-ion cell does not generate 5V by itself.

# Software / Libraries

The project uses Arduino/ESP32 libraries and project files including:

- Arduino
- ESP32 Arduino core
- `WiFi.h`
- `WebServer.h`
- `Preferences.h`
- `Arduino_GFX_Library`
- ESP32 BLE libraries
- `IRremote`
- `games.hpp`
- `ir_universal_send.hpp`

Keep the required local header files in the same Arduino sketch/project where needed.

---

# Firmware Development

> **The current MicroByte firmware was made with AI assistance.**
>
> This version is a work-in-progress prototype. The firmware will be **redone/reworked without AI** in the future to improve the code quality, structure, reliability, and maintainability.

# Development

MicroByte is actively being developed.

The project is expected to receive:

- More features
- More wireless tools
- Better CC1101 support
- UI improvements
- More games
- Better battery reporting
- Bug fixes
- Performance improvements
- More hardware compatibility

**Some features will be added over time.**

---

# Feedback

Please give me feedback!

Whether you find a bug, have an idea for a feature, want a different UI design, or have suggestions for improving the hardware, feedback is appreciated.

**Bug reports, feature requests, and suggestions are welcome.**

---

# Credits

## Huge thanks to DevEclipse1

A **HUGE thank you to DevEclipse1** for helping with this project.

Their help has been a major part of getting MicroByte to where it is today.

---

# Disclaimer

MicroByte is intended for learning, electronics experimentation, wireless research, and use with equipment and systems you are authorized to test.

Use the hardware responsibly and follow applicable laws and regulations.

---

**MicroByte — Small device. Big possibilities.**
