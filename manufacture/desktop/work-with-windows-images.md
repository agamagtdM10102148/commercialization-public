---

Description: Learn how to to work with Windows images
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: Work with Windows images
ms.date: 1/4/2019
ms.topic: article
ms.custom: RS5
---

# Work with Windows images

The Windows 10 OPK includes an image file, **install.wim**, which contains the operating system files for your Windows edition.

Starting by deploying this image to a device, add your customizations to it, test, and incorporate those changes into your images, iterating until you're ready to put the image onto the factory floor.

## Servicing strategies

You can make changes to a Windows image in different ways:

* [Online servicing](audit-mode-overview.md): Update Windows from a familiar Windows environment.

* [Offline servicing](mount-and-modify-a-windows-image-using-dism.md): Update Windows faster by using DISM to make your changes without ever booting Windows.

* [Servicing an image by using Windows Setup](windows-setup-automation-overview.md): Use Windows Setup, plus a customized answer file (unattend.xml), to make final modifications.

To learn more about these methods, see [Modify an image](modify-an-image.md).

## File formats: WIM, FFU, VHD

To get the Windows image onto a device, you can install Windows [using Windows Setup](install-windows-from-a-usb-flash-drive.md) (.wim only) or a [deployment script](apply-images-using-dism.md) (.wim or .ffu).

Manage multiple variations of your Windows images by [combining them into a single .wim file](append-a-volume-image-to-an-existing-image-using-dism--s14.md). A single .wim file can take a fraction of the drive space that multiple image files can take. 

When you're ready to manufacture devices, [recapture and deploy the image as an .FFU file](deploy-windows-using-full-flash-update--ffu.md), because FFUs are faster to apply on a factory floor. FFUs can still be modified like .WIM files, but you can only store one variation of the image at a time.

For more details about the file formats, see [WIM vs. VHD  vs. FFU: comparing image file formats](wim-vs-ffu-image-file-formats.md).

 ## In this section

| Topic | Description |
|  --- | ---  |
| [WIM vs. VHD  vs. FFU: comparing image file formats](wim-vs-ffu-image-file-formats.md) | Learn the differences of available Windows image formats |
| [Capture and apply WIM images](capture-and-apply-an-image.md) | Capture, deploy, and modify a Windows image using WIM |
| [Capture and apply Full Flash Update (FFU) images](deploy-windows-using-full-flash-update--ffu.md) |  Capture, deploy, and modify a Windows image using FFU |
| [Modify an image](modify-an-image.md) | How to make changes to Windows images |
