---
author: dawnwood
Description: Factory Encrypted Drives
ms.assetid: 3469481b-f380-4585-87c8-ca8a267fe607
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: Factory Encrypted Drives
ms.author: justinha
ms.date: 06/18/2018
ms.topic: article


---

# Factory Encrypted Drives


You can install Windows on factory-encrypted drives, also known as encrypted hard disk drives (eHDD). A *factory-encrypted drive* is a drive that is capable of full-disk encryption.

By default, when you install Windows on a factory-encrypted drive, Windows automatically encrypts the drive by using Trusted Computing Group (TCG) and IEEE 1667 transport encryption standards.

## <span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Requirements


To install Windows onto a factory-encrypted drive, use the following:

1.  Firmware: UEFI version 2.3.1 that has been configured to use the EFI storage security protocol.

2.  Hardware: a hard disk drive that is capable of using TCG and IEEE 1667 transport encryption standards.

## <span id="Using_other_encryption_standards"></span><span id="using_other_encryption_standards"></span><span id="USING_OTHER_ENCRYPTION_STANDARDS"></span>Using other encryption standards


To use another encryption standard on your drive, you must first disable the automatic drive provisioning that Windows provides. To do this on a new installation, set the [Microsoft-Windows-EnhancedStorage-Adm/TCGSecurityActivationDisabled](https://docs.microsoft.com/en-us/windows-hardware/customize/desktop/unattend/microsoft-windows-enhancedstorage-adm-tcgsecurityactivationdisabled) Unattend setting to **true**. 

## <span id="related_topics"></span>Related topics

- [Windows 10 S security features and requirements for OEMs](https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-10s-security)
- [Hard Drives and Partitions](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/hard-drives-and-partitions)

 

 






