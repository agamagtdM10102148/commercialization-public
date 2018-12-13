---
title: LAN CS Test - IPv4 Basic
description: LAN CS Test - IPv4 Basic
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 819b87c1-b150-46d5-bb6e-0997c0fa1caa
author: dawn.wood
ms.author: dawnwood
ms.date: 11/05/2018
ms.topic: article


---

# <span id="p_hlk_test.b5aaba9b-cdfc-4d7d-8a7d-94ed3f5868c3"></span>LAN CS Test - IPv4 Basic


This test verifies that the LAN device on systems that support InstantGo delivers reliable connectivity in Connected Standby.

The device seamlessly transitions between D0 and D2 states while in Connected Standby. The device maintains L2 connectivity while in Connected Standby. The device wakes up on matching wake patterns only. There are no spurious wakes while in Connected Standby. The wake packets are delivered without delay or buffering. The Real Time Communication app stays connected while in Connected Standby for 30 minutes.

## Test details

|||
|---|---|
| **Specifications**  | <ul><li>Device.Network.LAN.CS.ReliableCSConnectivity</li></ul> |  
| **Platforms**   | <ul><li>Windows 10, client editions (x86)</li><li>Windows 10, client editions (x64)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li><li>Windows 10, version 1803</li><li>Next update to Windows 10</li></ul> |
|**Expected run time (in minutes)**| 30 |
|**Category**| Development |
|**Timeout (in minutes)**| 1800 |
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

If you are still having problems completing this test, try the following:

-   If the device exits Connected Standby earlier than expected, make sure the device under test remains idle while the test runs.

-   If you get a system error for a control channel trigger, ensure that the network adapter is compatible with Connected Standby and it complies with NDIS 6.30 requirements.

-   If the OID request for a network adapter fails, ensure that the network adapter complies with NDIS 6.30 requirements.

-   If the network device removes unexpectedly, ensure that the driver is not crashing.

-   If the control channel trigger is detached, ensure that there is good reception and that the network adapter maintains L2 connectivity in Connected Standby.

-   If the network adapter disconnects, ensure that there is good reception.

-   If the push notification is triggered too early, ensure that the network adapter complies with NDIS 6.30 requirements and that the network adapter maintains L2 connectivity in Connected Standby.

-   If the push notification is triggered too late, ensure that the network adapter complies with NDIS 6.30 requirements and that the network adapter maintains L2 connectivity in Connected Standby.

-   If the push notification did not trigger on time, ensure that the network adapter complies with NDIS 6.30 requirements and that the network adapter maintains L2 connectivity in Connected Standby.

-   If you cannot install the package, ensure that the device under test is configured with the correct date and time. For more information, check the error description.

## <span id="More_information"></span><span id="more_information"></span><span id="MORE_INFORMATION"></span>More information


### <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters

| Parameter name            | Parameter description |
|---------------------------|-----------------------|
| **queryTestDeviceID**     |                       |
| **TestInterfaceIndex**    |                       |
| **TestDeviceStaticIP**    |                       |
| **SupportInterfaceIndex** |                       |
| **SupportDeviceStaticIP** |                       |
| **CsDuration**            |                       |












