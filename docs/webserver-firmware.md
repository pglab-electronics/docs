Firmware
========

E-BOARD supports Over The Air Firmware update (OTA).
Updates with the latest Firmware is important to keep up with the latest features and bug fixes.

Over The Air Firmware update allows you to remotely update the Firmware of E-BOARD device without the need for physical access.

From the Home page go to the About page, you should see a page similar to the following picture.

<center>![image_alt](img/about.png){width="512"  style="border: 1px solid grey;" }</center>

In the previous picture you can see various information of the device, such as, current Firmware Version, Serial Number, MQTT server connection, CPU Voltage and Temperature and more.

To update the current firmware:

- Download from here [PG LAB Firmware](https://github.com/pglab-electronics/firmware) the latest E-BOARD firmware version
- On the About page click the button to **Choose File** and browse to select the new firmware
- Click **UPGRADE** button
- Your browser is now sending the new firmware to E-BOARD

When E-BOARD receives the firmware it proceeds with a CRC check and it overwrites the current firmware with the new one. The Green LED on the E-BOARD blinks rapidly a few times and then the device reboots.

This operation should take less than a minute.

From your browser, check again the About Page in **DEVICE INFORMATION**. The Firmware Version should be updated to the latest one.

!!! warning
    Never disconnect the power during the firmware update.

Factory Reset
-------------

E-BOARD stores a safe firmware inside the internal memory. The safe firmware is used if for any reason you want to restore the original factory firmware and to restore the default settings.

You have to proceed in the following mode:

- Insert a **NON** conductive stick inside E-BOARD to press down  the Reset button as shown in the following picture
- Press down and hold the internal button for more than 10 seconds
- Keep pressing down until the Green LED on the E-BOARD blinks rapidly. This informs the user that E-BOARD is now ready to restore the original firmware
- Now release the Reset button

<center>![image_alt](img/eboard_reset.png)</center>

From your browser, check the About Page in **DEVICE INFORMATION** to see if the Firmware Version has been updated.

!!! warning
    Never use a conductive stick to push the Reset button. This can cause an internal short circuit and damage the device.

!!! info
    If you press down the Reset button once E-BOARD just reboots.
