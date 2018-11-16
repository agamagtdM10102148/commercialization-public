---
title: Link1
description: Link1
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6ae9b6f5-2cd6-476e-aec9-8163137e377f
ms.mktglfcycl: deploy
ms.sitesec: msdn
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# Link1


`Link1` specifies the URL or file path for the first of two links that describe a recommended online backup service in the Windows Server Backup menus.

Before an online backup service is installed, Windows displays a description of a recommended online backup service. This includes one or two description lines and one or two links that provide more information.

The link is added to the resource DLL file that the [ResourceDll](microsoft-windows-blb-wsb-online-main-resourcedll.md) setting specifies. The icon may be localized for different regions. For information about how to create localized versions for these settings, see [Using the MUI with Applications](http://go.microsoft.com/fwlink/?LinkId=140252).

The link in the Resource DLL file must be a text string. It must begin with `http://` or `file://`. For example, the link may resemble the following:

`file://%ProgramFiles%\Fabrikam\FabrikamCloudBackupService-TrialVersion.exe`

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>ResourceID</em></p></td>
<td><p>Specifies the resource ID from the resource DLL file for the link.</p>
<p><em>ResourceID</em> is an integer.</p></td>
</tr>
</tbody>
</table>

 

## Valid Configuration Passes


specialize

oobeSystem

## Parent Hierarchy


[Microsoft-Windows-BLB-WSB-Online-Main](microsoft-windows-blb-wsb-online-main.md) | **Link1**

## Applies To


For the list of the Windows editions and architectures that this component supports, see [Microsoft-Windows-BLB-WSB-Online-Main](microsoft-windows-blb-wsb-online-main.md).

## XML Example


The following XML output shows how to describe a recommended online backup service. This includes provider information, descriptions, links, and an icon.

```
<EnableOnlineBackup>true</EnableOnlineBackup>
<ResourceDll>%ProgramFiles%\Microsoft Shared\Resource.dll</ResourceDll>
<ProviderName>100</ProviderName>
<Icon>101</Icon>
<Link1>200</Link1>
<Link1Text>201<Link1Text>
<DescriptionText1>202</DescriptionText1>
<Link2>300</Link2>
<Link2Text>301<Link2Text>
<DescriptionText2>302</DescriptionText2>
```

## Related topics


[Microsoft-Windows-BLB-WSB-Online-Main](microsoft-windows-blb-wsb-online-main.md)

 

 







