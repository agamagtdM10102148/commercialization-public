---
title: LaunchApp1
description: Blocks the Start Application 1 key.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 32DD340C-7516-4416-BAC9-646C0B5093FF
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# LaunchApp1


Blocks the Start Application 1 key.

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
<td><p>The Start Application 1 key is not blocked.</p>
<p>This is the default value.</p></td>
</tr>
<tr class="even">
<td><p><em>Blocked</em></p></td>
<td><p>The Start Application 1 key is blocked.</p></td>
</tr>
</tbody>
</table>

 

## Parent Hierarchy


[Microsoft-Windows-Embedded-KeyboardFilterService](microsoft-windows-embedded-keyboardfilterservice.md) | **LaunchApp1**

## Valid Configuration Passes


offlineServicing

## Applies To


For a list of the Windows editions and architectures that this component supports, see [Microsoft-Windows-Embedded-KeyboardFilterService](microsoft-windows-embedded-keyboardfilterservice.md).

## XML example


```
<settings pass="offlineServicing">
    <component name="Microsoft-Windows-Embedded-KeyboardFilterService" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="NonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <LaunchApp1>Blocked</LaunchApp1>
    </component>
</settings>
```

 

 






