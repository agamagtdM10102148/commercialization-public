---
title: Required HID Top-Level Collections
description: This section discusses the required HID top-level collections that are used for precision touchpad reporting in Windows 10 and later operating systems.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 7AC803C9-EE9A-4244-82D9-D6C2357DACAE
ms.author: eliotgra
ms.date: 05/02/2017
ms.topic: article


---

# Required HID Top-Level Collections


This section discusses the required HID top-level collections that are used for precision touchpad reporting in Windows 10 and later operating systems.

A Windows Precision Touchpad device should expose two mandatory top-level collections: A Windows Precision Touchpad collection, and a Configuration collection. Optional (but recommended) collections for firmware updates and basic mouse mode support may also be implemented.

The following diagram shows the HID collections for a Windows Precision Touchpad device.

![diagram showing the hid collections for a windows precision touchpad device. image shows support for a vendor-specific firmware update collection.](../images/precision-img-hidcolls.png)

A sample descriptor (showing top-level collections) is provided in the [Sample Report Descriptors](touchpad-sample-report-descriptors.md) topic.

The following topics provide more details about the HID top-level collections.

## In this section


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Topic</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="touchpad-mouse-collection.md" data-raw-source="[Mouse Collection](touchpad-mouse-collection.md)">Mouse Collection</a></p></td>
<td><p>This topic discusses the mouse collection of a Windows Precision Touchpad device, and explains how the collection provides HID-compliant mouse reporting to the Windows host.</p></td>
</tr>
<tr class="even">
<td><p><a href="touchpad-configuration-collection.md" data-raw-source="[Configuration Collection](touchpad-configuration-collection.md)">Configuration Collection</a></p></td>
<td><p>This topic discusses the role played by the configuration collection of a Windows Precision Touchpad device, in Windows 10 and later operating systems.</p></td>
</tr>
<tr class="odd">
<td><p><a href="touchpad-windows-precision-touchpad-collection.md" data-raw-source="[Windows Precision Touchpad Collection](touchpad-windows-precision-touchpad-collection.md)">Windows Precision Touchpad Collection</a></p></td>
<td><p>This topic discusses the top-level collection of a Windows Precision Touchpad, and explains how the collection provides HID-compliant touchpad reporting to the Windows host.</p></td>
</tr>
<tr class="even">
<td><p><a href="touchpad-buttons-report-level-usages.md" data-raw-source="[Buttons, Report Level Usages](touchpad-buttons-report-level-usages.md)">Buttons, Report Level Usages</a></p></td>
<td><p>This topic discusses the report level usages for buttons, within the context of the <a href="touchpad-windows-precision-touchpad-collection.md" data-raw-source="[Windows Precision Touchpad Collection](touchpad-windows-precision-touchpad-collection.md)">Windows Precision Touchpad Collection</a>.</p></td>
</tr>
<tr class="odd">
<td><p><a href="touchpad-firmware-update-collection--optional-.md" data-raw-source="[Firmware Update Collection (Optional)](touchpad-firmware-update-collection--optional-.md)">Firmware Update Collection (Optional)</a></p></td>
<td><p>A Windows Precision Touchpad device can use the HID protocol to provide a vendor-specific top-level collection for performing device firmware and vendor configuration updates.</p></td>
</tr>
</tbody>
</table>

 

 

 






