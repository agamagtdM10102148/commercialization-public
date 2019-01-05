---
author: kpacquer
Description: Learn how to to work with Windows images
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: Work with Windows images
ms.author: kenpacq
ms.date: 1/4/2019
ms.topic: article
ms.custom: RS5
---

# Work with Windows images

The Windows 10 OPK includes an image file, **install.wim**, which contains the operating system files for your Windows edition.

Starting by deploying this image to a device, add your customizations to it, test, and incorporate those changes into your images, iterating until you're ready to put the image onto the factory floor.

## File formats: WIM, FFU, VHD

We recommend starting with using this WIM file (install.wim), because it's faster to work with, and you can save multiple iterations of your image into the same image file, often with little additional storage required.

To get a .WIM image onto a device, you can install Windows [using Windows Setup](install-windows-from-a-usb-flash-drive.md) or a [deployment script](apply-images-using-dism.md).

Later, when you're getting ready to manufacture devices, [recapture and deploy the image as an .FFU file](deploy-windows-using-full-flash-update--ffu
.md), because FFUs are faster to apply on a factory floor. FFUs can still be modified like .WIM files, but you can only store one iteration of the image at a time.

For more details about the file formats, see [WIM vs. VHD  vs. FFU: comparing image file formats](wim-vs-ffu-image-file-formats.md).

 ## In this section

| Topic | Description |
|  --- | ---  |
| [WIM vs. VHD  vs. FFU: comparing image file formats](wim-vs-ffu-image-file-formats.md) | Learn the differences of available Windows image formats |
| [Capture and apply WIM images](capture-and-apply-an-image.md) | Capture, deploy, and modify a Windows image using WIM |
| [Capture and apply Full Flash Update (FFU) images](deploy-windows-using-full-flash-update--ffu.md) |  Capture, deploy, and modify a Windows image using FFU |
| [Modify an image](modify-an-image.md) | How to make changes to Windows images |
