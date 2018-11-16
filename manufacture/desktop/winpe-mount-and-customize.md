---
author: kpacquer
Description: 'WinPE: Mount and Customize'
ms.assetid: 5d5c13e8-8754-4fff-afd1-dcc3fb757bb9
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: 'WinPE: Mount and Customize'
ms.author: kenpacq
ms.date: 4/24/2018
ms.topic: article


---

# WinPE: Mount and Customize

WinPE ships as a .wim file. Mounting and customizing a WinPE image is the same process as any other Windows image. WinPE also has some customizations that are specific to it. This topic covers the common ways to customize a WinPE image.

## Common customizations:

-   [Device drivers (.inf files)](winpe-add-drivers.md). You can customize device drivers, such as drivers that support network cards or storage devices.
-   [Packages (.cab files, also known as WinPE optional components)](winpe-add-packages--optional-components-reference.md) Add languages, hotfixes, or support for features like PowerShell and the HTML Application Language (HTA).
-   [Languages](winpe-add-packages--optional-components-reference.md). To run WinPE in multiple languages, add the packages (optional components) for those languages.
-   Add files and folders. These can be added directly to the WinPE image.
-   [DISM: Use a newer version](copy-dism-to-another-computer.md). When new versions of Windows require features from the latest version of DISM, you can add DISM directly into WinPE.
-   [Startup scripts](#addstartupscript). Examples include setting up a network connection, or adding a custom application, such as diagnostic software.
-   [Apps](#addapp). Note, WinPE only supports legacy apps.
-   [Temporary storage (scratch space)](#scratchspace). If your application requires temporary file storage, you can reserve extra memory space in RAM.
-   [Background image](#addwallpaper)
-   [Power scheme](#highperformance)
-   [WinPE settings](#addanswerfilesettings)
-   [Windows updates](#updates)

## <span id="Get_the_ADK"></span>Get the Windows Assessment and Deployment Kit with Windows PE tools

-   Install the [Windows Assessment and Deployment Kit (Windows ADK) Technical Reference](http://go.microsoft.com/fwlink/p/?LinkId=526803), with **Windows Preinstallation Environment**. If you're using the ADK for Windows 10, version 1809, you'll have to download and install the WinPE [addon](https://go.microsoft.com/fwlink/?linkid=2022233) after you install the ADK. Previous versions of the ADK include **Windows Preinstallation Environment** in the ADK installer.

## <span id="Create_WinPE_image"></span>Create a set of either 32-bit or 64-bit Windows PE files

Before you can customize WinPE, you need to have a WinPE image to work with. If you need to get a WinPE image, see [WinPE: Create USB bootable drive](winpe-create-usb-bootable-drive.md) to learn how.

## <span id="Mount_the_image"></span>Mount the Windows PE boot image

-   Use DISM to mount the WinPE image into a temporary location on your technician PC:

    ```
    Dism /Mount-Image /ImageFile:"C:\WinPE_amd64\media\sources\boot.wim" /index:1 /MountDir:"C:\WinPE_amd64\mount"
    ```

## <span id="Add_customizations"></span><span id="add_customizations"></span><span id="ADD_CUSTOMIZATIONS"></span>Add customizations


### <span id="AddDrivers"></span>Add device drivers (.inf files)

-   Use `DISM /add-driver` to add a device driver to your WinPE image.

    ```
    Dism /Add-Driver /Image:"C:\WinPE_amd64\mount" /Driver:"C:\SampleDriver\driver.inf"
    ```

    You can add multiple drivers to an image by using one command, but it's often easier to troubleshoot problems if you add each driver package individually.

    To learn more about drivers, see [Add device drivers (.inf files)](winpe-add-drivers.md).
    To see all available DISM driver servicing options, see [DISM driver servicing command-line options](dism-driver-servicing-command-line-options-s14.md).

### <span id="AddPackages"></span>Add packages/languages/optional components/.cab files

-   WinPE has packages that you can add with DISM to enable additional features and languages. Use `DISM /add-package` to add optional components to your image. When you add a WinPE optional component, make sure that you add both the optional component and its associated language packs.

    ```
    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-HTA.cab"  

    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-HTA_en-us.cab"
    ```

    To learn more about available optional components and languages, see [WinPE: Add packages (Optional Components Reference)](winpe-add-packages--optional-components-reference.md).

### <span id="AddFilesAndFolders"></span>Add files and folders

-   Copy files and folders into the C:\\WinPE\_amd64\\mount folder. These files will show up in the X:\\ folder in WinPE.

    Don't add too many files, as these will slow down WinPE and can fill up the available memory in the default RAMDisk environment.

### <span id="AddStartupScript"></span><span id="addstartupscript"></span><span id="ADDSTARTUPSCRIPT"></span>Add a startup script

-   Modify Startnet.cmd to include your customized commands. This file is located in your mounted image at `C:\WinPE_amd64\mount\Windows\System32\Startnet.cmd`.

    You can also call other batch files or command line scripts from this file.

    For Plug and Play or networking support, make sure that you include a call to **wpeinit** in your customized Startnet.cmd script. For more info, see [Wpeinit and Startnet.cmd: Using WinPE Startup Scripts](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md).

### <span id="AddApp"></span><span id="addapp"></span><span id="ADDAPP"></span>Add an app

1.  Create an app directory inside the mounted WinPE image.

    ```
    md "C:\WinPE_amd64\mount\windows\<MyApp>"
    ```

2.  Copy the necessary app files to the local WinPE directory.

    ```
    Xcopy C:\<MyApp> "C:\WinPE_amd64\mount\windows\<MyApp>"
    ```

3.  Test the app later by booting WinPE and running the application from the X: directory.

    ```
    X:\Windows\System32> X:\Windows\<MyApp>
    ```

    If your app requires temporary storage, or if WinPE becomes unresponsive when it runs an app, you may need to increase the amount of temporary storage (scratch space) allocated to WinPE.

4.  To automatically launch a shell or application that runs when WinPE starts, add the path location to the Winpeshl.ini file. For more info, see [Winpeshl.ini Reference: Launching an app when WinPE starts](winpeshlini-reference-launching-an-app-when-winpe-starts.md).

### <span id="ScratchSpace"></span><span id="scratchspace"></span><span id="SCRATCHSPACE"></span>Add temporary storage (scratch space)

-   WinPE reserves memory on the X: drive to unpack the WinPE files, plus additional temporary file storage, known as scratch space, that can be used by your applications. By default, this is 512MB for PCs with more than 1GB of RAM, otherwise the default is 32MB. Valid values are 32, 64, 128, 256, or 512.

    ```
    Dism /Set-ScratchSpace:256 /Image:"C:\WinPE_amd64\mount"
    ```

### <span id="AddWallpaper"></span><span id="addwallpaper"></span><span id="ADDWALLPAPER"></span>Replace the background image

If you've got multiple versions of WinPE, you can set the background image so you can instantly tell which version of WinPE is running.

Change the security permissions of the WinPE background image file (`\windows\system32\winpe.jpg`). This allows you to modify or delete the file.

1.  In Windows Explorer, navigate to `C:\WinPE_amd64\mount\windows\system32`.

2.  Right-click the `C:\WinPE_amd64\mount\windows\system32\winpe.jpg` file, and select **Properties** &gt; **Security** tab &gt; **Advanced**.

3.  Next to Owner, select **Change**. Change the owner to **Administrators**.

4.  Apply the changes, and exit the Properties window to save changes.

5.  Right-click the `C:\WinPE_amd64\mount\windows\system32\winpe.jpg` file, and select **Properties** &gt; **Security** tab &gt; **Advanced**.

6.  Modify the permissions for **Administrators** to allow full access.

7.  Apply the changes, and exit the Properties window to save changes.

8.  Replace the `winpe.jpg` file with your own image file.

### <span id="HighPerformance"></span><span id="highperformance"></span><span id="HIGHPERFORMANCE"></span>Set the power scheme to high performance

Note: Using the high performance power scheme can make the device run hotter than usual. 

1.  In Notepad, edit the file: `C:\WinPE_amd64\mount\windows\system32\startnet.cmd`, adding a command to set the power scheme to High Performance.

    ```
    wpeinit
    powercfg /s 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c 
    ```

### <span id="AddAnswerFileSettings"></span><span id="addanswerfilesettings"></span><span id="ADDANSWERFILESETTINGS"></span>Add answer file settings

-   Some WinPE settings can be managed by using an answer file, such as firewall, network, and display settings. Create an answer file, name it unattend.xml, and add it to the root of the WinPE media to process these settings. For more information, see [Wpeinit and Startnet.cmd: Using WinPE Startup Scripts](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md).

### <span id="updates"></span>Add updates to WinPE (if needed)

You can apply updates to your WinPE image, but you'll only need to for certain situations.

If you've been instructed to apply an update to your WinPE image, you'll have to first download the latest update for your WinPE version from the [Microsoft update catalog](https://www.catalog.update.microsoft.com/Search.aspx?q=cumulative%20update%20for%20Windows%2010). Updates for WinPE are included in updates for the matching version of Windows 10. You can find information about the latest available updates for Windows 10 at [Windows 10 update history](https://support.microsoft.com/en-us/help/4018124/windows-10-update-history).

1. Download the latest update.

2. Apply the update to your mounted WinPE image.

    ```
    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"E:\windows10.0-kbxxxxx.msu"
    ```
    Where Windows10.0-kbxxxxx.msu is the name of the update file 

3. Lock in the update:

    ```
    dism /cleanup-image /image:C:\WinPE_amd64\mount\windows /startcomponentcleanup /resetbase /scratchdir:C:\temp
    ```

## <span id="Unmount"></span>Unmount the Windows PE image and create media

1.  Unmount the WinPE image, committing changes.

    ```
    Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /commit
    ```

2.  Create bootable media, such as a USB flash drive.

    ```
    MakeWinPEMedia /UFD C:\WinPE_amd64 F:
    ```

3.  Boot the media. WinPE starts automatically. After the WinPE window appears, the wpeinit command runs automatically. This may take a few minutes. Verify your customizations.

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


-   WinPE won’t boot? See the troubleshooting tips at the end of the topic: [WinPE: Create USB Bootable drive](winpe-create-usb-bootable-drive.md)
-   For tips on connecting to a network, see [WinPE Network Drivers: Initializing and adding drivers](winpe-network-drivers-initializing-and-adding-drivers.md).
-   If the WinPE image becomes unserviceable, you may need to clean up the images before you can mount the image again. For information, see [Repair a Windows Image](repair-a-windows-image.md).

### <span id="To_delete_a_working_directory_"></span><span id="to_delete_a_working_directory_"></span><span id="TO_DELETE_A_WORKING_DIRECTORY_"></span>To delete a working directory:

In some cases, you may not be able to recover the mounted image. DISM protects you from accidentally deleting the working directory, so you may have to try the following steps to get access to delete the mounted directory. Try each of the following steps:

1.  Try remounting the image:

    ```
    dism /Remount-Image /MountDir:C:\mount
    ```

2.  Try unmounting the image, discarding the changes:

    ```
    dism /Unmount-Image /MountDir:C:\mount /discard
    ```

3.  Try cleaning up the resources associated with the mounted image:

    ```
    dism /Cleanup-Mountpoints
    ```

## <span id="related_topics"></span>Related topics

[WinPE: Optimize and shrink the image](winpe-optimize.md)

[WinPE for Windows 10](winpe-intro.md)

[WinPE: Create USB Bootable drive](winpe-create-usb-bootable-drive.md)

[WinPE: Create a Boot CD, DVD, ISO, or VHD](winpe-create-a-boot-cd-dvd-iso-or-vhd.md)

[WinPE: Install on a Hard Drive (Flat Boot or Non-RAM)](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)

[WinPE: Boot in UEFI or legacy BIOS mode](winpe-boot-in-uefi-or-legacy-bios-mode.md)

[WinPE: Add packages (Optional Components Reference)](winpe-add-packages--optional-components-reference.md)

 

 






