---
title: Lost Devices - Resource Management DX9.L
description: Lost Devices - Resource Management DX9.L
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 009e101a-c17e-4914-8fac-d36e03c715a2
author: dawn.wood
ms.author: dawnwood
ms.date: 11/05/2018
ms.topic: article


---

# <span id="p_hlk_test.750ea5cb-aa9d-4cf2-a42e-b8bebd95762e"></span>Lost Devices - Resource Management DX9.L


This automated test verifies the requirements listed in the test details table.

This topic applies to the following test jobs:

-   Lost Devices - Resource Management DX8 and lower (WoW64)

-   Lost Devices - Resource Management DX9 w Lost Texture

-   Lost Devices - Resource Management DX9 w Lost Texture (WoW64)

-   Lost Devices - Resource Management DX9 w-o Lost Texture

-   Lost Devices - Resource Management DX9 w-o Lost Texture (WoW64)

-   Lost Devices - Resource Management DX9.L

-   Lost Devices - Resource Management DX9.L (WoW64)

## Test details

|||
|---|---|
| **Specifications**  | <ul><li>Device.Graphics.AdapterRender.MinimumDirectXLevel</li></ul> |  
| **Platforms**   | <ul><li>Windows 10, client editions (x86)</li><li>Windows 10, client editions (x64)</li><li>Windows Server 2016 (x64)</li><li>Windows 10, client editions (ARM64)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li><li>Windows 10, version 1803</li><li>Next update to Windows 10</li></ul> |
|**Expected run time (in minutes)**| 13 |
|**Category**| Compatibility |
|**Timeout (in minutes)**| 780 |
|**Requires reboot**| false |
|**Requires special configuration**| false |
|**Type**| automatic |



## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [Device.Graphics additional documentation](device-graphics-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [Graphic Adapter or Chipset Testing Prerequisites](graphic-adapter-or-chipset-testing-prerequisites.md).

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](../user/troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see [Troubleshooting Device.Graphics Testing](troubleshooting-devicegraphics-testing.md).

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


This section will include test-related content that may not aid the tester in running or troubleshooting the test, but is information that is good to know, but not necessary for running the test.

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
<td><p><strong>Lostdev -!dx9 -M:1 -whql -logclean</strong></p></td>
<td><p>This command runs the Lost Devices - Resource Management DX8 and lower (WoW64) test job.</p></td>
</tr>
<tr class="even">
<td><p><strong>Lostdev -dx9 -losttexture -M:1 -dx9 -whql -logclean</strong></p></td>
<td><p>This command runs the Lost Devices - Resource Management DX9 w Lost Texture test job.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Lostdev -dx9 -losttexture -M:1 -whql -logclean</strong></p></td>
<td><p>This command runs the Lost Devices - Resource Management DX9 w Lost Texture (WoW64) test job.</p></td>
</tr>
<tr class="even">
<td><p><strong>Lostdev -dx9 -!losttexture -M:1 -dx9 -whql -logclean</strong></p></td>
<td><p>This command runs the Lost Devices - Resource Management DX9 w-o Lost Texture test job.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Lostdev -dx9 -!losttexture -M:1 -whql -logclean</strong></p></td>
<td><p>This command runs the Lost Devices - Resource Management DX9 w-o Lost Texture (WoW64) test job.</p></td>
</tr>
<tr class="even">
<td><p><strong>Lostdev -dx9.1 -M:1 -dx9 -whql -logclean</strong></p></td>
<td><p>This command runs the Lost Devices - Resource Management DX9.L test job.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Lostdev -dx9.1 -M:1 -whql -logclean</strong></p></td>
<td><p>This command runs the Lost Devices - Resource Management DX9.L (WoW64) test job.</p></td>
</tr>
</tbody>
</table>

> [!NOTE]
> 
> For command line help for this test binary, type **/h**.



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
<td><p>Configdisplay.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\tools&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>D3d10ref.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>D3d11ref.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>D3dcompiler_test.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>D3dref.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support</p></td>
</tr>
<tr class="even">
<td><p>D3dref8.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>D3dref9.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>D3dx10_test.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>D3dx11_TEST.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>D3dx8d.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>D3dx9_TEST.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>Fpstate.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\utility&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>Lostdev.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>Modechange.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\utility&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>TDRWatch.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>Vbswap.x</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\conf&lt;/p&gt;</td>
</tr>
</tbody>
</table>



### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name               | Parameter description                                 |
|------------------------------|-------------------------------------------------------|
| **MONITOR**                  | Index of display output to target with test           |
| **MODIFIEDCMDLINE**          | Additional command line arguments for test executable |
| **LLU\_NetAccessOnly**       | LLU Name of net user                                  |
| **ConfigDisplayCommandLine** | Custom Command Line for ConfigDisplay. Default: logo  |
| **TDRArgs**                  | /get or /set                                          |












