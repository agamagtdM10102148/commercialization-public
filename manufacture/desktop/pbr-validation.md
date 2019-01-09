---
Description: 'Push-button reset recommended validation scenarios'
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: 'Push-button reset frequently-asked questions (FAQ)'
ms.date: 1/9/2019
ms.topic: article
---

# Push-button reset recommended validation scenarios

<table>
<tbody>
<tr><td>
<p><strong>Scenario</strong></p></td>
<td><p><strong>Initiation steps</strong></p></td>
<td><p><strong>Validations</strong></p></td></tr>

<tr><td>
<p><strong>Reset this PC with Keep my files option from Settings</strong></p>
<p><strong>(Priority: High)</strong></p>
</td>

<td><ol>
<li><p>Select Settings > Update & security > Recovery > Reset this PC: Get started > Keep my files</p></li>
<li><p>Follow the on-screen instructions</p></li>
</ol></td>

<td><ul>
<li><p>Recovery completes successfully. Login screen is shown after recovery</p></li>
<li><p>Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p></li>
<li><p>Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p></li>
<li><p>Customizations restored via extensibility points are available after recovery</p></li>
<li><p>WinRE is enabled (reagentc /info)</p></li>
</ul></td></tr>

<tr><td>
<p><strong>Reset this PC with Remove everything option from Settings</strong></p>
<p><strong>(Priority: High)</strong></p>
</td>

<td><ol>
<li><p>Select Settings > Update & security > Recovery > Reset this PC: Get started > Remove everything</p></li>
<li><p>When prompted, choose "Just remove my files" and follow the on-screen instructions.</p></li>
</ol></td>

<td><ul>
<li><p>Recovery completes successfully. OOBE is shown after recovery</p></li>
<li><p>Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p></li>
<li><p>Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p></li>
<li><p>Customizations restored via extensibility points are available after recovery</p></li>
<li><p>WinRE is enabled (reagentc /info)</p></li>
</ul></td></tr>

<tr><td>
<p><strong>Creation of USB recovery drive</strong></p>
<p><strong>(Priority: High)</strong></p>
</td>

<td><ol>
<li><p>Select Control Panel > search for "Recovery" > Create a recovery drive</p></li>
<li><p>With the "Back up system files to the recovery drive" option selected, follow the on-screen instructions</p></li>
</ol></td>

<td><ul>
<li><p>USB recovery drive created successfully</p></li>
<li><p>The USB recovery drive is bootable</p></li>
<li><p>Customization packages and resources under C:\Recovery\Customizations and C:\Recovery\OEM, if available, are backed up on the USB recovery drive under \sources\Customizations and \sources\OEM</p></li>
</ul></td></tr>

<tr><td>
<p><strong>Bare metal recovery from USB recovery drive</strong></p>
<p><strong>(Priority: High)</strong></p>
</td>

<td><ol>
<li><p>Create a USB recovery drive and attach it to the device</p></li>
<li><p>Boot the device using the USB recovery drive</p></li>
<li><p>Once booted to the USB recovery drive, select language and keyboard</p></li>
<li><p>Select Troubleshoot > Recover from a drive</p></li>
<li><p>When prompted, choose "Just remove my files" and follow the on-screen instructions</p></li>
</ol></td>

<td><ul>
<li><p>Recovery completes successfully and OOBE is shown after recovery</p></li>
<li><p>Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p></li>
<li><p>Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p></li>
<li><p>Customizations restored via extensibility points are available after recovery</p></li>
<li><p>Customization packages and resources, if available, are restored to C:\Recovery\Customizations and C:\Recovery\OEM</p></li>
<li><p>Partition layout of the device is restored correctly</p></li>
<li><p>WinRE is enabled (reagentc /info)</p></li>
</ul></td></tr>

<tr><td>
<p><strong>Reset this PC with Keep my files option from USB recovery drive</strong></p>
<p><strong>(Priority: Medium)</strong></p>
</td>

<td><ol>
<li><p>Create a USB recovery drive and attach to the device</p></li>
<li><p>Boot the device using the USB recovery drive</p></li>
<li><p>Once booted to the USB recovery drive, select language and keyboard</p></li>
<li><p>Select Troubleshoot > Reset this PC > Remove everything > Keep my files</p></li>
<li><p>Follow the on-screen instructions</p></li>
</ol></td>

<td><ul>
<li><p>Recovery completes successfully. Login screen is shown after recovery</p></li>
<li><p>Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p></li>
<li><p>Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p></li>
<li><p>Customizations restored via extensibility points are available after recovery</p></li>
<li><p>WinRE is enabled (reagentc /info)</p></li>
</ul></td></tr>

<tr><td>
<p><strong>Reset this PC with Remove everything option from USB recovery drive</strong></p>
<p><strong>(Priority: Medium)</strong></p>
</td>

<td><ol>
<li><p>Create a USB recovery drive and attach to the device</p></li>
<li><p>Boot the device using the USB recovery drive</p></li>
<li><p>Once booted to the USB recovery drive, select language and keyboard</p></li>
<li><p>Select Troubleshoot > Reset this PC: Get started > Remove everything</p></li>
<li><p>When prompted, choose "Just remove my files" and follow the on-screen instructions</p></li>
</ol></td>

<td><ul>
<li><p>Recovery completes successfully. OOBE is shown after recovery</p></li>
<li><p>Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p></li>
<li><p>Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p></li>
<li><p>Customizations restored via extensibility points are available after recovery</p></li>
<li><p>WinRE is enabled (reagentc /info)</p></li>
</ul></td></tr>

<tr><td>
<p><strong>Reset this PC with Keep my files option from on-disk WinRE</strong></p>
<p><strong>(Priority: Medium)</strong></p>
</td>

<td><ol>
<li><p>Select Settings > Update & security > Recovery > Advanced startup: Restart now. The device reboots to WinRE.</p></li>
<li><p>Select Troubleshoot > Reset this PC > Keep my files</p></li>
<li><p>Follow the on-screen instructions</p></li>
</ol></td>

<td><ul>
<li><p>Recovery completes successfully. Login screen is shown after recovery</p></li>
<li><p>Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p></li>
<li><p>Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p></li>
<li><p>Customizations restored via extensibility points are available after recovery</p></li>
<li><p>WinRE is enabled (reagentc /info)</p></li>
</ul></td></tr>

<tr><td>
<p><strong>Reset this PC with Remove everything option from on-disk WinRE</strong></p>
<p><strong>(Priority: Medium)</strong></p>
</td>

<td><ol>
<li><p>Select Settings > Update & security > Recovery > Advanced startup: Restart now. The device reboots to WinRE.</p></li>
<li><p>Select Troubleshoot > Reset this PC > Remove everything</p></li>
<li><p>When prompted, choose "Just remove my files"</p></li>
<li><p>Follow the on-screen instructions</p></li>
</ol></td>

<td><ul>
<li><p>Recovery completes successfully. OOBE is shown after recovery</p></li>
<li><p>Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p></li>
<li><p>Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p></li>
<li><p>Customizations restored via extensibility points are available after recovery</p></li>
<li><p>WinRE is enabled (reagentc /info)</p></li>
</ul></td></tr>

<tr><td>
<p><strong>Reset this PC with Remove everything and Remove files and clean the drive options</strong></p>
<p><strong>(Priority: Low)</strong></p>
</td>

<td><ol>
<li><p>Select Settings > Update & security > Recovery > Advanced startup: Restart now. The device reboots to WinRE.</p></li>
<li><p>Select Troubleshoot > Reset this PC > Remove everything</p></li>
<li><p>When prompted, choose "Fully clean the drive" and follow the on-screen instructions</p></li>
</ol></td>

<td><ul>
<li><p>Recovery completes successfully. OOBE is shown after recovery</p></li>
<li><p>Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p></li>
<li><p>Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p></li>
<li><p>Customizations restored via extensibility points are available after recovery</p></li>
<li><p>WinRE is enabled (reagentc /info)</p></li>
</ul></td></tr>

<tr><td>
<p><strong>Bare metal recovery with "Clean the drive" option</strong></p>
<p><strong>(Priority: Low)</strong></p>
</td>

<td><ol>
<li><p>Create a USB recovery drive and attach it to the device</p></li>
<li><p>Boot the device using the USB recovery drive</p></li>
<li><p>Once booted to the USB recovery drive, select language and keyboard</p></li>
<li><p>Select Troubleshoot > Recover from a drive</p></li>
<li><p>When prompted, choose "Fully clean the drive" and follow the on-screen instructions</p></li>
</ol></td>

<td><ul>
<li><p>Recovery completes successfully. OOBE is shown after recovery</p></li>
<li><p>Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p></li>
<li><p>Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p></li>
<li><p>Customizations restored via extensibility points are available after recovery</p></li>
<li><p>Customization packages and resources, if available, are restored to C:\Recovery\Customizations and C:\Recovery\OEM</p></li>
<li><p>Partition layout of the device is restored correctly</p></li>
<li><p>WinRE is enabled (reagentc /info)</p></li>
</ul></td></tr>
</tbody>
</table>

**Related topics**

[Push-button reset overview](push-button-reset-overview.md)
