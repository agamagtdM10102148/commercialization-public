---
title: WillReboot
description: WillReboot
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b46a9c74-8bd4-4be9-9f39-b1bc3abb43c7
ms.mktglfcycl: deploy
ms.sitesec: msdn
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# WillReboot


`WillReboot` specifies in what circumstances to restart the computer after running a synchronous command.

If there are any additional commands that have yet to be processed before the computer restarts, those commands are saved. After the restart, the remaining synchronous commands resume.

[RunSynchronous](microsoft-windows-deployment-runsynchronous.md) commands run in the user context in the auditUser configuration pass and in the system context in the specialize pass.

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Always</strong></p></td>
<td><p>Specifies that the computer always restarts immediately after the command has run.</p></td>
</tr>
<tr class="even">
<td><p><strong>OnRequest</strong></p></td>
<td><p>Specifies that the computer restarts after the command has run, if requested. See the Remarks for a table of possible return codes.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Never</strong></p></td>
<td><p>Specifies that the computer does not restart after the command has run. This is the default value.</p></td>
</tr>
</tbody>
</table>

 

## Remarks


If the value of `WillReboot` is **OnRequest**, the synchronous command must return one of the following codes.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Return code</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>0</strong></p></td>
<td><p>The command was successful. No reboot is required.</p></td>
</tr>
<tr class="even">
<td><p><strong>1</strong></p></td>
<td><p>The command was successful. An immediate reboot is required. Then, the next command can be started.</p></td>
</tr>
<tr class="odd">
<td><p><strong>2</strong></p></td>
<td><p>The command is still in process. An immediate reboot is required. Then, the same command must be restarted. This code can be returned multiple times.</p></td>
</tr>
<tr class="even">
<td><p>Other codes</p></td>
<td><p>The command failed. An error must be returned and installation terminated.</p></td>
</tr>
</tbody>
</table>

 

## Valid Configuration Passes


auditUser

specialize

## Parent Hierarchy


[Microsoft-Windows-Deployment](microsoft-windows-deployment.md) | [RunSynchronous](microsoft-windows-deployment-runsynchronous.md) | [RunSynchronousCommand](microsoft-windows-deployment-runsynchronous-runsynchronouscommand.md) | **WillReboot**

## Applies To


For the list of the supported Windows editions and architectures that this component supports, see [Microsoft-Windows-Deployment](microsoft-windows-deployment.md).

## XML Example


The following XML output shows how to set synchronous commands.

```
<RunSynchronous>
   <RunSynchronousCommand wcm:action="add">
      <Credentials>
         <Domain>MyDomain</Domain>
         <Password>MyPassword</Password>
         <Username>MyUsername</Username>
      </Credentials>
      <Description>MySynchCommand1</Description>
      <Order>1</Order>
      <Path>\\network\server\share\filename</Path>
      <WillReboot>OnRequest</WillReboot>
   </RunSynchronousCommand>
   <RunSynchronousCommand wcm:action="add">
      <Credentials>
         <Domain>MyDomain</Domain>
         <Password>MyPassword</Password>
         <Username>MyUsername</Username>
      </Credentials>
      <Description>MySynchCommand2</Description>
      <Order>2</Order>
      <Path>\\network\server\share\filename</Path>
      <WillReboot>OnRequest</WillReboot>
   </RunSynchronousCommand>
</RunSynchronous>
```

## Related topics


[RunSynchronousCommand](microsoft-windows-deployment-runsynchronous-runsynchronouscommand.md)

 

 







