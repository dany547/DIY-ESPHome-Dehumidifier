# ESPHome Device: Bedroom Dehumidifier

This ESPHome project uses the **ESP32-C3 Super Mini** board to control a bedroom dehumidifier, monitor temperature and humidity, and manage fan speed via PWM. It integrates with Home Assistant and provides local control through a web server.

## Hardware Components
- **ESP32-C3 Super Mini**: Microcontroller for managing the device.
- **Relay** (GPIO0): Controls the dehumidifier's power supply.
- **DHT22 Sensor** (GPIO1): Monitors temperature and humidity.
- **Binary Sensor** (GPIO3): Detects if the water tank is installed.
- **Arctic Cooling 80MM PWM Fan** (GPIO5): Provides adjustable fan speed using PWM.

## ESPHome Features
- **Wi-Fi Connectivity**: Configured with a static IP (`10.100.10.86`) and fallback AP for recovery.
- **Web Server**: Offers a local interface for monitoring and manual control.
- **Home Assistant API**: Exposes sensors and switches for seamless integration.
- **Temperature & Humidity Monitoring**: Updates every 30 seconds via the DHT22 sensor.
- **Binary Sensor**: Ensures the dehumidifier operates only when the tank is installed.
- **PWM Fan Control**: Uses a configurable range of 100 speed levels for precise ventilation adjustments.
- **System Metrics**: Displays uptime and Wi-Fi signal strength in Home Assistant.

## GPIO Assignments
| GPIO | Component              | Function                                  |
|------|------------------------|------------------------------------------|
| 0    | Relay                 | Toggles the dehumidifier power.          |
| 1    | DHT22 Sensor          | Reads temperature and humidity.          |
| 3    | Binary Sensor         | Checks the water tank's installation.    |
| 5    | PWM Output            | Controls the Arctic Cooling 80MM fan.    |

## How It Works
1. The **binary sensor** checks the status of the dehumidifier’s water tank:
   - If the tank is installed, the relay (GPIO0) turns ON.
   - If the tank is removed, the relay turns OFF.
2. The **DHT22 sensor** monitors the environment and reports temperature and humidity values to Home Assistant.
3. The **Arctic Cooling 80MM PWM fan** adjusts its speed dynamically or manually via Home Assistant.
4. Wi-Fi metrics (signal strength, IP) and uptime information are displayed in Home Assistant and the ESPHome web server.

This project allows for efficient automation and monitoring of a dehumidifier, combining environmental sensors, fan control, and robust Home Assistant integration.
