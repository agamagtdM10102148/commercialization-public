---
title: VM Texture Blend
Description: VM Texture Blend
ms.assetid: 
author: dawn.wood
ms.author: dawnwood
ms.date: 11/05/2018
ms.topic: article


---

# VM Texture Blend



## Test details

|||
|---|---|
| **Specifications**  | <ul><li>Device.Graphics.WDDM24.AdapterRender.Paravirtualized.CoreRequirement</li></ul> |  
| **Platforms**   | <ul><li>Windows 10, client editions (x86)</li><li>Windows 10, client editions (x64)</li><li>Windows Server 2016 (x64)</li><li>Windows 10, client editions (ARM64)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li><li>Windows 10, version 1803</li><li>Next update to Windows 10</li></ul> |
|**Expected run time (in minutes)**| 2 |
|**Category**| Compatibility |
|**Timeout (in minutes)**| 120 |
|**Requires reboot**| false |
|**Requires special configuration**| false |
|**Type**| automatic |

## More Information
### Parameters

| Parameter Name | Parameter Description |
| --- | --- |
| **MONITOR** | Index of display output to target with test |
| **MODIFIEDCMDLINE** | Additional command line arguments for test executable |
| **LLU_NetAccessOnly** | LLU Name of net user |
| **ConfigDisplayCommandLine** | Custom Command Line for ConfigDisplay. Default: logo |
| **TDRArgs** | /get or /set |


## Additional Documentation
Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s): - [Device.Graphics additional documentation](device-graphics-additional-documentation.md)



## Troubleshooting
For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures.](../user/troubleshooting-windows-hlk-test-failures.md)