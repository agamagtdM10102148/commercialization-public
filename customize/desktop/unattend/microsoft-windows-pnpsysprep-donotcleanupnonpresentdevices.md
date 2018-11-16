---
title: DoNotCleanUpNonPresentDevices
description: DoNotCleanUpNonPresentDevices
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: faaf41be-d2fa-458c-9c03-e3f8e88a66d5
ms.mktglfcycl: deploy
ms.sitesec: msdn
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# DoNotCleanUpNonPresentDevices


The `DoNotCleanUpNonPresentDevices` setting specifies whether plug and play information for devices that are not detected on the destination computer during the next specialize should remain on the computer.

This setting is useful for devices with a physical on/off switch. When a physical on/off switch is off, the device information may be removed during either the **generalize** or **specialize** configuration pass. However, when both [PersistAllDeviceInstalls](microsoft-windows-pnpsysprep-persistalldeviceinstalls.md) and `DoNotCleanUpNonPresentDevices` are set to **true**, the device information remains on the computer.

This list describes the process Windows Setup uses to determine whether plug and play information remains on the computer, or is removed, or is removed and then re-initialized:

-   When [PersistAllDeviceInstalls](microsoft-windows-pnpsysprep-persistalldeviceinstalls.md) is set to **true**, then during the **generalize** configuration pass, plug and play device information remains on the computer.

    During the next **specialize** configuration pass:

    -   Any plug and play devices that are detected are re-installed.

    -   For plug and play devices that are not detected:

        -   If `DoNotCleanUpNonPresentDevices` is set to **true**, the device information remains on the computer.

        -   If `DoNotCleanUpNonPresentDevices` is set to **false**, the device information is removed from the computer.

-   When [PersistAllDeviceInstalls](microsoft-windows-pnpsysprep-persistalldeviceinstalls.md) is set to **false**, then during the **generalize** configuration pass, plug and play device information is removed from the computer.

    During the next **specialize** configuration pass:

    -   Any plug and play devices that are detected are re-installed.

    -   Any plug and play devices that are not detected remain uninstalled. The `DoNotCleanUpNonPresentDevices` setting will have no effect.

**Warning**  
Using the `DoNotCleanUpNonPresentDevices` setting can lead to the unnecessary storage of excess device state and contribute to slower boot times. For more information about maintaining driver configurations when capturing a Windows image, see [this Microsoft Website](http://go.microsoft.com/fwlink/p/?linkid=184946).

 

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>True</strong></p></td>
<td><p>Specifies that during the next <strong>specialize</strong> configuration pass:</p>
<p>plug and play devices that are not detected remain installed.</p></td>
</tr>
<tr class="even">
<td><p><strong>false</strong></p></td>
<td><p>Specifies that during the next <strong>specialize</strong> configuration pass:</p>
<p>plug and play devices that are not detected are removed from the computer.</p>
<p>This is the default value.</p></td>
</tr>
</tbody>
</table>

 

## Valid Configuration Passes


generalize

**Note**  
Though this setting is specified in the **generalize** configuration pass, it controls the behavior for the next **specialize** configuration pass.

 

## Parent Hierarchy


[Microsoft-Windows-PnpSysprep](microsoft-windows-pnpsysprep.md) | **DoNotCleanUpNonPresentDevices**

## Applies To


For a list of the supported Windows editions and architectures that this component supports, see [Microsoft-Windows-PnpSysprep](microsoft-windows-pnpsysprep.md).

## XML Example


The following XML output specifies that drivers for devices that are not on the destination computer remain installed during the **generalize** configuration pass and the next **specialize** configuration pass.

```
<PersistAllDeviceInstalls>true</PersistAllDeviceInstalls>
<DoNotCleanUpNonPresentDevices>true</DoNotCleanUpNonPresentDevices>
```

## Related topics


[PersistAllDeviceInstalls](microsoft-windows-pnpsysprep-persistalldeviceinstalls.md)

[Microsoft-Windows-PnpSysprep](microsoft-windows-pnpsysprep.md)

[Maintain Driver Configurations When Capturing a Windows Image](http://go.microsoft.com/fwlink/p/?linkid=184946)

 

 







