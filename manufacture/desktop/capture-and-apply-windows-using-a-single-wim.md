---
author: kpacquer
Description: 'Capture and apply Windows using a single WIM file'
ms.assetid: db1f011f-2cf3-46b7-a386-8333f6214b9e
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: 'Capture and Apply Windows using a WIM file'
ms.author: kenpacq
ms.date: 1/07/2019
ms.topic: article

---

# Capture and apply a Windows image using a single .WIM file

Capture a Windows image (.WIM) file and use it to deploy Windows to new devices.

You can start with either the install.wim file from a Windows distribution ISO, or you can generalize and capture a running Windows image into a .WIM file. 

WIM files only capture a single partition. You can usually capture just the Windows partition, and then use files from that image to set up the rest of the partitions on the drive. If you've created a custom partition configuration, see [Capture and Apply Windows, System, and Recovery Partitions](capture-and-apply-windows-system-and-recovery-partitions.md).

![Diagram showing a new computer with an empty hard drive, plus a single .wim image file, expands to become multiple configured partitions](images/dep-adk-partitions-uefi-overview-capture-windows.jpg)

## Capture the image**

1.  If you've booted into Windows, generalize the image so that it can be deployed to other devices. For more information, see [Sysprep (Generalize) a Windows installation](sysprep--generalize--a-windows-installation.md).

2.  Boot the device using [Windows PE](winpe-intro.md).

3.  Capture the Windows partition. For example:

    ```
    Dism /Capture-Image /ImageFile:"D:\Images\Fabrikam.wim" /CaptureDir:C:\ /Name:Fabrikam
    ```

    Where D: is a USB flash drive or other file storage location.

## Apply the image

1.  Boot the device using [Windows PE](winpe-intro.md).

2.  Wipe the hard drive and set up new hard disk partitions using a [script](windows-deployment-sample-scripts-sxs.md#-createpartitions-uefitxt
). Use [CreatePartitions-UEFI.txt](configure-uefigpt-based-hard-drive-partitions.md) (or [CreatePartitions-BIOS.txt](configure-biosmbr-based-hard-drive-partitions.md) for older, legacy BIOS devices).

    ```
    diskpart /s CreatePartitions-UEFI.txt
    ```

3.  Apply the images using a [script](windows-deployment-sample-scripts-sxs.md#applyimagebat). 

    ```
    D:\ApplyImage.bat D:\Images\Fabrikam.wim
    ```


    Sample script:

    ```batch
    rem == ApplyImage.bat ==

    rem == These commands deploy a specified Windows
    rem    image file to the Windows partition, and configure
    rem    the system partition.

    rem    Usage:   ApplyImage WimFileName 
    rem    Example: ApplyImage E:\Images\ThinImage.wim ==

    rem == Set high-performance power scheme to speed deployment ==
    call powercfg /s 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c

    rem == Apply the image to the Windows partition ==
    dism /Apply-Image /ImageFile:%1 /Index:1 /ApplyDir:W:\

    rem == Copy boot files to the System partition ==
    W:\Windows\System32\bcdboot W:\Windows /s S:

    :rem == Copy the Windows RE image to the
    :rem    Windows RE Tools partition ==
    md R:\Recovery\WindowsRE
    xcopy /h W:\Windows\System32\Recovery\Winre.wim R:\Recovery\WindowsRE\

    :rem == Register the location of the recovery tools ==
    W:\Windows\System32\Reagentc /Setreimage /Path R:\Recovery\WindowsRE /Target W:\Windows

    :rem == Verify the configuration status of the images. ==
    W:\Windows\System32\Reagentc /Info /Target W:\Windows
    ```

## Related topics

[Deploy Windows using Full Flash Update (FFU)](deploy-windows-using-full-flash-update--ffu.md)

[Capture and Apply Windows, System, and Recovery Partitions](capture-and-apply-windows-system-and-recovery-partitions.md)

[Configure UEFI/GPT-Based Hard Drive Partitions](configure-uefigpt-based-hard-drive-partitions.md)

[Configure BIOS/MBR-Based Hard Drive Partitions](configure-biosmbr-based-hard-drive-partitions.md)

[BCDboot Command-Line Options](bcdboot-command-line-options-techref-di.md)

[REAgentC Command-Line Options](reagentc-command-line-options.md)
