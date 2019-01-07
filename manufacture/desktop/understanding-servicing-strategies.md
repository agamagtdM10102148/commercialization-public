---
author: kpacquer
Description: Describes how to make changes to a Windows image, and the phases for when you can make changes.
ms.assetid: 2e24e9e3-8216-4d8a-bd63-c61adddc6ac8
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: Understanding Servicing Strategies
ms.author: kenpacq
ms.date: 01/07/2019
ms.topic: article
---

# Understanding Servicing Strategies

You can service, or make changes to, a Windows image at various phases of deployment in the following ways: online, offline, or during installation. The phase of deployment that you select depends on your deployment strategy.

[Servicing a running operating system](audit-mode-overview.md): Also known as **online servicing**, this method involves applying Windows to a device, then booting it in the built-in administrator account (audit mode). From here, you can add drivers, apps, and customizations in a familiar Windows environment. When you're ready, prepare (generalize) the device and capture a new image file that can be applied to new devices. 

![Modify an image online: Start with an image file (either .wim or .ffu format). Apply it to a reference device. Modify it in Windows. Generalize it to prepare it for capturing. Capture the image into a new image file (either .wim or .ffu format). Apply it to new devices.](images/servicing_audit.png)

[Offline Servicing](mount-and-modify-a-windows-image-using-dism.md): You can modify a Windows image without ever booting Windows. Use DISM to mount the image to a temporary location, add updates, change drivers, languages, settings, and more. Unmount and commit the changes to the image file, and apply it to new devices.
For many modifications, this method is faster and more efficient than online servicing. 

![Modify an image offline: Start with an image file (either .wim or .ffu format). Mount the file using DISM. It appears as a group of folders. Modify it using DISM, adding drivers, languages, and more. Use DISM to unmount and commit the changes back to the original image file. Apply it to new devices.](images/servicing_mount.png)

[Servicing an Image by Using Windows Setup](windows-setup-automation-overview.md): During final deployment, you can use Windows Setup, plus a customized answer file (unattend.xml), to make final modifications.

![Servicing with Setup: Start with a new device with a USB that contains Windows Setup, your Windows image file, and an unattend.xml customization file. Apply it to new devices.](images/servicing_unattend.png)

## <span id="onlineservicingstrategy"></span>Servicing a Running Operating System

Online servicing is ideal for drivers when the driver packages have co-installers or application dependencies. It is also efficient when most of your servicing packages have installers, or the updates are in .msi or KB.exe file formats, or the applications rely on Windows installed services and technologies (such as the .NET Framework or full Plug and Play support).

There are several tools that can be used to service a running operating system (also known as servicing an online image). You should boot to audit mode to add updates to your Windows image. Audit mode does not require settings in Windows Welcome to be applied, allowing quicker access to the desktop. After you have booted to audit mode, you can add Plug and Play device drivers, install applications and system components, and test the validity of the installation. For more information about how to use audit mode, see [Boot Windows to Audit Mode or OOBE](boot-windows-to-audit-mode-or-oobe.md).

The following tools are typically used to update a running Windows operating system:

-   Use DISM to enumerate drivers, international settings, packages, and features, and to apply unattended answer file settings. For more information, see [DISM - Deployment Image Servicing and Management Technical Reference for Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md).

-   Use DPInst to add drivers for detected hardware. For information about DPInst and other tools available in the Windows Driver Kit (WDK), see [Download kits and tools for Windows](http://go.microsoft.com/fwlink/?LinkId=89603).

-   Use PNPUtil to add, remove, and enumerate drivers. For more information, see [Use PnPUtil at a command line to install a Plug and Play device](http://go.microsoft.com/fwlink/?LinkId=139151).

-   Use Windows Update Stand-Alone Installer to add service packs or other .msu files. For more information, see [Description of the Windows Update Stand-alone Installer (Wusa.exe) and of .msu Files in Windows](http://go.microsoft.com/fwlink/?LinkId=90850)


## <span id="servicingdeploymentstrategy"></span>Servicing an Image by Using Windows Setup


Use an unattended answer file with Windows Setup to service an image during the various configuration passes of Windows Setup. The answer file contains all the settings that are used to configure and update the Windows image. Setup calls the answer file multiple times during the deployment process. After the operating system is installed, you can boot to audit mode or Windows Welcome. For more information about Windows Setup, see [Windows Setup Technical Reference](windows-setup-technical-reference.md). For more information about configuration passes, see [Windows Setup Configuration Passes](windows-setup-configuration-passes.md).

An unattended answer file can be used during setup to:

-   Add or remove a language pack.

-   Configure international settings.

-   Add and remove drivers.

-   Add and remove packages.

-   Enable and disable Windows operating system features.


## <span id="related_topics"></span>Related topics


[Deployment Image Servicing and Management (DISM) Best Practices](deployment-image-servicing-and-management--dism--best-practices.md)

[DISM - Deployment Image Servicing and Management Technical Reference for Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

 

 






