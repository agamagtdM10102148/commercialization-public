---
title: Answer Files Overview
description: Answer Files Overview
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d7a2667e-a5d0-4d8a-99c4-1e0078218e39
ms.mktglfcycl: deploy
ms.sitesec: msdn


ms.date: 05/02/2017
ms.topic: article


---
# Answer Files Overview

An answer file is an XML-based file that contains setting definitions and values to use during Windows Setup. In an answer file, you specify various setup options. These options include how to partition disks, where to find the Windows image that will be installed, and which product key to apply. You can also specify values that apply to the Windows installation, such as names of user accounts and display settings. The answer file for Setup is typically called Unattend.xml.

Answer files that are created in Windows System Image Manager (Windows SIM) are associated with a particular Windows image. You can therefore validate the settings in the answer file to the settings in the Windows image. However, because any answer file can be used to install any Windows image, if there are settings in the answer file for components that are not in the Windows image, those settings are ignored. For information about how to create answer files, see [Best Practices for Authoring Answer Files](best-practices-for-authoring-answer-files.md).

## Sections of an Answer File

Settings in an answer file are organized into two sections, components and packages.

### Components

The components section of an answer file contains all the component settings that are applied during Windows Setup. Components are organized into various configuration passes: **windowsPE**, **offlineServicing**, **generalize**, **specialize**, **auditSystem**, **auditUser**, and **oobeSystem**. Each configuration pass represents a different phase of Windows Setup. Settings can be applied during one or more passes. If a setting can be applied in more than one configuration pass, you can select the pass in which to apply the setting.

For more information about the different components and settings that you can configure in an answer file, see the [Unattended Windows Setup Reference](https://docs.microsoft.com/en-us/windows-hardware/customize/desktop/unattend/) (unattend.chm).

### Packages

Microsoft uses packages to distribute software updates, service packs, and language packs. Packages can also contain Windows features.

You can configure packages to be added to a Windows image or removed from a Windows image. You can also change the settings for features in a package.

The Windows Foundation Package, included in all Windows client and server images, includes Windows features. For example, Windows Media Player, Games, and Backup are all Windows features in the Windows Foundation Package.

Features are either enabled or disabled in Windows. If a Windows feature is enabled, the resources, executable files, and settings for that feature are available to users on the system. If a Windows feature is disabled, the package resources are not available, but the resources are not removed from the system.

Some Windows features may require that you install other features before you can enable the installed version of Windows. You must validate your answer file and add any required packages.

For example, you can disable the Windows Media Player feature to prevent end users from running Windows Media Player. However, because the package is disabled, those resources are not removed from the Windows image.

Packages in an answer file are applied to the Windows image during the **offlineServicing** configuration pass. You can also use Deployment Image Servicing and Management (DISM) to add packages to an offline Windows image.

## Related topics

[Create or Open an Answer File](create-or-open-an-answer-file.md)

[Windows System Image Manager Overview Topics](windows-system-image-manager-overview-topics.md)
