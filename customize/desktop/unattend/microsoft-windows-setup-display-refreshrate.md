---
title: RefreshRate
description: RefreshRate
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 45570f1b-8e3a-4f6c-b8dc-a39ad8c169b1
ms.mktglfcycl: deploy
ms.sitesec: msdn
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# RefreshRate


`RefreshRate` specifies the screen refresh rate to apply to the graphics adapter.

This setting is used to configure only Windows PE, and is not applied to the Windows installation. To change the display settings for the Windows installation, see [Display](microsoft-windows-shell-setup-display.md) in the [Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md) component.

**Note**  
We recommend that you use the default settings. If you select a value for this setting that is not supported by Windows PE, your video adapter, or the display monitor, then Windows PE might show only a blank screen and will not display an error.

 

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>refresh_rate_in_hertz</em></p></td>
<td><p>Specifies the screen refresh rate to apply to the graphics adapter.</p>
<p>For example, to specify a refresh rate of 60 hertz, set <code>RefreshRate</code> to <strong>60</strong>.</p>
<p>The value must be supported by the graphics adapter and the display monitor.</p></td>
</tr>
</tbody>
</table>

 

## Valid Configuration Passes


windowsPE

## Parent Hierarchy


[microsoft-windows-setup-](microsoft-windows-setup.md) | [Display](microsoft-windows-setup-display.md) | **RefreshRate**

## Applies To


For the list of the supported Windows editions and architectures that this component supports, see [microsoft-windows-setup-](microsoft-windows-setup.md).

## XML Example


The following XML output sets the display resolution to 640x480, with 16-bit color depth and a refresh rate of 60 hertz.

```
<Display>
   <HorizontalResolution>640</HorizontalResolution>
   <VerticalResolution>480</VerticalResolution>
   <ColorDepth>16</ColorDepth>
   <RefreshRate>60</RefreshRate>
</Display>
```

## Related topics


[Display](microsoft-windows-setup-display.md)

 

 







