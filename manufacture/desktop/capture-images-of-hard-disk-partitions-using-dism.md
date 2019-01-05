---
author: kpacquer
Description: Capture WIM Images of Hard Disk Partitions Using DISM
ms.assetid: 164b9185-402f-4afb-bcf5-ef2f37077ed6
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: Capture Images of Hard Disk Partitions Using DISM
ms.author: kenpacq
ms.date: 05/02/2017
ms.topic: article

redirect_url: https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/capture-and-apply-using-a-single-wim.md
---
<!--

# Capture Images of Hard Disk Partitions Using WIM files

When capturing a Windows image using .WIM files, you usually can just capture the Windows partition, and then use files from that image to set up the rest of the partitions on the drive. See [Capture and Apply Windows, System, and Recovery Partitions](capture-and-apply-windows-system-and-recovery-partitions.md).

However, if you're using custom partitions, use this topic to learn more about the individual partititions to capture and apply.

## <span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Prerequisites

1.  Windows PE. See [WinPE: Create USB Bootable drive](winpe-create-usb-bootable-drive.md).

2.  A reference computer. You can create a reference computer by deploying Windows, and then removing the computer-specific information from the system. For more information, see [Sysprep (Generalize) a Windows installation](sysprep--generalize--a-windows-installation.md).

## Step 1: Determine which partitions to capture

This table shows the types of partitions that you must capture and those that are managed automatically.

If you're deploying both UEFI and BIOS systems, you can reuse your primary and logical partitions across UEFI-based and BIOS-based devices, but not the other partition types.

| Partition type | Should you capture this partition? | Reuse across UEFI and BIOS systems? |
| --- | --- |
| **System partition** (EFI System Partition or BIOS system partition) | Optional. If only a simple set of partition files is required, you don’t have to capture this partition. | No | 
| **Microsoft Reserved partition (MSR)** | No | No |
| **Primary partitions** (Windows partitions, utility partitions that you've added) | Yes | Yes |
| **Extended partition** | No | No |
| **Logical partitions** (Windows partitions, utility partitions that you've added) | Yes | Yes |

## Step 2: Assign drive letters to partitions

If any of the partitions you want to capture don’t already have a drive letter assigned, assign a letter using the **DiskPart** tool.

1.  Start your reference computer by using Windows PE.

2.  At the Windows PE command prompt, type `diskpart` to open the DiskPart tool.

    ```
    X:> diskpart
    DISKPART>
    ```

3. View the disks in your PC with the `list disk` command. For example,

    ```
    DISKPART> list disk

    Disk ###  Status         Size     Free     Dyn  Gpt
    --------  -------------  -------  -------  ---  ---
    Disk 0    Online          127 GB      0 B        *
    ```

4.  Select the hard disk with the `select disk` command. For example,

    ```
    DISKPART> select disk 0
    ```

5.  View the partitions with the `list partition` command. For example,

    ```
    DISKPART> list partition

      Partition ###  Type              Size     Offset
      -------------  ----------------  -------  -------
      Partition 1    Recovery           300 MB  1024 KB
      Partition 2    System             100 MB   451 MB
      Partition 3    Reserved            16 MB   551 MB
      Partition 4    Primary            126 GB   567 MB
    ```

6.  Select the partition with the `select partition` command. For example,

    ```
    DISKPART> select partition=2
    ```

7.  Assign a letter to the partition with the `assign letter` command. For example,

    ```
    DISKPART> assign letter=S
    ```

8.  Type `exit` to return to the Windows PE command prompt.

    ```
    DISKPART> exit
    X:\>
    ```

For more information, see the DiskPart Help from the command line, or [Diskpart Command line syntax](http://go.microsoft.com/fwlink/?LinkId=128458).

## Step 3: Capture partitions

Capture images for each customized partition.

-   At the Windows PE command prompt, capture the images by using the **DISM** command together with the **/CaptureImage** option. For example,

    ```
    Dism /Capture-Image /ImageFile:c:\my-windows-partition.wim /CaptureDir:C:\ /Name:"My Windows partition"
    Dism /Capture-Image /ImageFile:s:\my-system-partition.wim /CaptureDir:S:\ /Name:"My system partition"
    ```

    For more information about using the DISM tool to capture an image, see [DISM Image Management Command-Line Options](dism-image-management-command-line-options-s14.md).

## Step 4: Save images to the network or another safe location.

1.  Connect an external drive, or connect to a safe network location, for example: 

    ```
    net use n: \\Server\Share
    ```

    If prompted, provide your network credentials.

2.  Copy the partitions to your network share. For example,

    ```
    md N:\Images\
    copy C:\my-windows-partition.wim N:\Images\
    copy c:\my-system-partition.wim N:\Images\
    ```

## <span id="Next_Steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Next Steps


After the image is captured and stored, you can:

-   Mount it to your reference computer for modification. For more information, see [Mount and Modify a Windows Image Using DISM](mount-and-modify-a-windows-image-using-dism.md).

-   Split the file into smaller files. For more information, see [Split a Windows Image (WIM) File to Span Across Multiple DVDs](split-a-windows-image--wim--file-to-span-across-multiple-dvds.md).

-   Apply the images to a destination computer. For more information, see [Apply Images Using DISM](apply-images-using-dism.md).

-   Service the image. For more information, see [Service a Windows Image Using DISM](service-a-windows-image-using-dism.md).

## <span id="related_topics"></span>Related topics


[Deployment Image Servicing and Management (DISM) Command-Line Options](deployment-image-servicing-and-management--dism--command-line-options.md)

[BCDboot Command-Line Options](bcdboot-command-line-options-techref-di.md)

[Capture and Apply Windows, System, and Recovery Partitions](capture-and-apply-windows-system-and-recovery-partitions.md)

[Boot to VHD (Native Boot): Add a Virtual Hard Disk to the Boot Menu](boot-to-vhd--native-boot--add-a-virtual-hard-disk-to-the-boot-menu.md)

-->
