---
title: WindowsPeriod
description: Blocks the Windows logo key+Period key combination used to snap the current screen to the left or right gutter. Also blocks the Windows logo key+Shift+Period key combinations.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: D5280ECE-F748-4AE7-B6F2-90AB245F23D4
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# WindowsPeriod


Blocks the Windows logo key+Period key combination used to snap the current screen to the left or right gutter. Also blocks the Windows logo key+Shift+Period key combinations.

## Type


String

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Allowed</em></p></td>
<td><p>The Windows logo key+Period and Windows logo key+Shift+Period key combination is not blocked.</p>
<p>This is the default value.</p></td>
</tr>
<tr class="even">
<td><p><em>Blocked</em></p></td>
<td><p>The Windows logo key+Period and Windows logo key+Shift+Period key combination is blocked.</p></td>
</tr>
</tbody>
</table>

 

## Parent Hierarchy


[Microsoft-Windows-Embedded-KeyboardFilterService](microsoft-windows-embedded-keyboardfilterservice.md) | **WindowsPeriod**

## Valid Configuration Passes


offlineServicing

## Applies To


For a list of the Windows editions and architectures that this component supports, see [Microsoft-Windows-Embedded-KeyboardFilterService](microsoft-windows-embedded-keyboardfilterservice.md).

## XML example


```
<settings pass="offlineServicing">
    <component name="Microsoft-Windows-Embedded-KeyboardFilterService" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="NonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <WindowsPeriod>Blocked</WindowsPeriod>
    </component>
</settings>
```

 

 






