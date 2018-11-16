---
title: NDISTest 6.0 - \1 Machine\ - 1c_Mini6RSSOids
description: NDISTest 6.0 - \ 1 Machine\ - 1c\_Mini6RSSOids
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1e140b1f-84f2-40d7-bde3-f4875680d7ec
author: dawn.wood
ms.author: dawnwood
ms.date: 11/05/2018
ms.topic: article


---

# NDISTest 6.0 - \[1 Machine\] - 1c_Mini6RSSOids


This test exercises the various receive side scaling OIDs. The miniport driver should:

-   Return a valid CAPABILITIES structure which includes support for NdisHashFunctionToeplitz.

-   Accept all the PARAMETER sets if the hash information is valid and supported.

-   Reject the PARAMETER sets if the hash information is not supported or invalid or if the hash table or the structure itself is not of the correct size.

-   In case the miniport rejects a PARAMETER set, it should retain the previously set PARAMETERs structure.

-   Miniport should handle 64 bit misaligned requests correctly.

## Test details

|||
|---|---|
| **Specifications**  | <ul><li>Device.Network.LAN.RSS.RSS</li><li>Device.Network.LAN.RSS.SetHashFunctionTypeAndValue</li><li>Device.Network.LAN.RSS.SupportIndirectionTablesSizes</li><li>Device.Network.LAN.RSS.SupportToeplitzHashFunction</li><li>Device.Network.LAN.RSS.SupportUpdatesToRSSInfo</li></ul> |  
| **Platforms**   | <ul><li>Windows 10, client editions (x86)</li><li>Windows 10, client editions (x64)</li><li>Windows Server 2016 (x64)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li><li>Windows 10, version 1803</li><li>Next update to Windows 10</li></ul> |
|**Expected run time (in minutes)**| 5 |
|**Category**| Development |
|**Timeout (in minutes)**| 300 |
|**Requires reboot**| false |
|**Requires special configuration**| false |
|**Type**| automatic |



## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [Device.Network additional documentation](device-network-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [LAN Testing Prerequisites](lan-testing-prerequisites.md).

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](../user/troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see [Troubleshooting LAN Testing](troubleshooting-lan-testing.md).

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


### <span id="Command_syntax"></span><span id="command_syntax"></span><span id="COMMAND_SYNTAX"></span>Command syntax

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Command</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>[WTTRunWorkingDir]\ndistest\bin\ndtest.exe /auto /client /dvi /u /target:Miniport /tc:[queryTestDeviceID] /script:{1c_Mini6RSSOids.wsf}</strong></p></td>
<td><p>Runs the test.</p></td>
</tr>
</tbody>
</table>



### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name        | Parameter description                    |
|-----------------------|------------------------------------------|
| **queryTestDeviceID** |                                          |
| **TestScript**        | comma separated list of test jobs to run |












