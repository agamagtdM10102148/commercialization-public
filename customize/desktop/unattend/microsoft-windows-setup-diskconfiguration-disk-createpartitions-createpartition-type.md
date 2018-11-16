---
title: Type
description: Type
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 83d8831d-fd39-469c-b8dc-c00077a61086
ms.mktglfcycl: deploy
ms.sitesec: msdn
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---
# Type

`Type` specifies the type of partition to create.

## Values

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Primary</strong></p></td>
<td><p>Creates a primary partition type.</p>
<p>A standard master boot record (MBR)-based hard disk can contain up to four primary partitions or three primary partitions and one extended partition. The extended partition can include additional logical drives.</p>
<p>A GUID partition table (GPT)-based hard disk can contain up to 128 primary partitions.</p>
<p>Windows must be installed on either a primary or a logical partition.</p></td>
</tr>
<tr class="even">
<td><p><strong>EFI</strong></p></td>
<td><p>Creates an extensible firmware interface (EFI) partition type.</p>
<p>The EFI partition type configures the partition as an EFI system partition (ESP). This is a required partition for a GUID partition table (GPT)-based disk.</p>
<p>Only a single EFI system partition is required, regardless of how many GPT-based disks exist on a system. For unattended installations, it is possible to create more than one ESP on a hard disk. If there is already an ESP on the hard disk to which you are installing, and you create a new ESP in your answer file, two ESPs will be present on the computer. Two ESPs might be problematic for users, and they will consume additional disk space.</p>
<p>We recommend that you use the <a href="microsoft-windows-setup-diskconfiguration-disk-willwipedisk.md" data-raw-source="[WillWipeDisk](microsoft-windows-setup-diskconfiguration-disk-willwipedisk.md)">WillWipeDisk</a> setting to erase all partitions on the disk before performing an unattended installation.</p>
<p>In attended installations, Windows Setup warns you that an ESP already exists on the hard disk.</p>
<p>Installation will be terminated if you specify Type as EFI and the format of the disk is of type MBR. Only GPT disks can have an EFI System partition.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Extended</strong></p></td>
<td><p>Specifies that the partition is an extended partition.</p>
<p>An extended partition can be created only on master boot record (MBR)-based disks.</p>
<p>Only one extended partition can exist on a single disk. If an extended partition already exists on the disk, a second extended partition is not created. If the value for the <a href="microsoft-windows-setup-diskconfiguration-willshowui.md" data-raw-source="[WillShowUI](microsoft-windows-setup-diskconfiguration-willshowui.md)">WillShowUI</a> setting is set to <strong>Never</strong>, an error is logged, and installation is terminated.</p>
<p>Extended partitions are useful if you intend to create more than four volumes on a basic MBR disk. Unlike primary partitions, you do not format an extended partition with a file system. Instead, you create one or more logical drives within the extended partition.</p></td>
</tr>
<tr class="even">
<td><p><strong>Logical</strong></p></td>
<td><p>Specifies that the partition is a logical partition.</p>
<p>Windows 7 must be installed on either a primary or a logical partition.</p>
<p>A logical partition is a volume that is created inside an extended partition on a basic master boot record (MBR)-based disk.</p>
<p>Logical partitions are similar to primary partitions. However, while only four primary partitions can exist on a single disk, the number of logical partitions that can exist on a disk is unlimited. A logical partition can be formatted and assigned a drive letter.</p>
<p>A logical partition must be created inside an extended partition. If an extended partition does not already exist on the disk or the specified size of the logical drive exceeds the extended partition, no partition is created.</p>
<p>If <a href="microsoft-windows-setup-diskconfiguration-willshowui.md" data-raw-source="[WillShowUI](microsoft-windows-setup-diskconfiguration-willshowui.md)">WillShowUI</a> is set to <strong>Never</strong>, an error is logged, and installation is terminated.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MSR</strong></p></td>
<td><p>Specifies that the partition is a Microsoft reserved (MSR) partition.</p>
<p>The MSR partition type is a required partition for GUID partition table (GPT)-based disks.</p>
<p>The size of the MSR partition varies. For GPT disks that are smaller than 16 GB, the size of the MSR partition is 32 MB. For disks larger than 16 GB, the MSR partition is 128 MB.</p>
<p>If an MSR partition already exists on the same disk, or the format of the disk is MBR, no partition is created. If the value for <a href="microsoft-windows-setup-diskconfiguration-willshowui.md" data-raw-source="[WillShowUI](microsoft-windows-setup-diskconfiguration-willshowui.md)">WillShowUI</a> is set to <strong>Never</strong>, an error is logged and the installation is terminated.</p>
<p>If an ESP is not detected or an MSR partition does not exist on each GPT disk in the system, no GPT-related disk configurations can be created.</p></td>
</tr>
</tbody>
</table>

> [!Note]
> For information about setting other types of partitions, such as utility and recovery partitions, see Microsoft-Windows-Setup/DiskConfiguration/Disk/ModifyPartitions/ModifyPartition/[TypeID](microsoft-windows-setup-diskconfiguration-disk-modifypartitions-modifypartition-typeid.md).

This string type does not support empty elements. Do not create an empty value for this setting.

## Valid Configuration Passes

windowsPE

## Parent Hierarchy

[Microsoft-Windows-Setup](microsoft-windows-setup.md) | [DiskConfiguration](microsoft-windows-setup-diskconfiguration.md) | [Disk](microsoft-windows-setup-diskconfiguration-disk.md) | [CreatePartitions](microsoft-windows-setup-diskconfiguration-disk-createpartitions.md) | [CreatePartition](microsoft-windows-setup-diskconfiguration-disk-createpartitions-createpartition.md) | **Type**

## Applies To

For a list of Windows editions and architectures that this component supports, see [Microsoft-Windows-Setup](microsoft-windows-setup.md).

## XML Examples

The following XML output for the `DiskConfiguration` setting shows a configuration for a **UEFI-based** system with four partitions, including an EFI partition, an MSR partition, and two primary partitions.

For full XML examples and recommended partition configurations, see [How to Configure UEFI/GPT-Based Hard Disk Partitions](http://go.microsoft.com/fwlink/?LinkId=214261) or [How to Configure BIOS/MBR-Based Hard Disk Partitions](http://go.microsoft.com/fwlink/?LinkId=214260).

```XML
<DiskConfiguration>

  <Disk wcm:action="add">
    <DiskID>0</DiskID> 
    <WillWipeDisk>true</WillWipeDisk> 
    <CreatePartitions>

      <!-- Recovery partition -->
      <CreatePartition wcm:action="add">
        <Order>1</Order> 
        <Type>Primary</Type> 
        <Size>250</Size> 
      </CreatePartition>

      <!-- EFI system partition (ESP) -->
      <CreatePartition wcm:action="add">
        <Order>2</Order> 
        <Type>EFI</Type> 
        <Size>100</Size> 
      </CreatePartition>

      <!-- Microsoft reserved partition (MSR) -->
      <CreatePartition wcm:action="add">
        <Order>3</Order> 
        <Type>MSR</Type> 
        <Size>128</Size> 
      </CreatePartition>

      <!-- Windows partition -->
      <CreatePartition wcm:action="add">
        <Order>4</Order> 
        <Type>Primary</Type> 
        <Extend>true</Extend> 
      </CreatePartition>

    </CreatePartitions>
    <ModifyPartitions>

      <!-- Recovery partition -->
      <ModifyPartition wcm:action="add">
        <Order>1</Order> 
        <PartitionID>1</PartitionID> 
        <Label>Recovery</Label> 
        <Format>NTFS</Format> 
        <TypeID>de94bba4-06d1-4d40-a16a-bfd50179d6ac</TypeID> 
      </ModifyPartition>

      <!-- EFI system partition (ESP) -->
      <ModifyPartition wcm:action="add">
        <Order>2</Order>
        <PartitionID>2</PartitionID>
        <Label>System</Label>
        <Format>FAT32</Format>
      </ModifyPartition>

      <!-- MSR partition does not need to be modified -->

      <!-- Windows partition -->
      <ModifyPartition wcm:action="add">
        <Order>3</Order>
        <PartitionID>4</PartitionID>
        <Label>Windows</Label>
        <Letter>C</Letter>
        <Format>NTFS</Format>
      </ModifyPartition>

    </ModifyPartitions>
  </Disk>

  <WillShowUI>OnError</WillShowUI>

</DiskConfiguration>

<ImageInstall>
  <OSImage>
    <InstallTo>
      <DiskID>0</DiskID>
      <PartitionID>4</PartitionID>
    </InstallTo>
  </OSImage>
</ImageInstall>
```

## Related topics

[CreatePartition](microsoft-windows-setup-diskconfiguration-disk-createpartitions-createpartition.md)

[TypeID](microsoft-windows-setup-diskconfiguration-disk-modifypartitions-modifypartition-typeid.md)

[How to Configure More than Four Partitions on a BIOS-Based Hard Disk](http://go.microsoft.com/fwlink/?LinkId=214072)
