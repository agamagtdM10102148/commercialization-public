---

Description: 'Capture and Apply Windows, System, and Recovery Partitions'
ms.assetid: db1f011f-2cf3-46b7-a386-8333f6214b9e
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: 'Capture and Apply Windows, System, and Recovery Partitions'

ms.date: 05/02/2017
ms.topic: article


---

# Capture and Apply Windows, System, and Recovery Partitions

When capturing a Windows image using .WIM files, you usually can just capture the Windows partition, and then use files from that image to set up the rest of the partitions on the drive. See [Capture and Apply Windows using a single WIM file](capture-and-apply-windows-using-a-single-wim.md).

However, if you're using custom partitions, use this topic to learn more about the individual partititions to capture and apply.

## Capture the customized partitions

### Step 1: Determine which partitions to capture

This table shows the types of partitions that you must capture and those that are managed automatically.

If you're deploying both UEFI and BIOS systems, you can reuse your primary and logical partitions across UEFI-based and BIOS-based devices, but not the other partition types.

| Partition type | Should you capture this partition? | Can you reuse the same WIM on UEFI and BIOS firmware? |
| --- | --- | - |
| **System partition** (EFI System Partition or BIOS system partition) | Optional. If only a simple set of partition files is required, you don’t have to capture this partition. | No | 
| **Microsoft Reserved partition (MSR)** | No | No |
| **Primary partitions** (Windows partitions, data / utility partitions that you've added) | Yes | Yes |
| **Recovery partition** | Optional. If you haven't customized this partition, you don’t have to capture it. | No | 
| **Extended partition** | No | No |
| **Logical partitions** (Windows partitions, data / utility partitions that you've added) | Yes | Yes |

### Step 2: Prepare to capture partitions

1.  If you've booted the Windows image, generalize it so that it can be deployed to other devices. For more information, see [Sysprep (Generalize) a Windows installation](sysprep--generalize--a-windows-installation.md).

2.  Start your reference device by using Windows PE.

3.  At the Windows PE command prompt, type `diskpart` to open the DiskPart tool.

    ```
    X:> diskpart
    DISKPART>
    ```

4.  Check to see if the partitions that you want to capture have drive letters assigned. 

    ```
    DISKPART> list volume

      Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
      ----------  ---  -----------  -----  ----------  -------  ---------  --------
      Volume 0     C   Windows      NTFS   Partition    475 GB  Healthy    Boot
      Volume 1                      NTFS   Partition    554 MB  Healthy
      Volume 2         SYSTEM       FAT32  Partition    499 MB  Healthy    System
    ```

    If any of the partitions you want to capture don’t already have a drive letter assigned, continue:

5.  List the disks in your PC:

    ```
    DISKPART> list disk

    Disk ###  Status         Size     Free     Dyn  Gpt
    --------  -------------  -------  -------  ---  ---
    Disk 0    Online          127 GB      0 B        *
    ```

6.  Select the primary hard disk:

    ```
    DISKPART> select disk 0
    ```

7.  View the partitions:

    ```
    DISKPART> list partition

      Partition ###  Type              Size     Offset
      -------------  ----------------  -------  -------
      Partition 1    System             499 MB  1024 KB
      Partition 2    Reserved           128 MB   500 MB
      Partition 3    Primary            475 GB   628 MB
      Partition 4    Recovery           554 MB   476 GB
    ```

8.  Select a partition that needs a drive letter:

    ```
    DISKPART> select partition=1
    ```

9.  Assign a letter to the partition with the `assign letter` command. For example,

    ```
    DISKPART> assign letter=S
    ```

10. Type `exit` to return to the Windows PE command prompt.

    ```
    DISKPART> exit
    X:\>
    ```

For more information, see the DiskPart Help from the command line, or [Diskpart Command line syntax](http://go.microsoft.com/fwlink/?LinkId=128458).

### Step 3: Capture images for each customized partition.

-   At the Windows PE command prompt, capture each customized partition, for example:

    ```
    Dism /Capture-Image /ImageFile:C:\my-windows-partition.wim /CaptureDir:C:\ /Name:"My Windows partition"
    Dism /Capture-Image /ImageFile:C:\my-system-partition.wim /CaptureDir:S:\ /Name:"My system partition"
    ```

    For more information about using the DISM tool to capture an image, see [DISM Image Management Command-Line Options](dism-image-management-command-line-options-s14.md).

### Step 4: Save images to the network or another safe location.

1.  Connect an external drive, or connect to a safe network location, for example: 

    ```
    net use n: \\Server\Share
    ```

    If prompted, provide your network credentials.

2.  Copy the partitions to your network share. For example,

    ```
    md N:\Images\
    copy C:\my-windows-partition.wim N:\Images\
    copy C:\my-system-partition.wim N:\Images\
    ```

## Apply the images

### Step 1: Prepare to apply partitions

1.  Start your destination device by using Windows PE.

2.  Connect an external drive, or connect to a safe network location, for example: 

    ```
    net use n: \\Server\Share
    ```

    If prompted, provide your network credentials.

3.  Wipe the hard drive and create new partitions.

    To apply to multiple devices, we recommend saving the Diskpart commands into a script and running it on each new device.  For examples, see [Configure UEFI/GPT-Based Hard Drive Partitions](configure-uefigpt-based-hard-drive-partitions.md) or [Configure BIOS/MBR-Based Hard Drive Partitions](configure-biosmbr-based-hard-drive-partitions.md). Example:

    ``` 
    diskpart /s D:\CreatePartitions-UEFI.txt
    ```
    Where D: is a USB flash drive or other file storage location.

    In these **DiskPart** examples, the partitions are assigned the letters: System=S, Windows=W, and Recovery=R.

    We recommend changing the Windows drive letter to a letter that’s near the end of the alphabet, such as W, to avoid drive letter conflicts. Do not use X, because this drive letter is reserved for Windows PE. After the device reboots, the Windows partition is assigned the letter C, and the other partitions don’t receive drive letters.

    If you reboot, Windows PE reassigns disk letters alphabetically, starting with the letter C, without regard to the configuration in Windows Setup. This configuration can change based on the presence of different drives, such as USB flash drives.

4.  Optional: speed up the image capture by setting the power scheme to High performance:

    ```
    powercfg /s 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c
    ```

### Step 2: Apply the partitions

1.  **Windows and data partitions:** Apply the image(s), example:

    ```
    dism /Apply-Image /ImageFile:N:\Images\my-windows-partition.wim /Index:1 /ApplyDir:W:\
    ```

    where W: is the Windows partition.

2.  **System partition:** You can either:
    
    * Configure the system partition by using the BCDBoot tool. This tool copies and configures system partition files by using files from the Windows partition. For example:

      ```
      W:\Windows\System32\bcdboot W:\Windows /s S:
      ```

      or:

    * Apply a custom image

      ```
      dism /Apply-Image /ImageFile:N:\Images\my-system-partition.wim /Index:1 /ApplyDir:S:\
      ```

      Where S: is the system partition

2.  **Recovery partition:** 

    a. You can either:
    
       * Copy the Windows Recovery Environment (RE) tools into the recovery tools partition.

         ```
         md R:\Recovery\WindowsRE
         copy W:\Windows\System32\Recovery\winre.wim R:\Recovery\WindowsRE\winre.wim
         ```

         Where R: is the recovery partition

     or:

       * Apply a custom image

         ```
         dism /Apply-Image /ImageFile:N:\Images\my-recovery-partition.wim /Index:1 /ApplyDir:R:\
         ```

    b. Register the location of the recovery tools, and hide the recovery partition using Diskpart. You can use our [sample script](windows-deployment-sample-scripts.md#create-recovery-partitions) or perform the steps manually:

       ```
       W:\Windows\System32\reagentc /setreimage /path R:\Recovery\WindowsRE /target W:\Windows
       ```

       Diskpart steps for UEFI: 
       
       ```
       set id="de94bba4-06d1-4d40-a16a-bfd50179d6ac"
       gpt attributes=0x8000000000000001
       ```

       Diskpart steps for BIOS:
       ```
       set id=27
       ```

### Step 3: Verify that it worked

Reboot the device (`exit`). Windows should boot.

> [!Note]
> If the device doesn't boot, (for example, if you receive the error message: **Bootmgr not found. Press CTRL+ALT+DEL**) check the steps for setting up the system partition:
> - See [BCDBoot command-line options](bcdboot-command-line-options-techref-di.md) for more info about copying boot files to the system partition.
> - Use the DiskPart tool to check to make sure that the system partition is set to Active.

Complete the out of box experience (OOBE) as a new user, and check the recovery partition:

* Check that in File Explorer that the Recovery partition is not visible.

* View the partitions exist, either by right-clicking **Start** and selecting **Disk Management**, or by using diskpart (Open a command prompt as an administrator > `diskpart` > `select disk 0` > `list partition` > `exit`).

## <span id="related_topics"></span>Related topics

[Configure UEFI/GPT-Based Hard Drive Partitions](configure-uefigpt-based-hard-drive-partitions.md)

[Configure BIOS/MBR-Based Hard Drive Partitions](configure-biosmbr-based-hard-drive-partitions.md)

[BCDboot Command-Line Options](bcdboot-command-line-options-techref-di.md)

[REAgentC Command-Line Options](reagentc-command-line-options.md)
