---
title: LoadGen Server Stress - Run Last - Reset Machine Policies
description: LoadGen Server Stress - Run Last - Reset Machine Policies
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 44b82c4a-5467-40a8-9a6f-f3943bca79df
author: dawn.wood
ms.author: dawnwood
ms.date: 11/05/2018
ms.topic: article


---

# <span id="p_hlk_test.8cb4f87c-d2a4-4d90-92a7-edd016ccdeac"></span>LoadGen Server Stress - Run Last - Reset Machine Policies


This automated test resets the machine policies that are used by the test on the test computers in the machine pool.

> [!NOTE]
> 
> This test should be run after all other tests are finished.



This test job completes the following actions:

1.  RunJob - ReSet the policies on SUT

2.  Reset AutoLogon on SUT

3.  Reboot SUT

4.  Reset AutoLogon on MC

5.  RunJob - ReSet the policies on MC

6.  Reboot MC

7.  Remove stressclients dimension on MC

## Test details

|||
|---|---|
| **Specifications**  | <ul><li>System.Server.SystemStress.ServerStress</li><li>System.Server.FaultTolerant.Core</li><li>System.Server.SVVP.SVVP</li></ul> |  
| **Platforms**   | <ul><li>Windows Server 2016 (x64)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li><li>Windows 10, version 1803</li><li>Next update to Windows 10</li></ul> |
|**Expected run time (in minutes)**| 30 |
|**Category**| Scenario |
|**Timeout (in minutes)**| 1800 |
|**Requires reboot**| false |
|**Requires special configuration**| false |
|**Type**| automatic |



## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [System.Server additional documentation](system-server-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [System Server Testing Prerequisites](system-server-testing-prerequisites.md) and [Test Server Configuration](test-server-configuration.md). This test should be run after all other tests are finished.

1.  Navigate to the **Tests** tab
2.  Select **LoadGen Server Stress - Run Last - Reset Machine Policies**
3.  Click the **Run Selected** link
4.  In the **Schedule** dialog, map machines to roles
    -   Use the **Role** dropdown to select machines for the MC and SC roles (SUT will be prepopulated)
5.  Click **OK** to schedule the test

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](../user/troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see [Troubleshooting System Server Testing](troubleshooting-system-server-testing.md).










