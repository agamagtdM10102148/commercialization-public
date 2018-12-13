---
title: Windows Touch Response Latency (Down) Test
description: Windows Touch Response Latency (Down) Test
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: fd2fb077-8ba2-4acc-a15f-63948f5f1c0d
author: dawn.wood
ms.author: dawnwood
ms.date: 11/05/2018
ms.topic: article


---

# <span id="p_hlk_test.2ab4ddd6-e2e8-4e28-8bcc-2fe4eda21e31"></span>Windows Touch Response Latency (Down) Test


This test verifies that a Windows Touch device meets the response latency requirements for both idle and active states.

## Test details

|||
|---|---|
| **Specifications**  | <ul><li>Device.Input.Digitizer.Touch.Latency</li></ul> |  
| **Platforms**   | <ul><li>Windows 10, client editions (x86)</li><li>Windows 10, client editions (x64)</li><li>Windows 10, client editions (ARM64)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li><li>Windows 10, version 1803</li><li>Next update to Windows 10</li></ul> |
|**Expected run time (in minutes)**| 30 |
|**Category**| Compatibility |
|**Timeout (in minutes)**| 1800 |
|**Requires reboot**| false |
|**Requires special configuration**| false |
|**Type**| automatic |



## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [Device.Input additional documentation](device-input-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [Windows Touch Testing Prerequisites](windows-touch-testing-prerequisites.md).

Similar to response rate, low response latency plays a large role in ensuring fast and fluid motion. Conversely, a high degree of response latency breaks the illusion that the user is manipulating a physical object.

This test uses specialized hardware to measure the latency in touch packet delivery under two conditions: touch-down (stationary) and panning (continuous reporting, in motion).

To learn about the hardware and about associated procedures, see [How to Measure Touch Panning Latency](http://go.microsoft.com/fwlink/?LinkID=287027) and [How to Measure Touch Down Latency](http://go.microsoft.com/fwlink/?LinkID=287028).

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](../user/troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see **Troubleshooting Device.Digitizer Testing**.

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


### <span id="Command_syntax"></span><span id="command_syntax"></span><span id="COMMAND_SYNTAX"></span>Command syntax

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Command option</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>audiotouch.exe</strong></p></td>
<td><p>Runs the test.</p></td>
</tr>
</tbody>
</table>



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
<td><p>audiotouch.exe</p></td>
<td><p><em>&lt;testbinroot&gt;</em>\digitizer\Win8Touch</p></td>
</tr>
</tbody>
</table>












