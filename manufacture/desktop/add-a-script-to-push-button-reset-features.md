---

Description: 'You can customize the Push-button reset experience by configuring extensibility points. This enables you to run custom scripts, install additional applications, or preserve additional user or application data.'
ms.assetid: 147358d0-bae5-4f48-b02d-1ccc48bdcc2e
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: 'Add extensibility scripts to push-button reset'
ms.date: 12/20/2018
ms.topic: article
ms.custom: RS5
---

# Add extensibility scripts to push-button reset

OEMs can insert custom extensibility scripts that run when a user runs the push-button reset features: **Keep my files** and **Remove everything**.

You can use either extensibility scripts or [Auto-apply folders](recovery-strategy-for-common-customizations.md#auto-apply) to restore common customizations that aren't otherwise restored, including:
* The Start Menu 
* Taskbar
* OOBE
* Unattend.xml customizations

In addition, extensibility scripts can help perform other tasks, like:
* Modifying data or utility partitions
* [Saving and restoring files](#preserving_and_retrieving_files) that aren't normally kept by the **Keep my files** feature.

Note: If you include Auto-apply folders, you shouldn't include extensibility scripts. If you include both Auto-apply folders and extensibilty scripts, the Auto-apply folders will be ignored.

**To configure the scripts**, add all of the following in the `C:\Recovery\OEM` folder:

* A push-button reset configuration file (ResetConfig.xml) that defines which scripts to run.
* The extensibility scripts
* Any files required by the extensibility scripts.

## Extensibility scripts

**Requirements:**
- The scripts are formatted as a .cmd or .exe files.
- The scripts do not depend on Windows PE optional components not present in the default Windows RE image (winre.wim).
- The scripts do not depend on binaries (e.g. .exe or .dll files) not present in the default Windows RE image (winre.wim).
- The scripts run without displaying a graphical user interface (GUI).
- The scripts complete all intended functions within 5 minutes for each extensibility point.
- The script must not modify the drive letters. This can potentially cause the recovery to fail.

The script must return a 0 (zero) if successful. If push-button reset receives a non-0 value, the following steps occur:
- If running the **Keep my files** feature: All system changes are rolled back. If the script or executable file is initiated from the Windows **PC settings** menu, the system reboots in Windows. If the script or executable file is initiated from Windows RE or the **Boot Options** menu, the system remains in Windows RE and displays an error message.
- If running the **Remove everything** feature: The failure is ignored. The script or executable file proceeds to the next step in the reset process and logs the failure.

## Push-button reset configuration file (ResetConfig.xml)
Add a [ResetConfig.xml](resetconfig-xml-reference-s14.md) file to point to your push-button reset extensibility scripts. 

This file must be saved with the file type of **UTF-8**. Do not use ANSI coding. For example: in Notepad, click **File**, and then click **Save As**. In the **Encoding** box, select **UTF-8**. 

Save this file and copy it into the Windows images as `C:\Recovery\OEM\ResetConfig.xml`. 

You can use the same ResetConfig.xml file to configure Windows to create recovery media. For more information, see [Deploy Push-Button Reset Features](deploy-push-button-reset-features.md).

There's four [extensibility points](#extensibility_points) that you can use to point to scripts that run near the beginning and end of the **Keep my files** or **Remove everything** operations. For common customizations, you usually only need a single script, as shown in the [sample script](#preserving_and_retrieving_files) below. 

## <span id="restore_common_options"></span>Sample script: restore the Start Menu, Taskbar, OOBE, and unattend.xml customizations

Save the following into the `C:\Recovery\OEM` folder:
* The sample script, **CommonCustomizations.cmd**
* The push-button reset configuration file, **ResetConfig.xml**
* A copy of the Start menu configuration file (**LayoutModification.xml**)
* A copy of the Taskbar configuration file (**TaskbarLayoutModification.xml**)
* A copy of the **unattend.xml** file

Save the following into the `C:\Recovery\OEM\OOBE\Info` folder:
* A copy the entire **OOBE** folder, `%WINDIR%\System32\Oobe\Info\`. 

**CommonCustomizations.cmd**
```
rem CommonCustomizations.cmd

rem Define %TARGETOS% as the Windows folder (This later becomes C:\Windows) 
for /F "tokens=1,2,3 delims= " %%A in ('reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RecoveryEnvironment" /v TargetOS') DO SET TARGETOS=%%C

rem Define %TARGETOSDRIVE% as the Windows partition (This later becomes C:)
for /F "tokens=1 delims=\" %%A in ('Echo %TARGETOS%') DO SET TARGETOSDRIVE=%%A

rem Add back Windows settings, Start menu, Taskbar, and OOBE.xml customizations
copy "%TARGETOSDRIVE%\Recovery\OEM\Unattend.xml" "%TARGETOS%\Panther\Unattend.xml" /y
copy "%TARGETOSDRIVE%\Recovery\OEM\LayoutModification.xml" "%TARGETOSDRIVE%\Users\Default\AppData\Local\Microsoft\Windows\Shell\LayoutModification.xml" /y
copy "%TARGETOSDRIVE%\Recovery\OEM\TaskbarLayoutModification.xml" "%TARGETOS%\OEM\TaskbarLayoutModification.xml" /y
xcopy "%TARGETOSDRIVE%\Recovery\OEM\OOBE\Info" "%TARGETOS%\System32\Info\" /s

rem Recommended: Create a pagefile for devices with 1GB or less of RAM.
wpeutil CreatePageFile /path=%TARGETOSDRIVE%\PageFile.sys /size=256

EXIT 0
```

**ResetConfig.xml**: Note, this example points to the same script twice, so it can be used by both the **Keep my files** or **Remove everything** features. 

```
<?xml version="1.0" encoding="utf-8"?>
<!-- ResetConfig.xml -->
<Reset>
  <Run Phase="BasicReset_AfterImageApply">
    <Path>CommonCustomizations.cmd</Path>
    <Duration>2</Duration>
  </Run>
  <Run Phase="FactoryReset_AfterImageApply">
    <Path>CommonCustomizations.cmd</Path>
    <Duration>2</Duration>
  </Run>
  <!-- May be combined with Recovery Media Creator
       configurations – insert SystemDisk element here -->
</Reset>
```

## <span id="preserving_and_retrieving_files"></span>Preserving and retrieving files

With the **Keep my files** feature, you can use sample scripts to preserve files that would otherwise be removed, by placing them in a temporary location in memory. You cannot keep files with the **Remove everything** feature.

You can use the following locations for storage, if needed.

- **Windows PE RAM drive (X:)**. This virtual drive is created by Windows PE, and stays active during the **Keep my files** process. You can use it with the **Keep my files** feature to save data before the partition is refreshed, and to restore the data after the partition refresh is complete. The amount of available memory is limited to the amount of RAM on the system, minus the amount of RAM needed for the Windows RE tools when fully expanded. For instructions about mounting Windows RE and determining the fully-expanded file size, see [Customize Windows RE](customize-windows-re.md).

- **Designated OEM partition**. You can leave extra room on a partition. For example, you can leave room on the recovery image partition, and use scripts to temporarily assign a drive letter and then save files to that partition. However, if your user uses the recovery media to repartition the disks, the data on these partitions might be lost during the recovery process.

These sample scripts preserve the Windows log files. Save these scripts in the `C:\Recovery\OEM` folder.

**ResetConfig.xml**
```
<?xml version="1.0" encoding="utf-8"?>
<!-- ResetConfig.xml -->
   <Reset>
      <Run Phase="BasicReset_BeforeImageApply">
         <Path>SaveLogFiles.cmd</Path>
         <Duration>4</Duration>
      </Run>      
      <Run Phase="BasicReset_AfterImageApply">
         <Path>RetrieveLogFiles.cmd</Path>
         <Duration>2</Duration>
      </Run>
      <!-- May be combined with Recovery Media Creator
       configurations – insert SystemDisk element here -->
   </Reset>
```

**SaveLogFiles.cmd**: Saves log files to a temporary folder in memory

```
:rem == SaveLogFiles.cmd

:rem == 1. Use the registry to identify the location of
:rem       the new operating system and the primary hard
:rem       drive. For example, 
:rem       %TARGETOS% may be defined as C:\Windows
:rem       %TARGETOSDRIVE% may be defined as C:
for /F "tokens=1,2,3 delims= " %%A in ('reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RecoveryEnvironment" /v TargetOS') DO SET TARGETOS=%%C

for /F "tokens=1 delims=\" %%A in ('Echo %TARGETOS%') DO SET TARGETOSDRIVE=%%A

:rem == 2. Copy old Windows logs to a temporary folder in memory
mkdir X:\Temp
xcopy %TARGETOS%\Logs\*.* X:\temp\OldLogs /cherkyi

EXIT 0
```

**RetrieveLogFiles.cmd**: Retrieves the files that were saved in memory by the SaveLogFiles.cmd script. 

```
:rem == RetrieveLogFiles.cmd

:rem == This sample script retrieves the files that 
:rem    were saved in memory by 
:rem    SaveLogFiles.cmd,
:rem    and adds them back to the system.

:rem == 1. Use the registry to identify the location of
:rem       the new operating system and the primary drive.
:rem        
:rem       %TARGETOS% is the Windows folder 
:rem          (This later becomes C:\Windows)
:rem       %TARGETOSDRIVE% is the Windows partition 
:rem          (This later becomes C:)
for /F "tokens=1,2,3 delims= " %%A in ('reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RecoveryEnvironment" /v TargetOS') DO SET TARGETOS=%%C
for /F "tokens=1 delims=\" %%A in ('Echo %TARGETOS%') DO SET TARGETOSDRIVE=%%A

:rem == 2. Copy the old logs to the new OS 
:rem       at C:\Windows\OldLogs
mkdir %TARGETOS%\OldLogs
xcopy X:\Temp\OldLogs\* %TARGETOS%\OldLogs /cherkyi

EXIT 0
```

## <span id="extensibility_points"></span>Extensibility points

The **Keep my files** feature can be summarized in the following steps:

1.  PC boots into the Windows Recovery Environment (Windows RE).
2.  **EXTENSIBILITY POINT A** (**BasicReset_BeforeImageApply**): Add a script here to copy files, drivers, or settings that are not migrated by default when the user runs the **Keep my files** feature.
3.  User accounts, settings, and data are gathered and moved to a temporary location.
4.  A new copy of the OS is constructed in a temporary location using files from the Windows Component Store.
5.  Customizations stored in provisioning packages under C:\\Recovery\\Customizations are applied to the new OS.
6.  Drivers are copied from the existing OS and injected into the new OS.
7.  Preinstalled Windows apps are restored from their backup location.
8.  System-critical settings are applied to the new OS.
9.  Existing OS is moved to C:\\Windows.old.
10. New OS is moved to the root of the OS volume.
11. **EXTENSIBILITY POINT B** (**BasicReset_AfterImageApply**): Add a script here to restore customization files (unattend.xml, layoutmodification.xml), or restore files and settings you might have backed up at extensibility point A.
12. PC reboots to the new OS.
13. During first boot, user data and settings are reapplied.

The **Remove everything** feature can be summarized in the following steps:

1.  PC boots into the Windows Recovery Environment (Windows RE).
2.  User accounts, data and installed Windows apps and Windows desktop applications are removed from the OS volume.
3.  Data volumes are formatted (if requested by the user).
4.  Data erasure is performed on OS and data volumes (if requested by the user).
5.  **EXTENSIBILITY POINT C** (**FactoryReset_AfterDiskFormat**): Add a script here to reconfigure data partitions if needed. <strong>Important</strong>: Do not modify the Windows partition.
6.  A new copy of the OS is constructed in a temporary location using files from the Windows Component Store.
7.  Customizations stored in provisioning packages under C:\\Recovery\\Customizations are applied to the new OS.
8.  Drivers are copied from the existing OS and injected into the new OS.
9.  Preinstalled Universal Windows apps are restored from their backup location.
10. Existing OS is removed.
11. New OS is moved to the root of the OS volume.
12. **EXTENSIBILITY POINT D** (**FactoryReset_AfterImageApply**): Add a script here to restore customization files (unattend.xml, layoutmodification.xml).
13. PC reboots to the new OS.
14. OOBE starts.

## Alternate method: copy scripts after deployment

A short time after your user completes OOBE, the recovery scripts are moved from the `C:\Recovery\OEM` folder to the recovery partition, at `R:\RecoveryImage\`.

In the unlikely event that push-button reset is used before this operation has taken place, these scripts may not run. To prevent that possibility, you can copy your recovery files directly to the recovery partition, `R:\RecoveryImage\` after your image has been deployed.


## Next steps

Now that you have customized the push-button reset experience, you can deploy the recovery image for push-button reset (Install.wim) to the recovery image partition.

To copy the Diskpart script, the ResetConfig.xml file, and the push-button reset recovery image (install.wim) to the recovery image partition of the destination PC, follow the instructions in the [Deploy Push-Button Reset Features](deploy-push-button-reset-features.md) topic.

## Related topics


[Push-Button Reset Overview](push-button-reset-overview.md)

[Create Media to Run Push-Button Reset Features](create-media-to-run-push-button-reset-features-s14.md)

[Deploy Push-Button Reset Features](deploy-push-button-reset-features.md)

[REAgentC Command-Line Options](reagentc-command-line-options.md)

[ResetConfig XML Reference](resetconfig-xml-reference-s14.md)



