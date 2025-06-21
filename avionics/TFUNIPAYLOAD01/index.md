---
layout: page
title: "TFUNIPAYLOAD01 - Universal MAVLink Sensor Interface"
permalink: /avionics/TFUNIPAYLOAD01/
parent: "Communication & Interfaces"
nav_order: "77"
---

# TFUNIPAYLOAD01 – Universal MAVLink Sensor Interface for UAV Payloads

TFUNIPAYLOAD01 is a universal interface board designed for seamless integration of custom sensors with PX4 or ArduPilot-based UAVs, especially when no dedicated driver exists for the sensor within the flight stack.

![TF-ATMON with TFUNIPAYLOAD01 block diagram](https://raw.githubusercontent.com/ThunderFly-aerospace/TFUNIPAYLOAD01/refs/heads/TFUNIPAYLOAD01A/doc/img/block_schematics.svg)

Its key advantage lies in the use of [MAVLink Tunnel packets](https://mavlink.io/en/services/tunnel.html), eliminating the need to modify autopilot firmware. This solution is suited for rapid deployment and testing of new environmental or scientific sensors without the need to delve into autopilot firmware development. It provides a plug-and-play bridge between your sensor and the powerful MAVLink ecosystem.

## Advantages of the MAVLink Tunnel Approach

* **No firmware modification** of PX4 or ArduPilot is necessary
* **Standardized MAVLink interface** allows inspection and logging tools (QGC, uLog, MAVSDK)
* **Sensor abstraction**: only the payload firmware knows the sensor-specific protocol and interface
* **Flexible and portable**: The same approach works across multiple autopilot flight stacks

## Hardware Overview

The TFUNIPAYLOAD01 module is based on the [MLAB ATmegaTQ4401](https://www.mlab.cz/module/ATmegaTQ4401/) board equipped with an ATmega1284P microcontroller. This hardware platform provides:

* 128 kB Flash and 16 kB RAM – sufficient for MAVLink message handling
* Multiple UARTs for communication with both sensors and the autopilot
* Standard [MLAB form factor](https://www.mlab.cz/) for mechanical and electrical compatibility with other modules

## Intended Use Case

TFUNIPAYLOAD01 is intended for users developing or deploying atmospheric or scientific sensors where direct driver support in PX4/ArduPilot is not yet available or practical. Common use cases include:

* Experimental sensors under development
* Rare or proprietary measurement devices
* Quick integration of payloads without altering autopilot code

## Communication Principle

Sensor data is processed on the TFUNIPAYLOAD01 module using **Arduino-compatible firmware**. The microcontroller encodes the measurements into **MAVLink Tunnel packets**, which are:

* Sent over UART to the autopilot's telemetry port
* Logged automatically by the autopilot (if configured correctly)
* Forwarded to the Ground Control Station (GCS) with software such as QGroundControl or [TF-ATMON](/instruments/TF-ATMON)

The [TF-ATMON system](/instruments/TF-ATMON) is specifically optimized to receive and process such sensor data using MAVLink Tunnel messages, while enabling the TF-ATMON system to visualize and geolocate the sensor measurements in time and space. This allows users to quickly gain insight into the measured environment without requiring any sensor-specific firmware changes in PX4 or ArduPilot.

## Integration Workflow

1. **Connect your sensor** to one of the TFUNIPAYLOAD01's UART or analog interfaces.
2. **Develop a small Arduino sketch** for the ATmega1284P to:

   * Read data from the sensor
   * Format it as a `MAVLink TUNNEL` message
   * Send it via serial port to the autopilot
3. **Wire the TFUNIPAYLOAD01** to an available TELEM port on the Pixhawk or compatible autopilot.
4. **Configure autopilot parameters** (see below) to enable MAVLink message logging in PX4.

## PX4 Parameter Configuration

The following PX4 parameters must be set (example for TELEM2):

| Parameter          | Value   | Description                              |
| ------------------ | ------- | ---------------------------------------- |
| MAV\_1\_CONFIG     | TELEM 2 | Enable MAVLink on the correct UART port  |
| MAV\_1\_FORWARD    | 1       | Enable message forwarding                |
| MAV\_1\_RADIO\_CTL | 0       | Disable radio control on that port       |
| MAV\_1\_RATE       | 0 B/s   | Unlimited rate                           |
| SER\_TEL2\_BAUD    | 57600   | Baud rate (match your firmware settings) |

## Example Firmware

Refer to the `TFUNIPAYLOAD_MINIMAL` sketch for a lightweight example that sends only `HEARTBEAT` and `TUNNEL` messages:

```cpp
mav.SendTunnelData(data, sizeof(data), sensor_id, 1, 1);
```

### Function Arguments:

* `data`: array of bytes (max 127)
* `length`: length of data
* `sensor_id`: identifier for your custom sensor
* `sysid`: usually `1`, or `0` for broadcast
* `compid`: usually `1`, or `0` for broadcast


## How to Verify MAVLink Message Reception

### Using QGroundControl

Ensure your autopilot is connected via a telemetry radio or USB-UART bridge, not via its USB port. The following steps allow you to inspect incoming MAVLink TUNNEL messages:

1. Open QGroundControl and connect the autopilot.
2. Click the QGC logo (top left corner), navigate to **Analyze Tools**, then select **MAVLink Inspector**.
3. Look for messages of type `TUNNEL`. These confirm correct reception and forwarding.

> **Note:** This requires the messages to be broadcast (sysid = 0, compid = 0), and QGC must be on a MAVLink-enabled link (not USB).


![MavLink Tunnel messages in QGC](https://user-images.githubusercontent.com/5196729/99434203-cec17d00-290e-11eb-93a7-e089ba893775.png)


### Using the PX4 Console

You can verify message reception even without broadcast using the PX4 shell:

1. Connect via [mavlink\_shell.py](https://github.com/ThunderFly-aerospace/PX4Firmware/blob/master/Tools/mavlink_shell.py) or through QGroundControl > Analyze Tools > Console.
2. Run:

```
listener mavlink_tunnel -n 100
```

This command displays the last 100 received tunnel messages.

![listenner showing tunnel message](https://user-images.githubusercontent.com/5196729/99431661-6ae98500-290b-11eb-80a6-a08f8229d600.png)

### Using Flight Logs

MAVLink TUNNEL messages are logged in PX4 `.ulg` logs. Although tools like Flight Review don't visualize this type of data, you can:

* Use [PlotJuggler](https://plotjuggler.io/) to load and inspect message content
* Use [TFUNIPAYLOAD Log Viewer Notebook](https://github.com/ThunderFly-aerospace/TFUNIPAYLOAD/blob/master/SW/LogViewer/ReadTunnelData.ipynb) to parse tunnel data programmatically


### Logging and Monitoring

* Tunnel messages can be monitored using `listener mavlink_tunnel` on PX4
* Use QGroundControl with a radio modem to inspect `TUNNEL` messages in real time
* For post-processing, extract data from `.ulg` logs using custom tools or PlotJuggler

## Limitations

* Autopilot memory is limited – avoid sending excessive data
* Max 3 MAVLink instances (incl. modem) due to PX4 firmware constraints
* Proper MAVLink stream segregation is necessary for logging vs telemetry transmission


