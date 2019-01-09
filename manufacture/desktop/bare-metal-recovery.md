---
author: kpacquer
Description: 'How bare-metal recovery features work'
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: 'How bare-metal recovery features work'
ms.author: kenpacq
ms.date: 12/20/2018
ms.topic: article

---

# Bare metal recovery

If the user needs to replace their hard drive or completely wipe it, they can use bootable recovery media to perform bare metal recovery. Bare metal recovery removes all existing partitions on the system disk and recreates all partitions, before restoring software onto the PC. Two types of recovery media are supported:

-   **[User-created recovery media](bare-metal-resetrecovery-enable-your-users-to-create-media-and-to-recover-hard-drive-space.md)** using the **Create a recovery drive** utility in Windows 10. This backs up the files needed to restore the PC to a pristine state.
-   **[Manufacturer-created recovery media](create-media-to-run-push-button-reset-features-s14.md)** for support and refurbishing scenarios by placing a recovery image on a piece of bootable Windows RE media.

**When user-created recovery media are used, the bare metal recovery feature can be summarized in the following steps:**

1.  The system disk is identified.
2.  All partitions from the system disk are removed.
3.  Data erasure is performed on the system disk (if requested by the user).
4.  Factory or default partition layout is recreated on the system disk.
5.  All partitions are formatted.
6.  Recovery files from recovery media are copied to the OS volume.
7.  A new copy of the OS is constructed at the root of the OS volume.
8.  Customizations stored in provisioning packages are applied.
9.  Drivers are injected into the new OS.
10. Preinstalled Windows apps are restored.
11. Boot files are configured on the system partition.
12. PC reboots to the new OS.
13. OOBE starts.

### <span id="Data_removal_options"></span><span id="data_removal_options"></span><span id="DATA_REMOVAL_OPTIONS"></span>Data removal options

When users use the bare metal recovery feature, they can choose to perform data erasure on the entire system disk before the factory partition layout is reapplied. On most PCs, this data erasure process is done in software, writing cryptographically random patterns to the entire LBA range of the system disk once.

However, on certain hardware configurations, the data erasure process is performed by the storage device’s hardware controller. This often takes less time to complete and is usually more thorough in removing remnant data. Hardware-based data erasure is supported on PCs with storage devices which meet the following criteria:

-   eMMC
-   Supports the **Secure Trim** and **Sanitize** commands

### <span id="System_disk_selection"></span><span id="system_disk_selection"></span><span id="SYSTEM_DISK_SELECTION"></span>System disk selection

Bare metal recovery automatically identifies the system disk using the following methods:

-   Adaptor location path and GUID of the system disk are written to a UEFI variable during OOBE.
    -   Performed only when both the system and Windows partitions are on the system disk.

    -   The variable is updated if necessary when Windows RE gets disabled and then re-enabled.

-   During bare metal recovery, if multiple internal disks are detected, the system disk is searched in this order:
    -   Disk with GUID matching the value stored in the UEFI variable.
    -   Disk with location path matching the value stored in firmware.
    -   Disk with an existing ESP.
        -   If multiple disks with ESP are found, bare metal recovery will not proceed.
    -   Uninitialized (raw) disk.
        -   If multiple uninitialized disks are found, bare metal recovery will not proceed.
-   On legacy BIOS/MBR systems, the BIOS-reported system disk is used.

### <span id="User-created_recovery_media"></span><span id="user-created_recovery_media"></span><span id="USER-CREATED_RECOVERY_MEDIA"></span>User-created recovery media

When users create USB recovery media using the **Create a recovery drive** utility, the resulting media always contain a bootable copy of Windows RE. This gives users access to troubleshooting and recovery tools when booting from recovery media.

Users can optionally back up files required to perform bare metal recovery. When the option is selected, the following are copied onto the USB recovery media as well:

-   Windows Component Store
-   Installed drivers
-   Backup of preinstalled Windows apps
-   Provisioning packages containing preinstalled customizations (under C:\\Recovery\\Customizations)
-   Push-button Reset configuration XML and scripts (under C:\\Recovery\\OEM)

### <span id="Manufacturer-created_recovery_media"></span><span id="manufacturer-created_recovery_media"></span><span id="MANUFACTURER-CREATED_RECOVERY_MEDIA"></span>Manufacturer-created recovery media

Bare metal recovery supports the use of a recovery WIM image when the media are prepared by manufacturers. This type of media is primarily used in support and refurbishing scenarios.

Manufacturer-created media must contain the following:

1.  A bootable Windows RE image.
2.  A Push-button reset-compatible recovery image (install.wim).
3.  A Push-button reset configuration file (Resetconfig.xml) which specifies disk partitioning information.
4.  A DISKPART script to perform partitioning of the disk.

## Let's set it up!
-   **[Bare metal reset/recovery: enable your users to create recovery media](bare-metal-resetrecovery-enable-your-users-to-create-media-and-to-recover-hard-drive-space.md)** using the **Create a recovery drive** utility in Windows 10. This backs up the files needed to restore the PC to a pristine state.
-   **[Bare metal reset/recovery: create recovery media while deploying new devices](create-media-to-run-push-button-reset-features-s14.md)** for support and refurbishing scenarios by placing a recovery image on a piece of bootable Windows RE media.

## Related topics
- [Push-button reset](push-button-reset-overview.md)
- [How push-button reset features work](how-push-button-reset-features-work.md)
 