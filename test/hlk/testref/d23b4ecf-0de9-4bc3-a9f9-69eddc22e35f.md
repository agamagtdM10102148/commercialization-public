---
title: IPSec TOv2 Logo Test
description: IPSec TOv2 Logo Test
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f573e5d7-9933-49e9-9160-68cd61cb6fee
author: dawn.wood
ms.author: dawnwood
ms.date: 11/05/2018
ms.topic: article


---

# <span id="p_hlk_test.d23b4ecf-0de9-4bc3-a9f9-69eddc22e35f"></span>IPSec TOv2 Logo Test


This test runs the Task Offload Logo test.

## Test details

|||
|---|---|
| **Specifications**  | <ul><li>Device.Network.LAN.IPsec.IPsec</li></ul> |  
| **Platforms**   | <ul><li>Windows 10, client editions (x64)</li><li>Windows Server 2016 (x64)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li><li>Windows 10, version 1803</li><li>Next update to Windows 10</li></ul> |
|**Expected run time (in minutes)**| 2 |
|**Category**| Development |
|**Timeout (in minutes)**| 120 |
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

For troubleshooting information, see [Troubleshooting Device.Network Testing](troubleshooting-devicenetwork-testing.md).

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
<td><p><strong>CPerseus.exe /module:[TestDirectory]\Suites\TOv2Logo.xml /type:&quot;IPSec Scenario Testing Add-in&quot;</strong></p></td>
<td><p>Runs the test.</p></td>
</tr>
</tbody>
</table>

> [!NOTE]
> 
> For command-line help for this test binary, type **/h**.



### <span id="File_list"></span><span id="file_list"></span><span id="FILE_LIST"></span>File list

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>File</th>
<th>Location</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPerseus.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>TOv2Logo.xml</p></td>
<td><p><em>&lt;SystemDrive&gt;</em>\IkeTest\Suites</p></td>
</tr>
</tbody>
</table>



### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name                            | Parameter description                                                                     |
|-------------------------------------------|-------------------------------------------------------------------------------------------|
| **queryTestNicMacAddress**                | Mac address of test network adapter                                                       |
| **ReplacePatternsInFile.ps1**             |                                                                                           |
| **Win7\_ReplaceNicNameInTest.ps1**        |                                                                                           |
| **IsWin7.ps1**                            |                                                                                           |
| **queryTestNicClass**                     | Device class of test network adapter                                                      |
| **Win7\_updateNicOffloadStateById.vbs**   |                                                                                           |
| **Win7\_updateNicOffloadStateByName.vbs** |                                                                                           |
| **TestDirectory**                         |                                                                                           |
| **Win7\_updateNicOffloadStateByAddr.vbs** |                                                                                           |
| **SupportNetConnectionID**                | will hold the returned value from the detect job                                          |
| **TestNetConnectionID**                   | will hold the returned value from the detect job                                          |
| **EnableTOv2Support.ps1**                 |                                                                                           |
| **EnableTOv2Client.ps1**                  |                                                                                           |
| **queryTestNicDeviceID**                  |                                                                                           |
| **MsgNICIPSupport**                       | IP of Message NIC on Support machine, to be populated by detect.wsf before installer runs |
| **MsgNICIPClient**                        | IP of Message NIC on Client machine, to be populated by detect.wsf before installer runs  |












