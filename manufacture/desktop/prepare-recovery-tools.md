---

Description: Prepare recovery tools for your Windows images
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: Prepare recovery tools for your Windows images
ms.date: 12/18/2018
ms.topic: article
ms.custom: RS5
---

# Prepare recovery tools for your Windows images

> [!Tip]
> If you want to reset a computer that runs Windows 10, see [Recovery options in Windows 10](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options).

OEMs: When you create custom Windows 10 and Windows Server images, update the recovery tools.

## [Windows Recovery Environment (Windows RE)](windows-recovery-environment--windows-re--technical-reference.md)
Both Windows 10 and Windows Server include a recovery environment that can repair common causes of unbootable operating systems.

Some customizations that you add to Windows should also be added to Windows RE:

| Customization | What do I need to update? | 
|---------------|---------------------------|
| **Boot-critical drivers** or **languages** | If you add these to your Windows image, [add those same drivers and languages (when available) to Windows RE](customize-windows-re.md). |
| **Custom recovery tools** | [Add a custom tool to the Windows RE boot options menu](add-a-custom-tool-to-the-windows-re-boot-options-menu.md) | 
| **Dedicated hardware button** | [Add a dedicated hardware button to boot immediately to WinRE](add-a-hardware-recovery-button-to-start-windows-re.md) |

More options:

* [Deploy Windows RE](deploy-windows-re.md): If you're deploying Windows using a .wim file, use these instrutions to deploy the recovery partition and hide the recovery drive letters.



## [Push-button reset](push-button-reset-overview.md)
Windows 10 users can reset their device, either keeping data and apps intact or resetting it for a new user. 

Some customizations that you add to Windows should also be added to the push-button reset tools:

<table>
<tr><th>Customization</th><th>What do I need to update? </th></tr>
<tr><td><b>Universal Windows apps</b>
</td><td>Automatically restored.
</td></tr>
<tr><td><b>Drivers</b> installed using an .inf file
</td><td>Automatically restored.
</td></tr>
<tr><td><b>Desktop apps</b> or <br/>
<b>drivers</b> installed using an .exe file
</td><td><a href="deploy-push-button-reset-features.md">Capture into a provisioning package</a> or a <a href="siloed-provisioning-packages.md">siloed provisioning package (SPP)</a>.
</td></tr>
<tr><td><b>Out of Box Experience customizations</b>, <br/>
<b>Start Menu</b>, and <br/>
<b>Unattend.xml settings</b>
</td><td>In Windows 10, version 1809 and later, save a copy in your <a href="recovery-strategy-for-common-customizations.md#auto-apply">Auto-apply folders</a>. <br/>
In earlier versions or as an alternative, use <a href="recovery-strategy-for-common-customizations.md#restoring_settings_using_unattend.xml_and_extensibility_scripts">extensibility scripts instead.
</td></tr>
<tr><td><b>Settings</b> created using Windows Configuration Designer (also known as ICD) 
</td><td>Copy the settings .ppkg file to C:\Recovery\Customizations. 
</td></tr>
</table>



More options: 

* Use [Compact OS, single-sourcing, and image optimization](compact-os.md) to save space on the disk.

## [Bare metal recovery](bare-metal-recovery.md)
If the user needs to replace their hard drive or completely wipe it, they can use bootable USB key to restore their device.

Some customizations that you add to Windows should also be added to the push-button reset tools:
<table>
<tr><th>Customization</th><th>What do I need to update? </th></tr>
<tr><td><b>Drive partitions</b>
</td><td>If your device uses a non-standard drive partition layout, <a href="bare-metal-resetrecovery-enable-your-users-to-create-media-and-to-recover-hard-drive-space.md">update bare-metal reset so users can create their own recovery media.
</td></tr>
<tr><td>Ship <b>USB recovery media</b> to customers
</td><td><a href="create-media-to-run-push-button-reset-features-s14.md">Create recovery media while deploying new devices
</td></tr>

</table>

## Reference
* [How push-button reset features work](how-push-button-reset-features-work.md)
* [Push-button reset frequently-asked questions (FAQ)](pbr-faq.md)
* [REAgentC command-line options](reagentc-command-line-options.md)
* [ResetConfig XML reference](resetconfig-xml-reference-s14.md)
* [WinREConfig XML reference](winreconfig-xml-reference.md)
* [Windows RE troubleshooting features](windows-re-troubleshooting-features.md)
