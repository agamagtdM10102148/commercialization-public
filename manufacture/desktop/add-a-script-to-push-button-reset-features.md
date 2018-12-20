---
author: kpacquer
Description: 'You can customize the Push-button reset experience by configuring extensibility points. This enables you to run custom scripts, install additional applications, or preserve additional user or application data.'
ms.assetid: 147358d0-bae5-4f48-b02d-1ccc48bdcc2e
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: 'Add a script to push-button reset features'
ms.author: kenpacq
ms.date: 05/02/2017
ms.topic: article
ms.custom: RS5
---

# Add a script to push-button reset features


You can customize the Push-button reset experience by configuring extensibility points. This enables you to run custom scripts, install additional applications, or preserve additional user or application data. If you've configured extensibility points in addition to Auto-apply folders, the extensibility points will be used and the Auto-apply folders will be ignored.

## <span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Prerequisites


To configure extensibility points and customize the Push-button reset experience, you need the following.

-   A configuration file named ResetConfig.xml
-   Scripts that execute custom operations at selected extensibility points.
-   Any additional files required by the scripts

Each script must meet the following requirements:

-   Be an executable (.exe) or a command script (.cmd)
-   Run without displaying a graphical user interface (GUI)
-   Return either 0 to indicate a successful operation, or a non-zero value to indicate an unsuccessful operation

These files should be placed in the folder C:\\Recovery\\OEM, and will automatically be detected by Push-button reset features. It's OK to use subfolders.

## <span id="Step_1__Creating_Configuration_Files_to_Prepare_for_Recovery"></span><span id="step_1__creating_configuration_files_to_prepare_for_recovery"></span><span id="STEP_1__CREATING_CONFIGURATION_FILES_TO_PREPARE_FOR_RECOVERY"></span>Step 1: Creating Configuration Files to Prepare for Recovery


**To create extensibility scripts**

-   In Notepad, you can create custom scripts to save or retrieve log files, check partitions, and to install applications.

    **Important**  
    Your scripts must meet the following requirements:

    -   The scripts are formatted as a .cmd or .exe files.
    -   The scripts do not depend on Windows PE optional components not present in the default Windows RE image (winre.wim).
    -   The scripts do not depend on binaries (e.g. .exe or .dll files) not present in the default Windows RE image (winre.wim).
    -   The scripts run without displaying a graphical user interface (GUI).
    -   The scripts complete all intended functions within 5 minutes for each extensibility point.
    -   The script must not modify the drive letters. This can potentially cause the recovery to fail.

    Your scripts must return a 0 (zero), if successful. If push-button reset receives a non-0 value, the following steps occur:

    -   **If running the Keep my files feature**: All system changes are rolled back. If the script or executable file is initiated from the Windows **PC settings** menu, the system reboots in Windows. If the script or executable file is initiated from Windows RE or the **Boot Options** menu, the system remains in Windows RE and displays an error message.

    -   **If running the Remove everything feature**: The failure is ignored. The script or executable file proceeds to the next step in the reset process and logs the failure.

    You can use the following locations for storage, if needed.

    -   **Windows PE RAM drive (X:)**. This virtual drive is created by Windows PE, and stays active during the **Keep my files** process. You can use it with the **Keep my files** feature to save data before the partition is refreshed, and to restore the data after the partition refresh is complete. The amount of available memory is limited to the amount of RAM on the system, minus the amount of RAM needed for the Windows RE tools when fully expanded. For instructions about mounting Windows RE and determining the fully-expanded file size, see [Customize Windows RE](customize-windows-re.md).

    -   **Designated OEM partition**. You can leave extra room on a partition. For example, you can leave room on the recovery image partition, and use scripts to temporarily assign a drive letter and then save files to that partition. However, if your user uses the recovery media to repartition the disks, the data on these partitions might be lost during the recovery process.

### Create a push-button reset configuration file

Create a configuration file (ResetConfig.xml) that points to your push-button reset extensibility scripts. For more information about this file, see [ResetConfig XML Reference](resetconfig-xml-reference-s14.md).

Save this file with the file type of **UTF-8**. Do not use ANSI coding. For example: in Notepad, click **File**, and then click **Save As**. In the **Encoding** box, select **UTF-8**, and save this file as `E:\Recovery\RecoveryImage\ResetConfig.xml`, where *E* is the drive letter of a USB flash drive or other removable media. 


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
      <Run Phase="FactoryReset_AfterDiskFormat">
         <Path>CheckPartitions.exe</Path>
         <Duration>2</Duration>
      </Run>
      <Run Phase="FactoryReset_AfterImageApply">
         <Path>InstallApps.cmd</Path>
         <Param>/allApps</Param>
         <Duration>2</Duration>
      </Run>
      <!-- May be combined with Recovery Media Creator
           configurations – insert SystemDisk element here -->
   </Reset>
```

Note, in these examples, SaveLogFiles.cmd, RetrieveLogFiles.cmd, CheckPartitions.exe, and InstallApps.cmd are all fictional scripts.


>[!Note]
> You can use the same ResetConfig.xml file to configure Windows to create recovery media. For more information, see [Deploy Push-Button Reset Features](deploy-push-button-reset-features.md).

## <span id="bkmk_4"></span><span id="BKMK_4"></span>Step 2: Add configuration files and scripts to the destination computer

1.  On your destination computer, insert the USB flash drive with the configuration files.

2.  Copy the configuration files to the destination computer

    ```
    Copy E:\Recovery\RecoveryImage\* R:\RecoveryImage\*
    ```

    where *E* is the drive letter of the USB flash drive.

## Sample scripts: keep unattend.xml, LayoutModification.xml, and OOBE.xml during a reset


Windows doesn't automatically save settings created through unattend.xml setup files, nor Windows Start Menu customizations created with LayoutModification.xml during a full-system reset, nor first-login info from oobe.xml. To make sure your customizations are saved, that includes steps to put the unattend.xml, LayoutModification.xml, and oobe.xml files back into place.

Here's some sample scripts that show how to retain these settings and put them back into the right spots.

Save copies of unattend.xml, LayoutModification.xml, oobe.xml, plus these two text files, in C:\\Recovery\\OEM\\.

**ResetConfig.xml**

```
<?xml version="1.0" encoding="utf-8"?>
<!-- ResetConfig.xml -->
<Reset>
  <Run Phase="BasicReset_AfterImageApply">
    <Path>EnableCustomizations.cmd</Path>
    <Duration>2</Duration>
  </Run>
  <Run Phase="FactoryReset_AfterImageApply">
    <Path>EnableCustomizations.cmd</Path>
    <Duration>2</Duration>
  </Run>
</Reset>
```

**EnableCustomizations.cmd**

```
rem EnableCustomizations.cmd

rem Define %TARGETOS% as the Windows folder (This later becomes C:\Windows) 
for /F "tokens=1,2,3 delims= " %%A in ('reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RecoveryEnvironment" /v TargetOS') DO SET TARGETOS=%%C

rem Define %TARGETOSDRIVE% as the Windows partition (This later becomes C:)
for /F "tokens=1 delims=\" %%A in ('Echo %TARGETOS%') DO SET TARGETOSDRIVE=%%A

rem Add back Windows settings, Start menu, and OOBE.xml customizations
copy "%TARGETOSDRIVE%\Recovery\OEM\Unattend.xml" "%TARGETOS%\Panther\Unattend.xml" /y
copy "%TARGETOSDRIVE%\Recovery\OEM\LayoutModification.xml" "%TARGETOSDRIVE%\Users\Default\AppData\Local\Microsoft\Windows\Shell\LayoutModification.xml" /y
xcopy "%TARGETOSDRIVE%\Recovery\OEM\OOBE\Info" "%TARGETOS%\System32\Info\" /s

rem Recommended: Create a pagefile for devices with 1GB or less of RAM.
wpeutil CreatePageFile /path=%TARGETOSDRIVE%\PageFile.sys /size=256

EXIT 0
```

For multilingual deployments, OOBE.xml uses a more complicated folder structure. It's OK to just copy the entire folder into C:\\Recovery\\OEM, and then modify the script to copy the entire folder:

```
xcopy "%ScriptFolder%\Info\" "%TargetOSDrive%\System32\Info\" /s
```


## Sample scripts: preserving and retrieving files

### Part 1: Save log files to a temporary folder in memory

This sample script preserves system log files that would otherwise be removed, by placing them in a temporary location in memory. These log files are to be retrieved by another sample script, **RetrieveLogFiles.cmd**.

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

### Part 2: Retrieve log files

This sample script retrieves the files that were saved in memory by the `SaveLogFiles.cmd` script, and adds them back to the system. 

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

## Next steps


Now that you have customized the push-button reset experience, you can deploy the recovery image for push-button reset (Install.wim) to the recovery image partition.

To copy the Diskpart script, the ResetConfig.xml file, and the push-button reset recovery image (install.wim) to the recovery image partition of the destination PC, follow the instructions in the [Deploy Push-Button Reset Features](deploy-push-button-reset-features.md) topic.

## <span id="related_topics"></span>Related topics


[Push-Button Reset Overview](push-button-reset-overview.md)

[Create Media to Run Push-Button Reset Features](create-media-to-run-push-button-reset-features-s14.md)

[Deploy Push-Button Reset Features](deploy-push-button-reset-features.md)

[REAgentC Command-Line Options](reagentc-command-line-options.md)

[ResetConfig XML Reference](resetconfig-xml-reference-s14.md)



