---
title: Stretch Rect
description: Stretch Rect
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b5e3b4d0-b925-4b07-ad2a-f4c6aedc8a62
author: dawn.wood
ms.author: dawnwood
ms.date: 11/05/2018
ms.topic: article


---

# <span id="p_hlk_test.a41ed4db-937f-4fe6-a9bd-0bcef993e8c3"></span>Stretch Rect


This automated test verifies correct implementation of the driver functionality that underlies the **IDirect3DDevice9::StretchRect** method.

The Stretch Rect test uses the **IDirect3D9::CheckDeviceFormat** method to determine the combinations of formats and surface types that the driver supports. It also uses the **IDirect3D9::CheckDeviceFormatConversion** method to determine the color-conversion operations that the driver supports.

For all valid surface-type combinations, the test performs a comprehensive set of **StretchRect** operations. These operations include those that involve stretching, color conversion, and copies to or from a subset rectangle (subrect). In these test cases, the source surface may be a texture surface (RT or non-RT), an off-screen render target, or an off-screen plain surface. The destination must be a render target or an RT texture surface.

Under D3D9L, the test also considers a more comprehensive set of source and destination surface-type combinations: Each surface may be a non-RT texture surface, an RT texture surface, an off-screen RT, or an off-screen plain surface. All sixteen combinations are tested. However, in compliance with D3D9L specifications, the **StretchRect** operations are limited to those that involve only full-surface copies without stretching or color conversion.

The test accomplishes automatic verification by rendering both the destination surface and a reference surface and comparing the rendered images. The test uses the **LoadSurfaceFromSurface** function in D3DX9 to prepare reference images.

This topic applies to the following test jobs:

-   Stretch Rect

-   Stretch Rect (WoW64)

## Test details

|||
|---|---|
| **Specifications**  | <ul><li>Device.Graphics.AdapterRender.MinimumDirectXLevel</li></ul> |  
| **Platforms**   | <ul><li>Windows 10, client editions (x86)</li><li>Windows 10, client editions (x64)</li><li>Windows Server 2016 (x64)</li><li>Windows 10, client editions (ARM64)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li><li>Windows 10, version 1803</li><li>Next update to Windows 10</li></ul> |
|**Expected run time (in minutes)**| 45 |
|**Category**| Compatibility |
|**Timeout (in minutes)**| 2700 |
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
<td><p><strong>Stretchrect.exe -M:1 -dx9 -whql -logclean</strong></p></td>
<td><p>Runs the Stretch Rect test job.</p></td>
</tr>
<tr class="even">
<td><p><strong>stretchrect.exe -M:1 -whql -logclean</strong></p></td>
<td><p>Runs the Stretch Rect (WoW64) test job.</p></td>
</tr>
</tbody>
</table>

> [!NOTE]
> 
> For command-line help for this test binary, type **/?**.



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
<td><p>D3dref9.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support</p></td>
</tr>
<tr class="even">
<td><p>D3dx10_test.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>D3dx11_test.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>Fpstate.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\utility&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>Modechange.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\utility&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>Stretchrect.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest&lt;/p&gt;</td>
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












