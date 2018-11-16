---
title: CPDecreaseTime
description: CPDecreaseTime specifies the minimum amount of time that must elapse before additional logical processors can be transitioned from the unparked state to the parked state.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: CA6572CD-DC6C-4A5E-952E-1F8FF640F81D
author: themar-msft
ms.author: themar
ms.date: 10/05/2017
ms.topic: article


---

# CPDecreaseTime


`CPDecreaseTime` specifies the minimum amount of time that must elapse before additional logical processors can be transitioned from the unparked state to the parked state. The time is specified in units of the number of processor performance time check intervals.

## <span id="Aliases_and_setting_visibility"></span><span id="aliases_and_setting_visibility"></span><span id="ALIASES_AND_SETTING_VISIBILITY"></span>Aliases and setting visibility


-   **Windows Provisioning:** `CPDecreaseTime`

-   **PowerCfg:** `CPDECREASETIME`

-   **Hidden setting:** Yes

## <span id="Values"></span><span id="values"></span><span id="VALUES"></span>Values


The value denotes time check intervals.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Minimum value</p></td>
<td><p>0</p></td>
</tr>
<tr class="even">
<td><p>Maximum value</p></td>
<td><p>100</p></td>
</tr>
</tbody>
</table>

 

## <span id="Applies_to"></span><span id="applies_to"></span><span id="APPLIES_TO"></span>Applies to


| Windows edition                                                        | x86-based devices | x64-based devices | ARM-based devices |
|------------------------------------------------------------------------|-------------------|-------------------|-------------------|
| Windows 10 for desktop editions (Home, Pro, Enterprise, and Education) | x86               | amd64             | N/A               |
| Windows 10 Mobile                                                      | N/A               | N/A               | Supported         |
