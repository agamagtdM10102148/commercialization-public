---
title: BitLocker Tpm And Recovery Password tests for AOAC devices with PCR\7\
description: BitLocker Tpm And Recovery Password tests for AOAC devices with PCR\ 7\
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 0166773e-eeef-4089-8936-34b1fa91b293
author: dawn.wood
ms.author: dawnwood
ms.date: 11/05/2018
ms.topic: article


---

# BitLocker Tpm And Recovery Password tests for AOAC devices with PCR\[7\]


All platforms that implement a TPM must ensure invariance of PCRs 7, 11 across power cycles in the absence of changes to the platform's static core root of trust for measurements (SRTM). Attaching a (non-bootable) USB to the platform or attaching the platform to a docking station should not cause changes to the SRTM.

> [!NOTE]
> 
> This test restarts the system multiple times to check whether PCRs are consistent.



## Test details

|||
|---|---|
| **Specifications**  | <ul><li>System.Fundamentals.TPM.CS.ConnectedStandby</li><li>Device.DevFund.Firmware.UpdateDriverPackage</li></ul> |  
| **Platforms**   | <ul><li>Windows 10, client editions (x86)</li><li>Windows 10, client editions (x64)</li><li>Windows 10, client editions (ARM64)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li><li>Windows 10, version 1803</li><li>Next update to Windows 10</li></ul> |
|**Expected run time (in minutes)**| 15 |
|**Category**| Scenario |
|**Timeout (in minutes)**| 900 |
|**Requires reboot**| false |
|**Requires special configuration**| false |
|**Type**| automatic |



## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [Device.DevFund additional documentation](device-devfund-additional-documentation.md)
-   [System.Fundamentals additional documentation](system-fundamentals-additional-documentation.md)

## <span id="Running_the_test"></span><span id="running_the_test"></span><span id="RUNNING_THE_TEST"></span>Running the test


Before you run the test, complete the test setup as described in the test requirements: [WDTF System Fundamentals Testing Prerequisites](wdtf-system-fundamentals-testing-prerequisites.md). Also, check that TPM is on and ready for use by running tpm.msc (the Trusted Platform Module (TPM) Management snap-in). Secure boot should be enabled.

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](../user/troubleshooting-windows-hlk-test-failures.md).

For troubleshooting information, see [Troubleshooting System Fundamentals Testing](troubleshooting-system-fundamentals-testing.md).

If this test fails, review the test log from Windows Hardware Lab Kit (Windows HLK) Studio.

1.  Make sure you can see **fveapi.dll** in **%systemroot%\\system32\\**.

2.  Check test output directly from command prompt when the test runs or open te.wtl in the HLK Manager.

3.  If a test script fails, check the BitLocker status:

    -   Manage-bde -status \[volume\]

4.  Collect BitLocker event logs from event viewer at two locations:

    -   Filter **\\Windows logs\\System** logs by event sources started with BitLocker

    -   **Applications and Services Logs\\Microsoft\\Windows\\BitLocker-API\\Management**

5.  Run **tpm.msc ** to ensure that the TPM Status is ON and that ownership has been taken.

6.  Check TCG logs

    -   Collect TCG log (\*.txt).

    -   Compare multiple copies of the TCG log and see whether PCR \[0, 2, 4, 11\] are consistent across reboot and hibernate.

> [!NOTE]
> 
> If the BitLocker WHLK test results in a recovery event, the BitLocker recovery key is 48-zeros (0000-0000-0000-0000-0000-0000-0000-0000-0000-0000-0000-0000).












