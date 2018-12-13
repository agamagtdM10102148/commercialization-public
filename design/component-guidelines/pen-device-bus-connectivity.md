---
title: Device Bus Connectivity
description: This topic discusses bus connectivity methods for a Windows pen device.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 3C53088C-3DFC-453B-9FC1-793069FC61FE
ms.author: eliotgra
ms.date: 05/02/2017
ms.topic: article


---

# Device Bus Connectivity


This topic discusses bus connectivity methods for a Windows pen device.

An integrated Windows pen device can use the Microsoft-provided inbox drivers to connect to its Windows host, using either HID over USB, or HID over I²C. However you can use any other bus that you want, as long as you provide the required Windows-compatible, 3rd party HID mini-port driver for the pen device. The following diagram shows the Windows 10 driver stack for a Windows pen device.

![diagram showing the windows 10 driver stack for a windows pen device.](../images/win10-pen-drv-stack.png)

For full compatibility with Windows 10 for desktop editions (Home, Pro, Enterprise, and Education), we recommend using the Microsoft-provided inbox drivers. If you decide to use a 3rd party mini-port driver, then you must add this 3rd party driver to the appropriate OEM, and System Restore images, and then make these images available for download on Windows Update.

The following sections present some examples of device configurations.

## <a href="" id="i2c-devices"></a>I²C Devices


An integrated Windows pen module is defined as the combination of a controller IC and a sensor.

A Windows pen module that connects to its Windows host via the I²C bus must, at a minimum, expose the following five connection pins:

-   A data line (SDA)
-   A clock line (SCL)
-   An interrupt line
-   A power supply line
-   A ground connection (GND)

The following is a diagram of the connections lines between a Windows pen device and its Windows host.

![diagram showing the connections lines between a windows pen device and its windows host.](../images/pen-i2c-connection.png)

When connecting to an I²C controller it is important to understand the bandwidth demands of all the components sharing that controller. A minimum I²C clock speed of 400 KHz is recommended for an integrated Windows pen. It is highly recommended that integrated Windows pen controllers do not share the same I²C controller with components that have high bandwidth usage.

We recommend connecting the interrupt line (also referred to as an ATTN line) to an On-SoC GPIO controller, or to an IOAPIC. The GPIO or IOAPIC resource to which the interrupt line is connected, should be capable of (and configured for) waking the SoC. The wake-up capability allows the integrated Windows pen to wake the system in various scenarios.

If you decide to use the wake functionality, the power line that is connected to the integrated Windows pen device should not be shared with other devices which are not wake-capable. In order for wake scenarios to function properly, the power line that is used must be energized during connected standby/S3 conditions.

**ACPI Table Entries**

A Windows pen device that is connected via I²C must define an entry in the Advanced Configuration and Power Interface (ACPI) table of the host, for the device to be recognized by the host. For more information about ACPI, see [Advanced Configuration and Power Interface Specification](http://www.acpi.info/spec.htm).

The ACPI table entry should specify the following information:

| Entry                          | Description                                                                                                                                                                                                                           |
|--------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ACPI Device Entry Name         | A 4-character identification unique to the ACPI table, to reference the device. For example, “WPEN”.                                                                                                                                  |
| ACPI Hardware ID               | A 4-character + 4-number ACPI hardware ID, to reference the device. This is exposed in device manager. For example, “MSFT0001”.                                                                                                       |
| Compatible ID                  | This should always be “PNP0C50” to indicate that the device is HID I²C compatible.                                                                                                                                                    |
| I²C Controller                 | Specifies an I²C controller on the Windows host. This controller is used to connect the pen to the Windows host, and makes it possible for the pen and the host to communicate. For example, “I2C3” – to indicate I²C controller \#3. |
| I²C Slave Address              | Specifies the I²C slave address for the device. The host uses this address to single out the pen device on the I²C bus for communication. For example, “0x6F”.                                                                        |
| I²C Speed                      | Specifies the maximum speed supported by both the device and the I²C controller. Specifying the speed in the ACPI table ensures reliable communication. This speed should not be any lower than 400KHz (0x61A80).                     |
| GPIO Controller                | The GPIO controller to which the pen's interrupt line is connected. This tells the host where to "listen" for interrupt signals. For example, “GPIO0” – to indicate GPIO controller \#0.                                              |
| GPIO Resource/Pin              | The GPIO controller pin to which pen's interrupt line is connected. The host then associates this specific GPIO pin with interrupt signals from the pen. For example, “{35}” – to indicate pin 35.                                    |
| GPIO Resource Type             | Defines the constraints around the GPIO resource. This entry for the ACPI table, should be set to “Exclusive” unless you want to select SoC wake. If you decide to select SoC Wake, then set this entry to “ExclusiveAndWake”.        |
| GPIO Interrupt Assertion Type  | Defines the type of triggering that the pen will provide for its interrupts. This can either be "Edge-triggered", or "Level-triggered". HID I²C-compliant devices should use “Level-triggered" interrupts.                            |
| GPIO Interrupt Assertion Level | Defines the voltage level on the interrupt line, when the interrupt is asserted by the device. This can be specified as “ActiveLow” or “ActiveHigh”.                                                                                  |

 

## USB Devices


A high-speed/full-speed integrated Windows pen module that is connected via USB 2.0, should expose the necessary pins for host connectivity.

Connection to the host can take many forms and is at the discretion of the integrator.

Note that, when connecting to a USB hub, it is important to understand the bandwidth demands of all the components that share the hub. It is highly recommended that high-bandwidth devices, and integrated Windows pen controllers do not share the same USB hub, as this may result in bandwidth demands that exceed bus capability.

**USB Bridge Devices (I**²**C -&gt; USB)**

If you use a USB bridge to connect an integrated I²C Windows pen to the host, the bridge should expose the integrated Windows pen as a distinct device node, with the device’s unique attributes (wVendorID, wProductID, wVersionID).
