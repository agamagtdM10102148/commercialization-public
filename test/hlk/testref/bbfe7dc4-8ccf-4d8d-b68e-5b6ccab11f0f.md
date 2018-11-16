---
title: MTP Compliance Test - Requirements - Media Players
description: MTP Compliance Test - Requirements - Media Players
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 5b5307fc-ce9b-4980-99fd-432d3d2ad8d1
author: dawn.wood
ms.author: dawnwood
ms.date: 11/05/2018
ms.topic: article


---

# <span id="p_hlk_test.bbfe7dc4-8ccf-4d8d-b68e-5b6ccab11f0f"></span>MTP Compliance Test - Requirements - Media Players


This test validates compliance with the Media Transfer Protocol (MTP), Revision 1.0.

This test makes sure that devices that use the MTP class driver comply with MTP implementation standards. This test is directed at portable media player devices that connect by using the MTP. This test validates compliance with defined protocols based on requirements that are documented in the Windows Certification Program.

> [!NOTE]
> 
> This test does not cover the following items:

-   Digital rights management (DRM) validation

-   Devices that use proprietary (third-party) drivers that work with the Windows Portable Device (WPD) driver stack

-   Devices that are not PTP or MTP-based



## Test details

|||
|---|---|
| **Specifications**  | <ul><li>Device.Portable.MediaPlayer.MTP</li></ul> |  
| **Platforms**   | <ul><li>Windows 10, client editions (x86)</li><li>Windows 10, client editions (x64)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li><li>Windows 10, version 1803</li><li>Next update to Windows 10</li></ul> |
|**Expected run time (in minutes)**| 5 |
|**Category**| Development |
|**Timeout (in minutes)**| 300 |
|**Requires reboot**| false |
|**Requires special configuration**| false |
|**Type**| automatic |



## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [Device.Portable additional documentation](device-portable-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [Device.Portable Testing Prerequisites](deviceportable-testing-prerequisites.md).

The MTP device should be active and plugged in before commencing the test. The tool Mtpinfup.exe will update the driver for the attached MTP device to a signed test .inf file Mtptest.inf. Upon completion of the test, Mtpinfup.exe will update the driver back to the original in-box driver Wpdmtp.inf. If an optional capability is not supported by the device, the test will skip that test case.

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](../user/troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see [Troubleshooting Device.Portable Testing](troubleshooting-deviceportable-testing.md).

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


This test requires that a MTP-compatible device is installed. The test is fully automated with Pass/Fail results for each requirement.

This test is divided into the following functional categories:

-   Device Capabilities tests

-   Operations tests

-   Device Properties

-   Object Property tests

Each of the functional categories mentioned above contain child test cases, testing the sub components that fall under the corresponding category.

The test will validate that the following Operations are supported by the device:

-   OpenSession

-   CloseSession

-   GetDeviceInfo

-   GetStorageIDs

-   GetStorageInfo

-   GetObject

-   GetDevicePropDesc

-   GetDevicePropValue

-   SetDevicePropValue

-   DeleteObject

-   SendObject

-   GetNumObjects

-   GetObjectHandles

-   GetObjectInfo

-   SendObjectInfo

-   GetPartialObject

-   GetObjectPropsSupported

-   GetObjectPropDesc

-   GetObjectPropValue

-   SetObjectPropValue

-   GetObjectReferences

-   SetObjectReferences

The test validates that the following device properties are supported:

-   Synchronization Partner

-   Device Friendly Name

The test validates that the following formats are supported:

-   Undefined

-   Association

-   AbstractAudioAlbum

-   AbstractAudioVideoPlaylist

For AbstractAudioAlbum, the following properties are verified:

-   Genre

-   AlbumArtist

The test validates that the following Object Properties are supported for each supported format:

1.  StorageID

2.  ObjectFormat

3.  ProtectionStatus

4.  ObjectSize

5.  ObjectFileName

6.  ParentObject

7.  PersistentUniqueObjectIdentifier

8.  Name

9.  Non-Consumable

For supported Image formats, the test looks for these additional Object Properties:

-   Width

-   Height

For supported Video formats, the test looks for these additional Object Properties:

-   Width

-   Height

-   SampleRate

-   NumberOfChannels

-   ScanType

-   Audio WAVE CODEC

-   AudioBitRate

-   VideoFourCCCodec

-   VideoBitrate

-   Frames PerThousand Second

-   Encoding Profile

For supported Audio formats, the test looks for these additional Object Properties:

-   Artist

-   Track

-   AlbumName

-   AlbumArtist

-   SampleRate

-   NumberOfChannels

-   AudioBitRate

-   AudioWaveCodec

All other supported operations, device properties, and object properties are considered optional and therefore will be validated according to implementation details defined in the Picture Transfer Protocol (PTP) for Digital Still Photography Devices, Version 1.0 (PIMA15740) and Media Transfer Protocol (MTP), Revision 1.0.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Run time:</strong></p></td>
<td><p>Test duration depends on the number of supported capabilities, formats, and operations. Run time can vary up to 2 hours.</p></td>
</tr>
<tr class="even">
<td><p><strong>Log file:</strong></p></td>
<td><p>WTTTestLog.xml</p></td>
</tr>
<tr class="odd">
<td><p><strong>System restart required:</strong></p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p><strong>Test category:</strong></p></td>
<td><p>Portable Media Player</p></td>
</tr>
<tr class="odd">
<td><p><strong>Program:</strong></p></td>
<td><p>MtpTest.exe</p></td>
</tr>
</tbody>
</table>



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
<td><p><strong>te.exe /p:&quot;BVT=TRUE&quot; MtpTest.dll /select(<xref href="name=" data-throw-if-not-resolved="False" data-raw-source="@name="></xref>&#39;<xref href="CapabilitiesTests*" data-throw-if-not-resolved="False" data-raw-source="@CapabilitiesTests*"></xref>&#39;) /p &quot;DeviceProfile=MtpMediaPlayer.xml&quot;</strong></p></td>
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
<td><p>Mtptest.dll</p></td>
<td><p><em>&lt;testbinroot&gt;</em>\mtp&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>MtpMediaPlayer.xml</p></td>
<td><p><em>&lt;testbinroot&gt;</em>\mtp&lt;/p&gt;</td>
</tr>
</tbody>
</table>



### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name     | Parameter description |
|--------------------|-----------------------|
| **WDKDeviceID**    |                       |
| **WpdTestDir**     |                       |
| **TaefTestFile**   |                       |
| **TaefParameters** |                       |
| **TestParameters** |                       |
| **TestSelect**     |                       |












