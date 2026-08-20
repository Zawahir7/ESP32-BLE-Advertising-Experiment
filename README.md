# 🍏 ESP32 BLE Advertising Experiment

A small **ESP32 BLE advertising experiment** that generates rapidly changing manufacturer-specific BLE advertisement packets using the **NimBLE-Arduino** library.

This project is intended **for fun, learning, and experimentation with BLE advertising on your own ESP32 hardware**.

> ⚠️ **Educational / Controlled-Testing Notice**
>
> This project is provided for educational and experimental purposes only. Test it on your own hardware and in a controlled environment. Rapid BLE advertising can cause unexpected behavior on nearby devices, so do not use it to intentionally disrupt, spam, or interfere with other people's devices or networks.

---

## 📌 Features

* ESP32 BLE advertising
* Uses the NimBLE-Arduino library
* Generates manufacturer-specific advertisement data
* Randomizes parts of the advertisement payload
* Configures BLE transmission power
* Starts and stops advertising repeatedly
* Useful for learning about:

  * BLE advertising
  * Manufacturer-specific data
  * ESP32 BLE APIs
  * NimBLE
  * BLE packet structure

---

# 🛠️ Requirements

### Hardware

* ESP32 development board
* USB cable
* Computer

No external components are required for the basic experiment.

---

# 💻 Software Setup

## 1. Install Arduino IDE

First, download and install the **Arduino IDE** on your computer.

Open Arduino IDE after installation.

---

## 2. Install ESP32 Board Support

In Arduino IDE:

**File → Preferences**

Add the ESP32 Boards Manager URL if you haven't already configured it.

Then go to:

**Tools → Board → Boards Manager**

Search for:

```text
esp32
```

Install the **ESP32 by Espressif Systems** package.

After installation, select your ESP32 board from:

**Tools → Board**

For example:

```text
ESP32 Dev Module
```

---

# 📦 3. Install NimBLE-Arduino

This step is required before compiling the project.

In Arduino IDE:

**Sketch → Include Library → Manage Libraries**

Search for:

```text
NimBLE
```

Install:

```text
NimBLE-Arduino
```

The library provides:

```cpp
#include <NimBLEDevice.h>
```

If you skip this step, Arduino IDE will normally show an error similar to:

```text
fatal error: NimBLEDevice.h: No such file or directory
```

---

# 🚀 4. Open the Project

Create a new Arduino sketch.

Save it, for example, as:

```text
ESP32_BLE_Advertising_Experiment
```

Paste the project code into the `.ino` file.

Make sure the file has the `.ino` extension.

---

# 🔌 5. Connect Your ESP32

Connect the ESP32 to your computer using a USB cable.

Then select:

**Tools → Port**

Choose the COM port belonging to your ESP32.

If the board does not appear, install the appropriate USB-to-serial driver for your ESP32 board.

---

# ⚙️ 6. Select the Board

Go to:

**Tools → Board**

Select the correct ESP32 board.

For a generic ESP32 board, you can usually start with:

```text
ESP32 Dev Module
```

For an ESP32-S3, select the appropriate:

```text
ESP32S3 Dev Module
```

---

# 📤 7. Compile and Upload

Click:

**Verify ✓**

first to compile the program.

If compilation succeeds, click:

**Upload →**

If the ESP32 does not enter download mode automatically, hold the **BOOT** button while the upload starts, then release it when flashing begins.

---

# 🧪 How It Works

The project initializes the ESP32 BLE stack:

```cpp
NimBLEDevice::init("");
```

It then creates a BLE server and obtains its advertising object:

```cpp
NimBLEServer *pServer = NimBLEDevice::createServer();

pAdvertising = pServer->getAdvertising();
```

The program constructs manufacturer-specific advertisement data and changes some of the payload bytes using random values.

The advertising process is repeatedly started and stopped:

```text
Generate advertisement
        ↓
Set advertisement data
        ↓
Start BLE advertising
        ↓
Short delay
        ↓
Stop advertising
        ↓
Generate new advertisement
        ↓
Repeat
```

This makes it useful for experimenting with how BLE advertising packets are generated and transmitted.

---

# 🧩 Main Components

### NimBLEDevice

Used to initialize and control the ESP32 BLE stack.

### NimBLEServer

Provides the BLE server object used to access advertising functionality.

### NimBLEAdvertising

Controls BLE advertisement transmission.

### NimBLEAdvertisementData

Stores the advertisement payload that will be transmitted.

---

# 📡 Advertisement Data

The project creates a manufacturer-specific advertisement using:

```cpp
0xFF
```

as the manufacturer-specific data type.

The payload contains several fields, including a manufacturer identifier and randomized bytes.

Some values are generated using:

```cpp
esp_fill_random()
```

so that portions of the advertisement change between transmissions.

---

# 🎯 Transmission Power

The example attempts to configure the ESP32 BLE transmission power:

```cpp
ESP_PWR_LVL_P9
```

The actual available power levels and behavior can depend on the ESP32 chip, Arduino-ESP32 version, BLE stack, and board hardware.

---

# ⚠️ Important Safety / Testing Note

This is a **BLE advertising experiment**, not a tool for attacking or disrupting devices.

Please:

* Test with your own ESP32 and devices.
* Use it in a controlled environment.
* Do not intentionally flood or disrupt other people's devices.
* Do not use it to bypass security or interfere with wireless services.
* Stop the experiment if nearby devices behave unexpectedly.

The code is intended to help understand **BLE advertising and ESP32 development**.

---

# 📁 Suggested Repository Structure

```text
ESP32-BLE-Advertising-Experiment/
│
├── ESP32-BLE-Advertising-Experiment.ino
│
├── README.md
│
└── LICENSE
```

---

# 📜 License

You can use this project for personal learning and experimentation.

If you publish modified versions, please give appropriate credit to the original project/code sources you used.

---

# ⭐ Credits

Original concept/code attribution:

```text
ESP32 Sour Apple by RapierXbox
```

This repository is intended as an educational adaptation/documentation project for experimenting with ESP32 BLE advertising.

---

# 🤝 Contributing

If you want to improve the project, you can contribute things such as:

* Better BLE packet explanations
* ESP32-S3 compatibility
* Improved code structure
* BLE packet analysis
* Arduino IDE setup documentation
* Serial Monitor debugging
* Educational examples

---

# 📚 Learning Goals

After completing this project, you should have a basic understanding of:

* ESP32 development
* Arduino IDE
* Installing Arduino libraries
* BLE advertising
* BLE advertisement payloads
* Manufacturer-specific BLE data
* NimBLE-Arduino
* ESP32 random-number generation
* BLE transmission power configuration

---

## ⭐ If This Project Helped You

Consider starring the repository ⭐ and sharing improvements that help others learn ESP32 and BLE development.
