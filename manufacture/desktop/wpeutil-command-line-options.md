---

Description: 'Wpeutil Command-Line Options'
ms.assetid: 6537713a-510e-40cd-8518-d1150422bfe8
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: 'Wpeutil Command-Line Options'
ms.date: 12/20/2018
ms.topic: article
ms.custom: RS5
---

# Wpeutil Command-Line Options

The Windows PE utility (Wpeutil) is a command-line tool that enables you to run commands during a Windows PE session. For example, you can shut down or restart Windows PE, enable or disable a firewall, set language settings, and initialize a network.

Wpeutil uses the following conventions.

 <b>Wpeutil</b> {command} \[<i>argument</i>\]

For example:

```
Wpeutil Shutdown
Wpeutil Enablefirewall
Wpeutil SetMuiLanguage de-DE
```

> [!Important]
> Wpeutil can only accept one command per line.

<table>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Description</th>
</tr>
</thead>
<tr><td><b>CreatePageFile [/path=&lt;path&gt;] [/size=&lt;size&gt;]</b></td>
<td>Creates a page file to a specified path and size. The default path is C:\pagefile.sys and default size is 64 megabytes. At least one option must be specified. For example:<br></br>
<font face="courier" color="red">Wpeutil CreatePageFile /path=C:\pagefile.sys</font><br></br>
-or-<br></br>
<font face="courier" color="red">Wpeutil CreatePageFile /path=C:\pagefile.sys /size=128</font><br></br>
<b>Important</b><br></br>
If a page file exists, the <b>CreatePageFile</b> option must be set equal to or greater than the current size of the page file or the command will fail.  
</td></tr>
<tr><td><b>DisableExtendedCharactersForVolume &lt;path_on_target_volume&gt;</b></td>
<td>Disables extended character support for DOS-compatible file names (8.3 format) for the volume that contains <i>path on target volume</i>. This command only applies to NTFS volumes. The <i>path on target volume</i> must specify the root of the volume. For example:<br></br>
<font face="courier" color="red">Wpeutil DisableExtendedCharactersForVolume C:\</font><br></br>
If disabled, all files that have been created with extended characters will be converted to a short file name.  
</td></tr>
<tr><td><b>DisableFirewall</b></td>
<td>Disables a firewall. For example:<br></br>
<font face="courier" color="red">Wpeutil DisableFirewall</font>
</td></tr>
<tr><td><b>EnableExtendedCharactersForVolume &lt;path_on_target_volume&gt;</b></td>
<td>Allows 8.3 format file names to contain extended characters on the volume that contains <i>path on target volume</i>. This command only applies to NTFS volumes. The <i>path on target volume</i> must specify the root of the volume. For example:<br></br>
<font face="courier" color="red">Wpeutil EnableExtendedCharactersForVolume C:\</font> <br></br> <b>Note</b>:<br></br>If you are installing an operating system in a language that has extended characters that are enabled by default, such as ja-JP or ko-KR, or using a copy of Windows PE in a language that doesn't have extended characters enabled, such as en-US, the installation will cause a Chkdsk error during first boot. Enabling this option before you install to that volume will prevent Chkdsk command from running.
</td></tr>
<tr><td><b>EnableFirewall</b></td>
<td>Enables a firewall. For example:<br></br><font face="courier" color="red">Wpeutil EnableFirewall</font>  
</td></tr>
<tr><td><b>InitializeNetwork [/NoWait]</b></td>
<td>Initializes network components and drivers, and sets the computer name to a randomly-chosen value. The  <b>/NoWait</b> option will skip the time where your PC would otherwise wait to acquire an IP address. If you don't use  <b>/NoWait</b>, Windows PE will wait to acquire an address before it finishes loading your WinPE session.  <b>/NoWait </b> is helpful for environments that don't use DHCP. For example:<br></br><font face="courier" color="red">Wpeutil InitializeNetwork</font><br></br><font face="courier" color="red">wpeutil InitializeNetwork /NoWait</font>   
</td></tr>
<tr><td><b>ListKeyboardLayouts <i>&lt;LCID&gt;</i></b></td>
<td>Lists the supported keyboard layouts (Name and ID) for a given Locale ID (LCID) value. The keyboard layouts will also be updated in the registry under the key:  <b>HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\CurrentVersion\WinPE\KeyboardLayouts</b>. For example:<br></br><font face="courier" color="red">Wpeutil ListKeyboardLayouts 0x0409</font><br></br>-or-<br></br><font face="courier" color="red">Wpeutil ListKeyboardLayouts 1033</font><br></br>For a list of valid Locale IDs, see <a href="https://docs.microsoft.com/en-us/previous-versions/windows/embedded/ms912047(v=winembedded.10)">Microsoft Locale ID Values</a>.  
</td></tr>
<tr><td><b>Reboot</b></td>
<td>Restarts the current Windows PE session. For example:<br></br><font face="courier" color="red">Wpeutil Reboot</font>   
</td></tr>
<tr><td><b>SaveProfile</b></td>
<td>Stops logging and saves the custom profile to the location the user specified earlier with the  <b>Dism /enable-profiling</b> command. For more information about the  <b>/enable-profiling</b> command-line option, see <a href="dism-windows-pe-servicing-command-line-options.md">DISM Windows PE Servicing Command-Line Options</a>. For example:<br></br><font face="courier" color="red">Wpeutil SaveProfile profile_file_name &quot;short description&quot;</font>    
</td></tr>
<tr><td><b>SetKeyboardLayout<i>&lt;keyboard_layout_ID&gt;</i></b></td>
<td>Sets the keyboard layout in the current Windows PE session. This will take effect for processes after the command succeeds. To obtain a list of supported keyboard layouts, enter:<br></br><font face="courier" color="red">ListKeyboardLayouts LCID</font><br></br>To set the keyboard for en-US, for example:<br></br><font face="courier" color="red">Wpeutil SetKeyboardLayout 0409:00000409</font>   
</td></tr>
<tr><td><b>SetMuiLanguage <i>&lt;language-name&gt;</i></b>[;<i>&lt;language-name&gt;</i>]</td>
<td>Sets the language. <i>&lt;language-name&gt;</i> uses the international language code format (for example, en-US for the U.S. English language). You can specify multiple languages in priority order, by separating them with a semicolon. For example:<br></br><font face="courier" color="red">Wpeutil SetMuiLanguage de-DE;en-US</font>
</td></tr>
<tr><td><b><b>SetUserLocale</b> <i>&lt;language-name&gt;</i></b>[;<i>&lt;language-name&gt;</i>]</b></td>
<td>Sets the user locale. <i>&lt;language-name&gt;</i> uses the international language code format (for example, en-US for the U.S. English language). You can specify multiple languages in priority order, by separating them with a semicolon. For example:<br></br><font face="courier" color="red">Wpeutil SetUserLocale de-DE;en-US</font>                      
</td></tr>
<tr><td><b>Shutdown</b></td>
<td> Shuts down the current Windows PE session. For example:<br></br><font face="courier" color="red">Wpeutil Shutdown</font><br></br><b>Note</b>:<br></br>You can also do the following in the Command Prompt window: <ul><li>Click the  <b>Close</b> button</li><li>Type EXIT</li></ul> 
</td></tr>
<tr><td><b>UpdateBootInfo</b></td>
<td>Populates the registry with information about how Windows PE boots. <br></br>After you run this command, query the registry. For example:<br></br><font face="courier" color="red">wpeutil UpdateBootInfo reg query HKLM\System\CurrentControlSet\Control /v PEBootType</font><br></br>The results of this operation might change after loading additional driver support.<br></br>To determine where Windows PE is booted from, examine the following:<ul><li> <b>PEBootType</b>: Error, Flat, Remote, Ramdisk:SourceIdentified Ramdisk:SourceUnidentified, Ramdisk:OpticalDrive</li><li> <b>PEBootTypeErrorCode</b>: HRESULT code</li><li> <b>PEBootServerName</b>: Windows Deployment Services server name</li><li> <b>PEBootServerAddr</b>: Windows Deployment Services server IP address</li><li> <b>PEBootRamdiskSourceDrive</b>: Source drive letter, if available.</li><li> <b>PEFirmwareType</b>: Firmware boot mode: 0x1 for BIOS, 0x2 for UEFI.</li></ul><br></br>If you are not booting Windows Deployment Services, the best way to determine where Windows PE booted from is to first check for PEBootRamdiskSourceDrive registry key. If it is not present, scan the drives of the correct PEBootType and look for some kind of tag file that identifies the boot drive. </td></tr>
<tr><td><b>WaitForNetwork</b></td>
<td>Waits for the network card to be initialized. Use this command when creating scripts to make sure that the network card has been fully initialized before continuing.</td></tr>
<tr><td><b>WaitForRemovableStorage</b></td>
<td>During the Windows PE startup sequence, this command will block startup until the removable storage devices, such as USB hard drives, are initialized. For example:<br></br><font face="courier" color="red">Wpeutil WaitForRemovableStorage</font>
</td></tr>
</table>

**Related topics**

[WinPE for Windows 10](winpe-intro.md)

[WinPE: Mount and Customize](winpe-mount-and-customize.md)

[DISM Windows PE Servicing Command-Line Options](dism-windows-pe-servicing-command-line-options.md)
