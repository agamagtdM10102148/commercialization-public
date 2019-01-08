---

Description: Modify a Windows image
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: Modify a Windows image
ms.date: 1/7/2019
ms.topic: article
ms.custom: RS5
---

# Modify a Windows image

You can service, or make changes to, a Windows image in different ways:

* [Online servicing (audit mode)](audit-mode-overview.md): Update Windows from a familiar Windows environment. Apply your Windows image to a new reference device, and boot it into the built-in administrator account (audit mode). From here, you can add drivers, apps, and customizations. When you're done, prepare (generalize) the device and capture a new image file that can be applied to new devices. 

  ![Modify an image online: Start with an image file (either .wim or .ffu format). Apply it to a reference device. Modify it in Windows. Generalize it to prepare it for capturing. Capture the image into a new image file (either .wim or .ffu format). Apply it to new devices.](images/servicing_audit.png)

* [Offline servicing](mount-and-modify-a-windows-image-using-dism.md): Update Windows faster by using DISM to make your changes without ever booting Windows. Mount your image to a temporary location, install apps, drivers, languages, and more, and then commit the changes so they can be applied to new devices. DISM works from an elevated command-line or from PowerShell, which makes it easier to automate your changes with scripts.

  ![Modify an image offline: Start with an image file (either .wim or .ffu format). Mount the file using DISM. It appears as a group of folders. Modify it using DISM, adding drivers, languages, and more. Use DISM to unmount and commit the changes back to the original image file. Apply it to new devices.](images/servicing_mount.png)

* [Servicing an image by using Windows Setup](windows-setup-automation-overview.md): During final deployment, you can use Windows Setup, plus a customized answer file (unattend.xml), to make final modifications.

  ![Servicing with Setup: Start with a new device with a USB that contains Windows Setup, your Windows image file, and an unattend.xml customization file. Apply it to new devices.](images/servicing_unattend.png)

## In this section

| Topic | Description |
|  --- | ---  |
| [Audit mode](audit-mode-overview.md) | Update Windows from a familiar Windows environment. |
| [Mount and Modify a Windows Image Using DISM](mount-and-modify-a-windows-image-using-dism.md) | How to use DISM to mount a Windows image and make changes |
| [Repair a Windows Image](repair-a-windows-image.md) | How to repair a corrupted Windows image |
