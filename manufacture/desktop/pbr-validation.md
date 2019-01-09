---
Description: 'Push-button reset recommended validation scenarios'
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: 'Push-button reset frequently-asked questions (FAQ)'
ms.date: 01/9/2019
ms.topic: article
---

# Push-button reset recommended validation scenarios

<table>
<tbody>
<tr><td><p><strong>Scenario</strong></p></td>
<td><p><strong>Initiation Steps</strong></p></td>
<td><p><strong>Validations</strong></p></td></tr>

<tr><td><p><strong>Reset this PC with Keep my files option from Settings</strong></p>
<p><strong>(Priority: High)</strong></p></td>

<td><ol>
<li><p>Go to Settings > Update & security > Recovery > Reset this PC: Get started > Keep my files</p></li>
<li><p>Follow the on-screen instructions</p></li>
</ol></td>

<td><ul>
<li><p>Recovery completes successfully. Login screen is shown after recovery</p></li>
<li><p>Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p></li>
<li><p>Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p></li>
<li><p>Customizations restored via extensibility points are available after recovery</p></li>
<li><p>WinRE is enabled (reagentc /info)</p>
</td></tr>

<tr><td>
<p><strong>Reset this PC with Remove everything option from Settings</strong></p>
<p><strong>(Priority: High)</strong></p></td>

<td><ol>
<li><p>Go to Settings > Update & security > Recovery > Reset this PC: Get started > Remove everything</p></li>
<li><p>When prompted, choose "Just remove my files" and follow the on-screen instructions.</p></li></td>

<td><ul>
<li><p>Recovery completes successfully. OOBE is shown after recovery</p></li>
<li><p>Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p></li>
<li><p>Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p></li>
<li><p>Customizations restored via extensibility points are available after recovery</p></li>
<li><p>WinRE is enabled (reagentc /info)</p></li>
</ul></td></tr>
<tr>
<td>
<p><strong>Creation of USB recovery drive</strong></p>
<p><strong>(Priority: High)</strong></p>
</td>
<td><ol>
<li><p>Go to Control Panel > Recovery-&gt;Create a recovery drive</p>
<p>2.&nbsp;&nbsp;&nbsp; With the "Back up system files to the recovery drive" option selected, follow the on-screen instructions</p>
</td>
<td>
<p>1.&nbsp;&nbsp;&nbsp; USB recovery drive created successfully</p>
<p>2.&nbsp;&nbsp;&nbsp; The USB recovery drive is bootable</p>
<p>3.&nbsp;&nbsp;&nbsp; Customization packages and resources under C:\Recovery\Customizations and C:\Recovery\OEM, if available, are backed up on the USB recovery drive under \sources\Customizations and \sources\OEM</p>
</td>
</tr>
<tr>
<td>
<p><strong>Bare metal recovery from USB recovery drive</strong></p>
<p><strong>(Priority: High)</strong></p>
</td>
<td>
<p>1.&nbsp;&nbsp;&nbsp; Create a USB recovery drive and attach it to the device</p>
<p>2.&nbsp;&nbsp;&nbsp; Boot the device using the USB recovery drive</p>
<p>3.&nbsp;&nbsp;&nbsp; Once booted to the USB recovery drive, select language and keyboard</p>
<p>4.&nbsp;&nbsp;&nbsp; Select Troubleshoot-&gt;Recover from a drive</p>
<p>5.&nbsp;&nbsp;&nbsp; When prompted, choose "Just remove my files" and follow the on-screen instructions</p>
</td>
<td>
<p>1.&nbsp;&nbsp;&nbsp; Recovery completes successfully and OOBE is shown after recovery</p>
<p>2.&nbsp;&nbsp;&nbsp; Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p>
<p>3.&nbsp;&nbsp;&nbsp; Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p>
<p>4.&nbsp;&nbsp;&nbsp; Customizations restored via extensibility points are available after recovery</p>
<p>5.&nbsp;&nbsp;&nbsp; Customization packages and resources, if available, are restored to C:\Recovery\Customizations and C:\Recovery\OEM</p>
<p>6.&nbsp;&nbsp;&nbsp; Partition Layout of the device is restored correctly</p>
<p>7.&nbsp;&nbsp;&nbsp; WinRE is enabled (reagentc /info)</p>
</td>
</tr>
<tr>
<td>
<p><strong>Reset this PC with Keep my files option from USB recovery drive</strong></p>
<p><strong>(Priority: Medium)</strong></p>
</td>
<td>
<p>1.&nbsp;&nbsp;&nbsp; Create a USB recovery drive and attach to the device</p>
<p>2.&nbsp;&nbsp;&nbsp; Boot the device using the USB recovery drive</p>
<p>3.&nbsp;&nbsp;&nbsp; Once booted to the USB recovery drive, select language and keyboard</p>
<p>4.&nbsp;&nbsp;&nbsp; Select Troubleshoot-&gt;Remove everything-&gt;Keep my files</p>
<p>5.&nbsp;&nbsp;&nbsp; Follow the on-screen instructions</p>
</td>
<td>
<p>1.&nbsp;&nbsp;&nbsp; Recovery completes successfully. Login screen is shown after recovery</p>
<p>2.&nbsp;&nbsp;&nbsp; Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p>
<p>3.&nbsp;&nbsp;&nbsp; Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p>
<p>4.&nbsp;&nbsp;&nbsp; Customizations restored via extensibility points are available after recovery</p>
<p>5.&nbsp;&nbsp;&nbsp; WinRE is enabled (reagentc /info)</p>
</td>
</tr>
<tr>
<td>
<p><strong>Reset this PC with Remove everything option from USB recovery drive</strong></p>
<p><strong>(Priority: Medium)</strong></p>
</td>
<td>
<p>1.&nbsp;&nbsp;&nbsp; Create a USB recovery drive and attach to the device</p>
<p>2.&nbsp;&nbsp;&nbsp; Boot the device using the USB recovery drive</p>
<p>3.&nbsp;&nbsp;&nbsp; Once booted to the USB recovery drive, select language and keyboard</p>
<p>4.&nbsp;&nbsp;&nbsp; Select Troubleshoot-&gt;Remove everything-&gt;Remove everything</p>
<p>5.&nbsp;&nbsp;&nbsp; When prompted, choose "Just remove my files" and follow the on-screen instructions</p>
</td>
<td>
<p>1.&nbsp;&nbsp;&nbsp; Recovery completes successfully. OOBE is shown after recovery</p>
<p>2.&nbsp;&nbsp;&nbsp; Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p>
<p>3.&nbsp;&nbsp;&nbsp; Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p>
<p>4.&nbsp;&nbsp;&nbsp; Customizations restored via extensibility points are available after recovery</p>
<p>5.&nbsp;&nbsp;&nbsp; WinRE is enabled (reagentc /info)</p>
</td>
</tr>
<tr>
<td>
<p><strong>Reset this PC with Keep my files option from on-disk WinRE</strong></p>
<p><strong>(Priority: Medium)</strong></p>
</td>
<td>
<p>Go to Settings > Update & security > Recovery > Advanced startup: Restart now > 
<p>1.&nbsp;&nbsp;&nbsp; Go to Settings-&gt;Update &amp; security-&gt;Recovery-&gt;Advanced startup-&gt;Troubleshoot-&gt;Remove everything-&gt;Keep My Files</p>
<p>2.&nbsp;&nbsp;&nbsp; Once booted to WinRE, follow the on-screen instructions</p>
</td>
<td>
<p>1.&nbsp;&nbsp;&nbsp; Recovery completes successfully. Login screen is shown after recovery</p>
<p>2.&nbsp;&nbsp;&nbsp; Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p>
<p>3.&nbsp;&nbsp;&nbsp; Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p>
<p>4.&nbsp;&nbsp;&nbsp; Customizations restored via extensibility points are available after recovery</p>
<p>5.&nbsp;&nbsp;&nbsp; WinRE is enabled (reagentc /info)</p>
</td>
</tr>
<tr>
<td>
<p><strong>Reset this PC with Remove everything option from on-disk WinRE</strong></p>
<p><strong>(Priority: Medium)</strong></p>
</td>
<td>
<p>1.&nbsp;&nbsp;&nbsp; Go to Settings-&gt;Update &amp; security-&gt;Recovery-&gt;Advanced startup-&gt;Troubleshoot-&gt;Remove everything-&gt;Remove everything</p>
<p>2.&nbsp;&nbsp;&nbsp; When prompted, choose "Just remove my files"</p>
<p>3.&nbsp;&nbsp;&nbsp; Follow the on-screen instructions</p>
</td>
<td>
<p>1.&nbsp;&nbsp;&nbsp; Recovery completes successfully. OOBE is shown after recovery</p>
<p>2.&nbsp;&nbsp;&nbsp; Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p>
<p>3.&nbsp;&nbsp;&nbsp; Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p>
<p>4.&nbsp;&nbsp;&nbsp; Customizations restored via extensibility points are available after recovery</p>
<p>5.&nbsp;&nbsp;&nbsp; WinRE is enabled (reagentc /info)</p>
</td>
</tr>
<tr>
<td>
<p><strong>Reset this PC with Remove everything and Remove files and clean the drive options</strong></p>
<p><strong>(Priority: Low)</strong></p>
</td>
<td>
<p>1.&nbsp;&nbsp;&nbsp; Go to Settings-&gt;Update &amp; security-&gt;Recovery-&gt;Advanced startup-&gt;Troubleshoot-&gt;Remove everything-&gt;Remove everything</p>
<p>2.&nbsp;&nbsp;&nbsp; When prompted, choose "Fully clean the drive" and follow the on-screen instructions</p>
</td>
<td>
<p>1.&nbsp;&nbsp;&nbsp; Recovery completes successfully. OOBE is shown after recovery</p>
<p>2.&nbsp;&nbsp;&nbsp; Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p>
<p>3.&nbsp;&nbsp;&nbsp; Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p>
<p>4.&nbsp;&nbsp;&nbsp; Customizations restored via extensibility points are available after recovery</p>
<p>5.&nbsp;&nbsp;&nbsp; WinRE is enabled (reagentc /info)</p>
</td>
</tr>
<tr>
<td>
<p><strong>Bare metal recovery with "Clean the drive" option</strong></p>
<p><strong>(Priority: Low)</strong></p>
</td>
<td>
<p>1.&nbsp;&nbsp;&nbsp; Create a USB recovery drive and attach it to the device</p>
<p>2.&nbsp;&nbsp;&nbsp; Boot the device using the USB recovery drive</p>
<p>3.&nbsp;&nbsp;&nbsp; Once booted to the USB recovery drive, select language and keyboard</p>
<p>4.&nbsp;&nbsp;&nbsp; Select Troubleshoot-&gt;Recover from a drive</p>
<p>5.&nbsp;&nbsp;&nbsp; When prompted, choose "Fully clean the drive" and follow the on-screen instructions</p>
</td>
<td>
<p>1.&nbsp;&nbsp;&nbsp; Recovery completes successfully. OOBE is shown after recovery</p>
<p>2.&nbsp;&nbsp;&nbsp; Classic Windows applications captured via ScanState.exe are reinstalled and working correctly</p>
<p>3.&nbsp;&nbsp;&nbsp; Installed drivers are available and corresponding devices working as expected. Applications installed via drivers' setup.exe will NOT be restored unless captured via ScanState.exe</p>
<p>4.&nbsp;&nbsp;&nbsp; Customizations restored via extensibility points are available after recovery</p>
<p>5.&nbsp;&nbsp;&nbsp; Customization packages and resources, if available, are restored to C:\Recovery\Customizations and C:\Recovery\OEM</p>
<p>6.&nbsp;&nbsp;&nbsp; Partition Layout of the device is restored correctly</p>
<p>7.&nbsp;&nbsp;&nbsp; WinRE is enabled (reagentc /info)</p>
</td>
</tr>
</tbody>
</table>


