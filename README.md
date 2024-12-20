ESPHome Device: Bedroom Dehumidifier
This ESPHome project uses the ESP32-C3 Super Mini board to control a bedroom dehumidifier, monitor temperature and humidity, and manage fan speed via PWM. It includes components for Wi-Fi connectivity, web server access, and integration with Home Assistant.

Hardware Components
Microcontroller:
ESP32-C3 Super Mini (board type: esp32-c3-devkitm-1).
Relay:
Used to toggle the dehumidifier’s power supply.
Controlled via GPIO0.
DHT22 Sensor:
Measures temperature and humidity.
Connected to GPIO1.
Binary Sensor (Tank Installed):
Monitors if the water tank is correctly installed.
Connected to GPIO3.
Fan (PWM Control):
Arctic Cooling 80MM PWM fan for cooling or ventilation.
PWM signal generated on GPIO5.
Wi-Fi Signal and System Monitoring:
Tracks signal strength and system uptime.
ESPHome Features
Wi-Fi Connectivity:
Configured with a static IP (10.100.10.86) for reliable integration into the network.
Includes a fallback AP for troubleshooting connectivity issues.
Web Server:
Provides a local web interface for monitoring and control.
Home Assistant Integration:
Exposes all sensors, switches, and controls to Home Assistant via API.
Text Sensors:
Displays firmware version, IP address, and human-readable uptime.
ESPHome YAML Configuration Overview
Wi-Fi and Connectivity
Static IP configuration ensures consistent communication.
Output power set to 17.5dB for optimal Wi-Fi range.
Includes an AP fallback mode.
Sensors
Temperature and Humidity:
DHT22 sensor measures temperature and humidity every 30 seconds.
Binary Sensor (Tank Installed):
Detects if the water tank is properly installed using GPIO3.
Delayed ON filter prevents false positives.
Wi-Fi Signal:
Tracks Wi-Fi strength and updates every 10 minutes.
Uptime:
Reports uptime in both raw days and a human-readable format.
Switch and Relay
Relay Control:
Operates the dehumidifier using GPIO0.
Configurable via the web interface or Home Assistant.
Fan Control
Arctic Cooling 80MM PWM Fan:
Uses PWM to control the fan speed on GPIO5.
Configurable speed range with 100 levels of precision.
Outputs
LEDC PWM control for fan output, operating at 1000Hz.
How It Works
The binary sensor checks the status of the dehumidifier’s water tank.
If the tank is installed, the relay (GPIO0) turns ON.
If the tank is removed, the relay turns OFF.
The DHT22 sensor monitors the environment, reporting temperature and humidity values to Home Assistant and the web server.
The Arctic Cooling 80MM PWM fan adjusts its speed dynamically or manually via Home Assistant, using GPIO5.
Wi-Fi metrics (signal strength, IP) and uptime information are displayed in Home Assistant or the ESPHome web server.
Key GPIO Assignments
GPIO	Component	Description
0	Relay	Controls the dehumidifier power.
1	DHT22 Sensor	Reads temperature and humidity.
3	Tank Binary Sensor	Detects tank installation status.
5	PWM Output	Controls Arctic Cooling 80MM PWM fan.
Features for Debugging and Maintenance
Local web server for real-time monitoring.
Fallback AP for easy troubleshooting.
OTA updates for seamless firmware upgrades.
