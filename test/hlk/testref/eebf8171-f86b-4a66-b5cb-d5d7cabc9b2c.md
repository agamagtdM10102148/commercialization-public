---
title: WGF11 Geometry Shader
description: WGF11 Geometry Shader
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d11b7b2c-7598-4e7e-91fd-40c728979773
author: dawn.wood
ms.author: dawnwood
ms.date: 11/05/2018
ms.topic: article


---

# <span id="p_hlk_test.eebf8171-f86b-4a66-b5cb-d5d7cabc9b2c"></span>WGF11 Geometry Shader


This automated test verifies verifies D3D graphics driver/hardware conformance for geometry shader features that are not specifically tested elsewhere.

This topic applies to the following test jobs:

-   WGF11 Geometry Shader

-   WGF11 Geometry Shader (WoW64)

## Test details

|||
|---|---|
| **Specifications**  | <ul><li>Device.Graphics.AdapterRender.D3D111Core.D3D111CorePrimary</li><li>Device.Graphics.AdapterRender.D3D11Core.D3D11CorePrimary</li><li>Device.Graphics.AdapterRender.D3D101Core.D3D101CorePrimary</li><li>Device.Graphics.AdapterRender.D3D10Core.D3D10CorePrimary</li></ul> |  
| **Platforms**   | <ul><li>Windows 10, client editions (x86)</li><li>Windows 10, client editions (x64)</li><li>Windows Server 2016 (x64)</li><li>Windows 10, client editions (ARM64)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li><li>Windows 10, version 1803</li><li>Next update to Windows 10</li></ul> |
|**Expected run time (in minutes)**| 2 |
|**Category**| Compatibility |
|**Timeout (in minutes)**| 120 |
|**Requires reboot**| false |
|**Requires special configuration**| false |
|**Type**| automatic |



## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [Device.Graphics additional documentation](device-graphics-additional-documentation.md)

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](../user/troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see [Troubleshooting Device.Graphics Testing](troubleshooting-devicegraphics-testing.md).

The test might return SKIP if it is run with a feature level that doesn't support the feature being tested. The test might return BLOCKED if there is an uncaught exception (framework catches it at the end and logs it).

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


The following items outline the Geometry Shader Conformance Test Plan:

**Geometry Shader Input**

- Verifies support for all input primitive types:

  -   Line

  -   Point

  -   Triangle

  -   LineAdj

  -   TriangleAdj

- PrimitiveID

  - Verifies that primitive ordering is respected.

  - PS test should test this for cases where there is no GS in the pipeline.

  - Cycle on Draw() and DrawInstanced().

    > [!NOTE]
    > 
    > Make sure that the id resets to zero for each instance drawn.



- InstanceID

**Geometry Shader Output**

- RenderTargetArrayIndex

- Position

- Limits

  > [!NOTE]
  > 
  > Maximum GS invocation output data size (components \* vertices) go up to 1024.



- Ordering (Verifies that primitive ordering is respected.)

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
<td><p><strong>Wgf11geometryshader</strong></p></td>
<td><p>Runs the test jobs. Without any options, the test enumerates devices.</p></td>
</tr>
<tr class="even">
<td><p><strong>-FeatureLevel:XX.X</strong></p></td>
<td><p>Sets the feature level, where XX.X is the Feature Level the test will run at: 10.0, 10.1, or 11.0.</p></td>
</tr>
</tbody>
</table>

> [!NOTE]
> 
> For command line help for this test binary, type **/?**.



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
<td><p>D3d11_1sdklayers.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>D3d11ref.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>D3d11sdklayers.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>D3dcompiler_test.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support</p></td>
</tr>
<tr class="even">
<td><p>D3dx10_test.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>d3dx11_test.dll</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\support&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>TDRWatch.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>Wgf11geometryshader.exe</p></td>
<td><p><em>&lt;[testbinroot]&gt;</em>\nttest\windowstest\graphics\d3d\conf</p></td>
</tr>
</tbody>
</table>



### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name               | Parameter description                                 |
|------------------------------|-------------------------------------------------------|
| **MODIFIEDCMDLINE**          | Additional command line arguments for test executable |
| **LLU\_NetAccessOnly**       | LLU Name of net user                                  |
| **ConfigDisplayCommandLine** | Custom Command Line for ConfigDisplay. Default: logo  |
| **TDRArgs**                  | /get or /set                                          |












