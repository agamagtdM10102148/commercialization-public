---
title: Audio Codec - Lullaby Test - Certification - Desktop
description: Audio Codec - Lullaby Test - Certification
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1dd9c51c-4c6c-4fcc-a9e8-fdb4b03a54b5
author: dawn.wood
ms.author: dawnwood
ms.date: 11/05/2018
ms.topic: article


---

# Audio Codec - Lullaby Test - Certification - Desktop


This automated test verifies audio during power-state transitions. The test plays audio before, during, and after transitions into sleep and hibernate power states to verify the integrity of the audio pipeline.

Specifically, the test uses the Microsoft® DirectSound® and Wave APIs to play audio, calls Advanced Configuration and Power Interface (ACPI) functions to put the computer into a low-power state, and awakens the computer by using a wait able timer event. The test then verifies that audio still plays correctly.

## Test details

|||
|---|---|
| **Specifications**  | <ul><li>Device.Audio.Base.PowerManagement</li><li>Device.Audio.Base.JackDetection</li><li>Device.Audio.Base.Endpoints</li><li>Device.Audio.HardwareAudioProcessing.AudioHardwareOffloading</li></ul> |  
| **Platforms**   | <ul><li>Windows 10, client editions (x86)</li><li>Windows 10, client editions (x64)</li><li>Windows Server 2016 (x64)</li><li>Windows 10, client editions (ARM64)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li><li>Windows 10, version 1803</li><li>Next update to Windows 10</li></ul> |
|**Expected run time (in minutes)**| 20 |
|**Category**| Development |
|**Timeout (in minutes)**| 1200 |
|**Requires reboot**| false |
|**Requires special configuration**| true |
|**Type**| automatic |



## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [Device.Audio additional documentation](device-audio-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [Audio Device Testing Prerequisites](audio-device-testing-prerequisites.md).

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](../user/troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see [Troubleshooting Audio Testing](troubleshooting-audio-testing.md).

The test returns FAIL if it does not detect an audio device, if it cannot set the power state of the computer, or if the audio pipeline is in an inconsistent state. For specific information about failures, review the test results in the generated log file.

Depending on BIOS, the test might require user intervention. If BIOS does not support wake from sleep and wake from hibernate, you must bring the computer out of sleep states for the test to continue.

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
<td><p><strong>Lullaby</strong></p></td>
<td><p>Without any options, the test opens the GUI.</p></td>
</tr>
<tr class="even">
<td><p><strong>-c [string]</strong></p></td>
<td><p>This option starts the application and runs the test cases that are specified in the .pro file that <strong>[string]</strong> specifies.</p></td>
</tr>
<tr class="odd">
<td><p><strong>-h [string]</strong></p></td>
<td><p>This option specifies the Plug and Play (PnP) ID of the device for the test cases to use. The default value is all devices.</p></td>
</tr>
</tbody>
</table>

> [!NOTE]
> 
> For command-line help for this test binary, type **/h**



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
<td><p>DevIDParse.vbs</p></td>
<td><p><em>&lt;testbinroot&gt;</em>\nttest\multimediatest \avcore\audio\scripts&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>Lullaby.exe</p></td>
<td><p><em>&lt;testbinroot&gt;</em>\nttest\multimediatest\avcore\audio\wdk</p></td>
</tr>
<tr class="odd">
<td><p>Logo_win7_lullaby.pro</p></td>
<td><p><em>&lt;testbinroot&gt;</em>\nttest\multimediatest\AVCore\Audio\Profiles&lt;/p&gt;</td>
</tr>
<tr class="even">
<td><p>Logo_vista_lullaby.pro</p></td>
<td><p><em>&lt;testbinroot&gt;</em>\nttest\multimediatest\AVCore\Audio\Profiles&lt;/p&gt;</td>
</tr>
<tr class="odd">
<td><p>S98wtt.dll</p></td>
<td><p><em>&lt;testbinroot&gt;</em>\nttest\multimediatest\common&lt;/p&gt;</td>
</tr>
</tbody>
</table>



### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name         | Parameter description                   |
|------------------------|-----------------------------------------|
| **LLU\_NetAccessOnly** | Name of machine's LLU for copying files |
| **TestExe**            | Name of test executable                 |
| **TestExePath**        | Partial path of the test executable     |
| **WDKDeviceID**        | Device ID string                        |
| **TestPro**            | Name of test profile                    |












