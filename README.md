# Security Door Unlock System Using RFID and Arduino Mega

## Overview

This project is the final assignment for the Computer Laboratory 1 course. It involves the development of a security door unlock system using an Arduino Mega and an RFID card reader. The system reads the ID from an RFID card, and if the ID matches a predefined set of authorized IDs, it unlocks the door. This system can be used for secure access to rooms, such as those in hotels.

## Table of Contents

- [Project Description](#project-description)
- [Hardware Requirements](#hardware-requirements)
- [Software Requirements](#software-requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Project Description

The project uses an RFID reader connected to an Arduino Mega to read card IDs. When a card is scanned, the Arduino checks if the ID matches one of the authorized IDs stored in the system. If there is a match, the Arduino triggers a mechanism to unlock the door. This can be particularly useful in hotel room access systems, ensuring only authorized personnel or guests can enter.

## Hardware Requirements

- Arduino Mega
- RFID Card Reader (e.g., MFRC522)
- RFID Cards or Tags
- Relay Module (for controlling door lock mechanism)
- Door Lock Mechanism (e.g., electromagnetic lock or servo motor)
- Jumper Wires
- Breadboard (optional)

## Software Requirements

- Arduino IDE
- MFRC522 Library (for RFID reader)
- Additional Libraries: SPI.h, MFRC522.h

## Installation

### Install Arduino IDE

Download and install the Arduino IDE from [here](https://www.arduino.cc/en/software).

### Install Required Libraries

Open the Arduino IDE, go to `Sketch` > `Include Library` > `Manage Libraries`. Search for and install the following libraries:

- MFRC522

### Upload the Code

1. Connect your Arduino Mega to your computer.
2. Open the `security_door_unlock.ino` file in the Arduino IDE.
3. Select the correct board and port from `Tools` > `Board` and `Tools` > `Port`.
4. Click the upload button to upload the code to the Arduino Mega.

## Usage

### Connect the Hardware

Connect the RFID reader to the Arduino Mega as follows:
- SDA to pin 53
- SCK to pin 52
- MOSI to pin 51
- MISO to pin 50
- IRQ to pin 2
- GND to GND
- RST to pin 9
- 3.3V to 3.3V

Connect the relay module to a digital pin (e.g., pin 7) to control the door lock mechanism.

Connect the door lock mechanism to the relay module.

### Power the System

Provide power to the Arduino Mega and other components.

### Authorize RFID Cards

Update the code with the authorized card IDs in the `authorized_ids` array.

### Scan RFID Cards

Scan an RFID card near the RFID reader. If the card ID is authorized, the door will unlock.

## Contributing

Contributions are welcome! Please follow these steps to contribute:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature-name`).
3. Make your changes.
4. Commit your changes (`git commit -m 'Add some feature'`).
5. Push to the branch (`git push origin feature/your-feature-name`).
6. Open a pull request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
