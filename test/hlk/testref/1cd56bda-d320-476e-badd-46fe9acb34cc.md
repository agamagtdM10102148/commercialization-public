---
title: OPM - Protocol Test
description: OPM - Protocol Test
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: af2d7ee5-7ca8-4f24-a54b-caa497c4f3af
author: dawn.wood
ms.author: dawnwood
ms.date: 11/05/2018
ms.topic: article


---

# <span id="p_hlk_test.1cd56bda-d320-476e-badd-46fe9acb34cc"></span>OPM - Protocol Test


These automated tests run PVP-OPM (Protected Video Path - Output Protection Management) commands. They test display drivers for PVP-OPM compatibility, and check for the availability of digital protection (HDCP) and analog protections (ACP and CGMSA).

There are three assertions for this test:

-   The display driver must support PVP-OPM driver interfaces.

-   The display driver must support CGMSA and APS.

-   The display driver must support HDCP.

For all of the assertions, the test goes through the PVP-OPM initialization protocol. If initialization fails, all of the assertions fail for premium SKUs (and skip for basic SKUs). Tests do not actually verify each protection schema, but do query the driver for the availability.

This topic applies to the following test jobs:

-   OPM - HDCP CSS DVD Test

-   OPM - HDCP CSS DVD Test (WoW64)

-   OPM - HDCP Test

-   OPM - HDCP Test (WoW64)

-   OPM - Protocol Test

-   OPM - Protocol Test (WoW64)

## Test details

|||
|---|---|
| **Specifications**  | <ul><li>Device.Graphics.WDDM11.DisplayRender.Base</li><li>Device.Graphics.WDDM.DisplayRender.OutputProtection</li><li>Device.Graphics.WDDM.DisplayRender.OutputProtection.Windows7</li></ul> |  
| **Platforms**   | <ul><li>Windows 10, client editions (x86)</li><li>Windows 10, client editions (x64)</li><li>Windows Server 2016 (x64)</li><li>Windows 10, client editions (ARM64)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li><li>Windows 10, version 1803</li><li>Next update to Windows 10</li></ul> |
|**Expected run time (in minutes)**| 10 |
|**Category**| Compatibility |
|**Timeout (in minutes)**| 600 |
|**Requires reboot**| false |
|**Requires special configuration**| false |
|**Type**| automatic |



## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [Device.Graphics additional documentation](device-graphics-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [Graphic Adapter or Chipset Testing Prerequisites](graphic-adapter-or-chipset-testing-prerequisites.md).

In addition:

-   If the graphics card supports a digital connector (DVI or HDMI), you must connect and enable an HDCP-enabled monitor.

-   If the graphics card supports an analog connector (component, composite, or S-Video), you must connect and enable the analog connector.

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](../user/troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see [Troubleshooting Device.Graphics Testing](troubleshooting-devicegraphics-testing.md).

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


The following jobs validate the test assertions below:

-   OPM - HDCP CSS DVD Test

-   OPM - HDCP Test

-   OPM - Protocol Test

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
<td><p><strong>ShellRunner.exe -x premium -c OPM_CSSDVD_HDCP_Test.pro -l &quot;[WTTRunWorkingDir]\s98wtt_u.dll&quot;</strong></p></td>
<td><p>Runs the OPM - HDCP CSS DVD test job.</p></td>
</tr>
<tr class="even">
<td><p><strong>ShellRunner.exe -x premium -c OPM_CSSDVD_HDCP_Test.pro -l &quot;[WTTRunWorkingDir]\s98wtt_u.dll&quot;</strong></p></td>
<td><p>Runs the OPM - HDCP CSS DVD Test (WoW64) test job.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ShellRunner.exe -x basic -c OPM_HDCP_Test.pro -l &quot;[WTTRunWorkingDir]\s98wtt_u.dll&quot;</strong></p></td>
<td><p>Runs the OPM - HDCP test job.</p></td>
</tr>
<tr class="even">
<td><p><strong>ShellRunner.exe -x basic -c OPM_HDCP_Test.pro -l &quot;[WTTRunWorkingDir]\s98wtt_u.dll&quot;</strong></p></td>
<td><p>Runs the OPM - HDCP Test (WoW64) test job.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ShellRunner.exe -x basic -c OPM_Protocol_Test.pro -l &quot;[WTTRunWorkingDir]\s98wtt_u.dll&quot;</strong></p></td>
<td><p>Runs the OPM - Protocol test job.</p></td>
</tr>
<tr class="even">
<td><p><strong>ShellRunner.exe -x basic -c OPM_Protocol_Test.pro -l &quot;[WTTRunWorkingDir]\s98wtt_u.dll&quot;</strong></p></td>
<td><p>Runs the OPM - Protocol Test (WoW64) test job.</p></td>
</tr>
</tbody>
</table>

> [!NOTE]
> 
> For command line help for this test binary, type **/h**.



### <span id="File_List"></span><span id="file_list"></span><span id="FILE_LIST"></span>File List

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
<td><p>Configdisplay.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\tools&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>OPM_ACPandCGMSA_Test.pro</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>OpmCompTest.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>S98wtt_u.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>Shellrunner.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>TDRWatch.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics&lt;/p&gt;</td>
</tr>
</tbody>
</table>



### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

|        Parameter name        |                Parameter description                 |
|------------------------------|------------------------------------------------------|
|    **LLU\_NetAccessOnly**    |        LLU local name, local with net access         |
|       **LIBRARYNAME**        |             Library for the test to run              |
|       **PROFILENAME**        |             Profile for the test to run              |
|     **DISPLAYLOGOLEVEL**     |      Qualification level for submission: basic       |
| **ConfigDisplayCommandLine** | Custom Command Line for ConfigDisplay. Default: logo |
|         **TDRArgs**          |                     /get or /set                     |

