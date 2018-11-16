---
title: WacomKMDF Driver
description: WacomKMDF Driver
MS-HAID:
- 'TouchSamples\_9fc183ca-ac0d-48b0-903f-75bbe2a46e5b.xml'
- 'p\_weg\_hardware.wacomkmdf\_driver'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a66a2ba1-a7e0-420d-9a0e-b93f9d5c7af5
ms.author: eliotgra
ms.date: 05/02/2017
ms.topic: article


---

# WacomKMDF Driver


### Description

The WacomKMDF directory contains a KMDF version of the sample Wacom HID minidriver.

The WacomPen drivers are HID minidrivers for pen devices from Wacom Technology Corporation. These are electromagnetic input devices that use a 16550 UART-compatible interface. If such a device is installed on a computer system, the corresponding driver is loaded on top of the system-supplied Serial.sys driver, which acts as a lower-level device filter driver. The corresponding sample INF file can be generated from Wacompen.inx. This INF file installs the WacomPen driver for devices whose device ID is ACPI\\WACF004. To install a device of this type by using Wacompen.inf, you must specify a device ID of ACPI\\WACF004 in the ACPI BIOS.

The sample drivers share code that is located in the following directories:

-   The src\\input\\hiddigi\\common directory contains code that is common to the WacomPen and EloMT sample drivers.

-   The src\\input\\hiddigi\\util directory contains utility functions that are common to all the sample drivers. The utility functions handle tracing driver operation and error logging.

The sample driver demonstrates how to write a KMDF driver for a HID device even though KMDF does not natively support minidrivers. This is achieved by a WDM shim driver (Hidkmdf.sys) that acts as the HIDCLASS minidriver while the real driver is a lower filter in the driver stack. Otherwise, the sample is very similar to the WDM version in terms of how easy it is to customize for a new driver project.

### Building the Sample

Use the standard driver build tools from the Windows Driver Kit. In a driver directory, type **build**. The build script will generate the Wacomdigi.sys driver.

### Installation

**Driver Files:**

-   Wacompen.inf

-   Wacomdigi.sys

-   Hidkmdf.sys (build from the src\\hid\\hidusbfx2\\hidmapper directory)

-   WDF co-installer from &lt;WDK ROOT&gt;\\redist\\wdf\\&lt;platform&gt;\\

To install the drivers, copy the driver files and the INF files to the same location. In Device Manager, complete the following steps:

On Windows XP Tablet PC Edition:

1.  Right-click the device, and click **Update Driver**.

2.  Select **Install from a list or specific location (Advanced)**, and then click **Next**..

3.  Select **Don't search. I will choose the driver to install**, and then click **Have Disk**..

4.  In the **Install From Disk** dialog box, type the path of the directory where you copied the driver and INF file, and then click **OK**..

5.  Click **Finish**.

On Windows Vista and Windows 7:

1.  Right-click the device, and then click **Update Driver**.

2.  Click the **Browse my computer for driver software** link.

3.  Click the **Let me pick from a list of device drivers on my computer** link.

4.  Click **Have Disk**.

5.  Navigate to the location of the driver file, and then click the INF file.

6.  Click **OK**.

### Resources

For information about Microsoft Windows Vista and the Tablet PC, see http://www.microsoft.com/tabletpc.

### Code Tour

This section includes a file manifest of all the files in the src\\input\\hiddigi directory.

### File Manifest

src\\input\\hiddigi\\WacomKMDF

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>File</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Errcodes.mc</p></td>
<td><p>Contains event code and messages.</p></td>
</tr>
<tr class="even">
<td><p>Pch.h</p></td>
<td><p>Precompiled header file.</p></td>
</tr>
<tr class="odd">
<td><p>Sources</p></td>
<td><p>WDK sources file.</p></td>
</tr>
<tr class="even">
<td><p>Makefile</p></td>
<td><p>WDK build environment make file.</p></td>
</tr>
<tr class="odd">
<td><p>WacomPen.c</p></td>
<td><p>Contains the OEM specific code.</p></td>
</tr>
<tr class="even">
<td><p>Oempen.c</p></td>
<td><p>Contains the OEM specific code.</p></td>
</tr>
<tr class="odd">
<td><p>WacomPen.h</p></td>
<td><p>Contains the OEM specific definitions.</p></td>
</tr>
<tr class="even">
<td><p>WacomPen.rc</p></td>
<td><p>The resource file for the driver.</p></td>
</tr>
<tr class="odd">
<td><p>Wacompen.inx</p></td>
<td><p>INX file that is used to generate INF files.</p></td>
</tr>
</tbody>
</table>

 

src\\input\\hiddigi\\common

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>File</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>hid.c</p></td>
<td><p>Handles all the internal HIDClass IOCTLs.</p></td>
</tr>
<tr class="even">
<td><p>naturalInput.h</p></td>
<td><p>Contains common definitions for UART digitizer drivers.</p></td>
</tr>
<tr class="odd">
<td><p>Pnp.c</p></td>
<td><p>Handles PnP and power management.</p></td>
</tr>
<tr class="even">
<td><p>Serial.c</p></td>
<td><p>Contains all functions that deal with the serial port.</p></td>
</tr>
<tr class="odd">
<td><p>Serial.h</p></td>
<td><p>Contains serial port definitions.</p></td>
</tr>
</tbody>
</table>

 

src\\input\\hiddigi\\util

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>File</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Errlog.c</p></td>
<td><p>Contains all the error logging functions.</p></td>
</tr>
<tr class="even">
<td><p>Errlog.h</p></td>
<td><p>Contains error logging definitions.</p></td>
</tr>
<tr class="odd">
<td><p>Wtrace.h</p></td>
<td><p>Definitions for trace macros. This should be edited to enable tracing if needed.</p></td>
</tr>
</tbody>
</table>

 

 

 






