---
title: LoadFromFile
description: LoadFromFile
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 8816f97e-aa11-4e02-ade7-537e0b288cce
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.author: eliotgra
ms.date: 05/05/2017
ms.topic: article


---

# LoadFromFile


Loads a profile from a file.

## Syntax


```
HRESULT LoadFromFile
  ([in] BSTR bstrProfileName,
  [in] BSTR bstrFileName)
;
```

## Parameters


<a href="" id="bstrprofilename"></a>*bstrProfileName*  
\[in\] The name of the profile to load.

<a href="" id="bstrfilename"></a>*bstrFileName*  
\[in\] The name of the file that contains the profile.

## Return Value


The following table describes possible return values.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Return Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>S_OK</p></td>
<td><p>Indicates success.</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>One or more arguments are invalid. Use <a href="iparsingerrorinfo.md" data-raw-source="[IParsingErrorInfo](iparsingerrorinfo.md)">IParsingErrorInfo</a> to obtain detailed error information.</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_VALIDATE_PROFILE</p></td>
<td><p>The library failed to validate the profile. Use <strong>IParsingErrorInfo</strong> to obtain detailed error information.</p></td>
</tr>
</tbody>
</table>

 

## Related topics


[IProfile](iprofile.md)

 

 







