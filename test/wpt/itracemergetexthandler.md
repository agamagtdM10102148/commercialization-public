---
title: ITraceMergeTextHandler
description: ITraceMergeTextHandler
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 0827802d-a62a-4420-8bb9-83f8af650669
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.author: eliotgra
ms.date: 05/05/2017
ms.topic: article


---

# ITraceMergeTextHandler


Obtains the text and other metadata that was added by the user.

## Syntax


```
{
    [propget, id(1), helpstring("Count")] HRESULT Count([out, retval] ULONG* cText);
    [id(2), helpstring("GetText")] HRESULT GetText([in] ULONG iText, [out] BSTR* pbstrText);
    [id(3), helpstring("WaitForText")] HRESULT WaitForText([in] ULONG Milliseconds);
    [id(4), helpstring("GetFileName")] HRESULT GetFileName([out] BSTR* pbstrFileName);
    [id(5), helpstring("GetNGenPdbsPath")] HRESULT GetNGenPdbsPath([out] VARIANT_BOOL* pfEnable, [out] BSTR* pbstrNGenPdbsCachePath, [out] BSTR* pbstrNGenPdbsTargetPath);
};
```

## Functions


The following table describes the functions that this interface provides.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Function</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>propget</strong></p></td>
<td><p>Returns the value of the specified property.</p></td>
</tr>
<tr class="even">
<td><p><a href="gettext.md" data-raw-source="[GetText](gettext.md)">GetText</a></p></td>
<td><p>Obtains the string from the specified file.</p></td>
</tr>
<tr class="odd">
<td><p><a href="waitfortext.md" data-raw-source="[WaitForText](waitfortext.md)">WaitForText</a></p></td>
<td><p>Waits until the user adds the appropriate text strings and calls.</p></td>
</tr>
<tr class="even">
<td><p><a href="getfilename.md" data-raw-source="[GetFileName](getfilename.md)">GetFileName</a></p></td>
<td><p>Obtains the file name.</p></td>
</tr>
<tr class="odd">
<td><p><a href="getngenpdbspath.md" data-raw-source="[GetNGenPdbsPath](getngenpdbspath.md)">GetNGenPdbsPath</a></p></td>
<td><p>Obtains the path to NGEN PDBs.</p></td>
</tr>
</tbody>
</table>

 

## Properties


The following table describes the properties that this interface provides.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Count</strong></p></td>
<td><p>Indicates the number of text entries added by the user.</p></td>
</tr>
</tbody>
</table>

 

## Related topics


[Interfaces](interfaces-wprcontrol.md)

 

 







