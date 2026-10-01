# Tuya Monitor Daemon

Tuya Monitor Daemon is a service that integrates the ESP Controller with Tuya Cloud.

The daemon receives actions from Tuya Cloud, executes them through the ESP Controller service using UBUS, and returns execution results back to the Tuya platform.

## Features

Supported Tuya Actions:

- GetDevices
- PinOn
- PinOff
- ReadSensor

### GetDevices

Returns a list of available ESP devices.

#### Output

- Message
- Devices

Example:

```json
{
  "outputParams": {
    "Message": "Devices found",
    "Devices": "/dev/ttyUSB0 (VID=0x10C4 PID=0xEA60)"
  }
}