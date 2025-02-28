PYTHON
======

E-BOARD can be controlled by python with the library **pypglab**. The library can be used to discover devices, to control relay and shutter outputs and to get status updates.

The library is simple to use and can be easily integrated in your personal project. Internally it creates a connection with an MQTT broker to control E-BOARD and receive status updates.
The library was created for PG LAB Electronics Home Assistant Integration. <br>
The library **pypglab** is available on [github](https://github.com/pglab-electronics/pypglab).

From your terminal window run the following command to install the library:

``` yaml
pip install pypglab
```

The library has a helper class to simplify the discovery and the use of PG LAB Electronics devices.
The helper class hides the complexity to setup the MQTT connection with the broker.

In the following example, the {==pyPgLab==} class connects with the MQTT broker and retrieves a specific E-BOARD device.

```yaml
from pypglab.helper import pyPgLab

pglab = pyPgLab()
pglab.start("192.168.1.8")
pglab.connect()

e_board = pglab.get_device_by_name("E-BOARD-DD53AC85")

pglab.stop()
```

The following is an example of how to print each property of E-BOARD device:

```yaml
print("IP address: " + e_board.ip)
print("MAC address: " + e_board.mac)
print("Device ID: " + e_board.id)
print("Device Name: " + e_board.name)
print("Device Type: " + e_board.type)
print("Device Manufacturer: "+ e_board.manufacturer)
print("Hardware Version: " + e_board.hardware_version)
print("Firmware Version: " + e_board.firmware_version)
```

In this example, all Relay outputs are turned ON and after a short time are turned OFF:

```yaml
from pypglab.relay import Relay
...

for relay in e_board.relays:
    asyncio.run( relay.turn_on() )
    time.sleep(0.02)
    asyncio.run( relay.turn_off() )
```

In this example, an open command is sent to the shutter.  It waits until that shutter state change to fully open.
Then a close command is sent.

```yaml
from pypglab.shutter import Shutter
...

for shutter in e_board.shutters:
    asyncio.run( shutter.open() )
    while (not shutter.state is Shutter.STATE_OPEN):
        time.sleep(1)
    asyncio.run( shutter.close() )
    while (not shutter.state is Shutter.STATE_CLOSED):
        time.sleep(1)
```

The following is an example of how to print the state of the internal sensors:

```yaml
from pypglab.const import SENSOR_REBOOT_TIME, SENSOR_TEMPERATURE, SENSOR_VOLTAGE
from pypglab.sensor import Sensor
...

sensors = e_board.sensors.state

print("MPU Temperature: " + str(sensors[SENSOR_TEMPERATURE]) + "[C]" )
print("MPU Voltage: " + str(sensors[SENSOR_VOLTAGE]) + "[V]")
print("Time from last reboot: " + str(sensors[SENSOR_REBOOT_TIME]) + "[sec]" )

```
