---
title: CPMaxCores
description: CPMaxCores specifies the maximum percentage of logical processors (in terms of logical processors within each NUMA node) that can be in the un-parked state at any given time.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6C3C6857-183C-48EE-BCAE-70B0AFCB5470
author: themar-msft
ms.author: themar
ms.date: 10/05/2017
ms.topic: article


---

# CPMaxCores


`CPMaxCores` specifies the maximum percentage of logical processors (in terms of logical processors within each NUMA node) that can be in the un-parked state at any given time.

For example, in a NUMA node with 16 logical processors, configuring the value of this setting to 50% ensures that no more than 8 logical processors are ever in the un-parked state at the same time. The value of this setting will automatically be rounded up to the value of [CPMinCores](options-for-core-parking-cpmincores.md).

## <span id="Aliases_and_setting_visibility"></span><span id="aliases_and_setting_visibility"></span><span id="ALIASES_AND_SETTING_VISIBILITY"></span>Aliases and setting visibility


-   **Windows Provisioning:** `CPMaxCores`, `CPMaxCores1`

-   **PowerCfg:** `CPMAXCORES`, `CPMAXCORES1`

-   **Hidden setting:** Yes

## <span id="Values"></span><span id="values"></span><span id="VALUES"></span>Values


The value denotes percentage (%).

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
