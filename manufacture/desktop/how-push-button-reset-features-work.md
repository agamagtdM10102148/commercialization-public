---

Description: 'How push-button reset features work'
ms.assetid: 86c93069-916c-4c94-8ba8-2fbf0d792a36
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: 'How push-button reset features work'

ms.date: 05/02/2017
ms.topic: article
ms.custom: RS5

---

# <span id="How_push-button_reset_features_work"></span>How push-button reset features work


## <span id="Restoring_the_operating_system_and_customizations"></span><span id="restoring_the_operating_system_and_customizations"></span><span id="RESTORING_THE_OPERATING_SYSTEM_AND_CUSTOMIZATIONS"></span>Restoring the operating system and customizations

This section discusses the mechanisms Push-button reset uses to restore software on the PC.

### <span id="Restoring_Windows"></span><span id="restoring_windows"></span><span id="RESTORING_WINDOWS"></span>Restoring Windows

Push-button reset restores Windows 10 by constructing a new copy of the OS using runtime system files located in the Windows Component Store (C:\\Windows\\WinSxS). This allows recovery to be possible even without a separate recovery image containing a backup copy of all system files.

In addition, Push-button reset restores Windows to an updated state rather than to the factory-preinstalled state. All updates installed on the PC (such as Windows 10, version 1809) will be restored.  Due to this improvement it is not required nor recommended to mark updates as permanent by using the DISM /Cleanup-Image command with the /ResetBase option.

This approach provides a balance between user experience in terms of the number of updates which need to be reinstalled and the features’ effectiveness in addressing update problems. It also allows Windows to remove older system files which are no longer needed for runtime use or for recovery, freeing up disk space.

### <span id="Restoring_language_packs"></span><span id="restoring_language_packs"></span><span id="RESTORING_LANGUAGE_PACKS"></span>Restoring language packs

Language packs that are installed and used by at least one user account are restored. This includes languages installed by users.

Seven days after the Out-of-Box Experience (OOBE), any language packs that haven't yet been used are removed. Using Push-button reset features after that will not restore the removed language packs.

On PCs running single-language editions of Windows, such as Windows 10 Home, users cannot download or install additional language packs, and they cannot use push-button reset features to switch languages if the preinstalled language packs have been removed.

### <span id="Restoring_drivers"></span><span id="restoring_drivers"></span><span id="RESTORING_DRIVERS"></span>Restoring drivers

Drivers are restored in a similar fashion as the OS. Instead of restoring them from a recovery image, existing drivers are preserved across recovery. As with system files, drivers are restored to the state they were in when the most recent release or major update is installed. For example:

-   If the customer performs recovery after booting up a new PC preinstalled with Windows 10, drivers that are present during OOBE will be restored, even if newer drivers have been installed since.
-   If the customer performs recovery after upgrading from Windows 10 to Windows 10, version 1511, the drivers that are present during the upgrade will be restored, even if newer drivers have been installed since.

Device applets which are installed outside of the driver INF package are not restored as part of this process. They are restored to factory version and state in the same way as other customizations such as Windows desktop applications. (See Restoring other customizations for more information.) If the device applet must always stay in sync (version wise) with the driver, it is recommended that both the driver and the device applet be installed via the same INF package.

### <span id="Restoring_previously_installed_Windows_apps"></span><span id="restoring_previously_installed_windows_apps"></span><span id="RESTORING_PREVIOUSLY_INSTALLED_WINDOWS_APPS"></span>Restoring previously installed Windows apps

Starting with Windows 10, version 1809, preinstalled Windows apps that have been updated after their initial installation get restored to their updated state. Prior to Windows 10, version 1809, preinstalled Windows apps get restored to their factory version and state. Instead of restoring them from a recovery image, a copy of the Windows apps is automatically backed up when they are provisioned during image customization and manufacturing, and the backups are restored when Push-button reset features are used.

### <span id="Restoring_other_customizations"></span><span id="restoring_other_customizations"></span><span id="RESTORING_OTHER_CUSTOMIZATIONS"></span>Restoring other customizations

To restore Windows desktop applications and settings, you can use provisioning packages created using the ScanState utility, and either push-button reset extensibility points or Auto-apply folders (Windows 10, version 1809 and later).

To learn more, see [Deploy push-button reset features using ScanState](deploy-push-button-reset-features.md) and [Deploy push-button reset features using Auto-apply folders](deploy-pbr-features-using-auto-apply.md) .
 

## Keep my files

The **Keep my files** feature preserves a number of system and user settings that are required to keep the system running while minimizing the need for users to reconfigure their PCs.

Preserved settings can be broadly categorized into one of the following categories:

-   Are required for users to log on to their PCs after running the **Keep my files** feature.
-   Affect how users access their documents and personal files.
-   Are difficult for most users to recreate.
-   Affect system security or user privacy.
-   Personalize the PC.

### Settings
The preserved settings are summarized as follows:

-   User accounts (local, domain, Microsoft account), and group memberships
-   Domain settings
-   Windows Update settings
-   Library settings
-   Lock screen background
-   Desktop themes
-   International settings
-   Wireless network profiles
-   Settings configured in Windows Welcome

### <span id="User_data"></span><span id="user_data"></span><span id="USER_DATA"></span>User data

Because user data can be stored in many locations, the **Keep my files** feature preserves most folders and files that are not part of a standard Windows installation. The **Keep my files** feature refreshes the following system locations and does not preserve the contents.

-   \\Windows
-   \\Program Files
-   \\Program Files(x86)
-   \\ProgramData
-   \\Users\\&lt;user name&gt;\\AppData (in each user profile)

**Note**  Some applications store user data in the \\AppData folder in user profiles. The \\AppData folders are available in C:\\Windows.old after using the **Keep my files** feature.

The **Keep my files** feature bypasses the following locations and preserves the contents:

-   File History versioning data
-   All files and folders on non-OS partitions

### <span id="Windows_Applications"></span><span id="windows_applications"></span><span id="WINDOWS_APPLICATIONS"></span>Windows Applications

The **Keep my files** feature handles application types differently in order to ensure that the PC can be restored to a reliable state. 

Applications are handled as follows:

-   User-acquired Windows apps from the Microsoft Store are not preserved. Users will need to reinstall them from the Microsoft Store. This is a change from Windows 8/8.1.
-   Starting with Windows 10, version 1809, preinstalled Windows apps that have been updated since initial installation will be restored to an updated state. Prior to Windows 10, version 1809, preinstalled Windows apps are restored to their factory version and state. Updates to these apps will be downloaded and reapplied automatically when internet connectivity is available.
-   User-acquired Windows desktop applications are not preserved. Users will need to reinstall them manually.
-   Preinstalled Windows desktop applications captured in the customizations provisioning package will be restored to their factory condition, even if users have previously uninstalled them.

The **Keep my files** feature does not preserve user-installed Windows desktop applications by default, and locations that are commonly used for storing application settings (\\AppData and \\ProgramData) are deleted. Manufacturers can leverage Auto-apply folders or the push-button reset extensibility points to save and later restore specific application settings and data, if necessary.

## Remove everything 

When users use the **Remove everything** feature, they will be presented with options that affect the way that their data is removed from the PC.

-   If the PC has more than one user-accessible hard drive volumes, users can choose to remove data from all volumes or only the Windows volume.

    The Windows volume is never formatted, as the files needed to rebuild the OS are on it. Instead, user data files are deleted individually.

    If user chooses to remove data from all volumes, the data volumes are formatted.
	
-   Users can choose to simply delete their files or to also perform data erasure on the drive(s) so that recovery of the data by someone else is much more difficult.

Manufacturers must configure custom utility partitions as follows to ensure these partitions are not affected by the reset process.

-   For UEFI-based PCs, utility partitions on GUID Partition Table (GPT) disks should have the GPT\_ATTRIBUTE\_PLATFORM\_REQUIRED attribute set. See [PARTITION\_INFORMATION\_GPT structure](http://go.microsoft.com/fwlink/?LinkId=617162) for more information on GPT partition attributes.
-   For BIOS-based PCs, utility partitions on Master Boot Record (MBR) disks must be of a type other than 0x7, 0x0c, 0x0b, 0x0e, 0x06, and 0x42.

The time it takes to perform data erasure depends on drive speed, partition size, and whether the drive is encrypted using Windows BitLocker Drive Encryption. The data erasure functionality is targeted at consumers and does not meet government and industry data erasure standards.

If [Compact OS](compact-os.md) is enabled on the OS before the reset, Compact OS will remain enabled after the PC has been reset. 



## <span id="Compact_OS"></span><span id="compact_os"></span><span id="COMPACT_OS"></span>Compact OS


Compact OS is a collection of technologies which allow Windows 10 to be deployed on PCs with storage capacity as low as 16 gigabytes (GB). The following two technologies in particular work in conjunction with the Push-button reset changes to reduce Windows’ disk footprint:

-   Per-file compression When applying a reference image file (WIM) to a PC, the files written to the disk can be compressed individually using the XPRESS Huffman codec. This is the same codec used by the WIMBoot technology in Windows 8.1. When Push-button reset features rebuilds the OS, the runtime system files remain compressed.
-   Single-instancing of installed customizations After the installed customizations (e.g. Windows desktop applications) have been captured (using ScanState) into a reference device data image stored inside a provisioning package, the two copies of the customizations can be singled-instanced to reduce disk footprint impact. This is accomplished by converting the installed customizations (e.g. C:\\Program Files\\Foo\\Foo.exe) into file pointers linked to the contents of the reference device data image.

The following diagram illustrates the high-level content layout of PCs with Compact OS enabled:

![Diagram shows the partition structure. The OS partition includes the Runtime OS and provisioning packages, which are in C:\Recovery\Customizations. The Runtime OS is compressed. Desktop apps are in provisioning packages, in the C:\Recovery\Customizations folder, and these provisioning packages are compressed. To run the desktop apps, the runtime OS uses file pointers that go to the provisioning package.](images/dep-winre-compactos.png)

Both technologies are optional and can be configured during deployment.

## Related topics
[Bare metal recovery](bare-metal-recovery.md)
 





