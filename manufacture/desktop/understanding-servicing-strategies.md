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

# Understanding servicing strategies

You can service, or make changes to, a Windows image in different ways:

## Online servicing

Update Windows from a familiar Windows environment. Apply your Windows image to a new reference device, and boot it into the built-in administrator account (audit mode). From here, you can add drivers, apps, and customizations. When you're done, prepare (generalize) the device and capture a new image file that can be applied to new devices. 

![Modify an image online: Start with an image file (either .wim or .ffu format). Apply it to a reference device. Modify it in Windows. Generalize it to prepare it for capturing. Capture the image into a new image file (either .wim or .ffu format). Apply it to new devices.](images/servicing_audit.png)

To learn more, see [Audit mode overview](audit-mode-overview.md).

## Offline servicing

To make faster changes to your images, you can make changes to the image without ever booting it. With the DISM tool, you can mount your image to a temporary location, install apps, drivers, languages, and more, and then commit the changes so they can be applied to new devices. DISM works from an elevated command-line or from PowerShell, which makes it easier to automate your changes with scripts.

![Modify an image offline: Start with an image file (either .wim or .ffu format). Mount the file using DISM. It appears as a group of folders. Modify it using DISM, adding drivers, languages, and more. Use DISM to unmount and commit the changes back to the original image file. Apply it to new devices.](images/servicing_mount.png)

To learn more, see [Mount and modify a Windows image using DISM](mount-and-modify-a-windows-image-using-dism.md).

## Servicing an image by using Windows Setup

During final deployment, you can use Windows Setup, plus a customized answer file (unattend.xml), to make final modifications.

![Servicing with Setup: Start with a new device with a USB that contains Windows Setup, your Windows image file, and an unattend.xml customization file. Apply it to new devices.](images/servicing_unattend.png)

To learn more, see [Windows Setup automation overview](windows-setup-automation-overview.md).

## <span id="related_topics"></span>Related topics


[Deployment Image Servicing and Management (DISM) Best Practices](deployment-image-servicing-and-management--dism--best-practices.md)

[DISM - Deployment Image Servicing and Management Technical Reference for Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)
