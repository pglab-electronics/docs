Setting
=======

!!! success
    To have an effective change. Click the SAVE button at the end of the **"Setting"** page and reboot E-BOARD from the **"Reboot"** page.

From the Home page go to the Setting page. You should see a page similar to the following picture.

<center>![image_alt](img/setting.png){width="512"  style="border: 1px solid grey;" }</center>

This page contains settings for:

- Timezone and Daylight Saving Time (DST)
- Safe control of the Relay outputs
- Reboot
- Relay and Shutter output times

To set E-BOARD time zone and the daylight saving time use the setting as shown in the following table:

| **Ref.**      |  **Description**                      |
| :-------------| :-------------------------------------|
| Timezone      | Set to your time zone in respect to UTC (Coordinated Universal Time). |
| DST/STD Week  | Set the week number of the month to start daylight saving time (DST) and to return to the standard time (STD). Set the field to NEVER to disable this feature. |
| DST/STD Day   | Set the day of the week to start DST and return to STD. |
| DST/STD Month | Set the month of the year to start DST and return to STD. |
| DST/STD Hours | Set the hour of the day to start DST and return to STD. |

The following settings are used as safety mechanism in the way E-BOARD controls the Relay outputs.

| **Ref.**        |  **Description**                     |
| :---------------| :------------------------------------|
| Auto OFF        | A timeout in seconds. E-BOARD automatically turns OFF all Relay terminal outputs that have been ON for more than the set time. Set the field to zero to disable this feature. |
| Max ON          | This is the maximum number of Relay outputs that can be ON at the same time.                   |
| MQTT QoS        | Set the Quality of Service level of the message sent to MQTT server.                           |
| MQTT retain     | Select the checkbox to retain the last sent message to the MQTT server.                        |
| MQTT lost       | Select the checkbox to turn off all relays when the MQTT connection with the server is lost.   |

!!! note
    The {==Auto_OFF==} setting is useful in an irrigation system setup to prevent an electro-valve staying open for too much time or to never close. For example, this can happen if the user forget to turn OFF the Relay output or if the connection with MQTT server is lost. In a critical scenario it is highly recommended to set this value.

!!! note
    The {==Max_On==} setting is useful to limit the number of devices connected to E-RELAY that can be ON at the same time. This helps to prevent overload.

!!! note
    The {==MQTT_lost==} setting is useful to turn OFF the Relay outputs when the MQTT server connection is lost. This prevents loads from continuing to run. In a critical scenario it's highly recommended to set this value

E-BOARD has an auto reboot feature. It is recommended to use this feature to increase the stability of E-BOARD over time.
The available settings are:

| **Ref.**      |  **Description**                      |
| :-------------| :-------------------------------------|
| Auto REBOOT   | Set E-BOARD auto reboot at a specific day. Possible values are EveryDay, or a specific day of the week. Set the field to NEVER to disable this feature.  |
| REBOOT hours  | Set the time in hours and minutes when to reboot E-BOARD. |

The following settings are used to set the Shutter outputs and to set the timing for opening and closing the shutter bi-directional AC motor.

| **Ref.**          |  **Description**                      |
| :-----------------| :-------------------------------------|
| Shutter Controls  | This value is the number of shutters that E-BOARD can control. When set to zero no relay output is reserved for controlling shutters.  |
| Shutter Time      | Set a time in seconds for opening and closing the shutter.  |

!!! note
    The {==Shutter_Time==} setting is a global time for all shutters. To set each individual shutter use {==Relay_Auto_OFF==}.

!!! note
    The two relay outputs that control a shutter always start from the Index 0. The first Relay output (Index 0) to open and the second Relay output (Index 1) to close.

    For example, in a scenario with 3 shutters set {== Shutter_Controls ==} to the value 3.
    E-BOARD now reserves relay outputs from 0 to 5 to control the 3 shutters. E-BOARD uses the relay outputs 0, 2, 4 for opening and the relay outputs 1, 3, 5 for closing.
    Please see [Wiring](wiring.md) for further details.

The {==Relay_Auto_OFF==} allows you to set the timing of each individual Relay output. This overrides the global setting {==Auto_OFF==}.
From the dropdown menu of {==Relay_Auto_OFF==} select the Relay index output (0 to 64) and then set the value in seconds.
You can control when to automatically turn OFF each individual Relay output.

| **Ref.**          |  **Description**                                      |
| :-----------------| :-----------------------------------------------------|
| Relay_Auto_OFF    | Sets the auto off time in seconds for a specific Relay output. |

!!! note
    The {==Relay_Auto_OFF==} for Shutter output defines the opening/closing time in seconds. When set to zero it uses the global setting {== Shutter_Time ==}.

!!! note
    The {==Relay_Auto_OFF==} for Relay outputs defines the auto off time in seconds. When set to zero it uses the global setting {== Auto_OFF ==}.
