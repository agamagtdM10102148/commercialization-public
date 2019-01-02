---
title: UWF\_Volume.Unprotect
description: UWF\_Volume.Unprotect
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 958533dd-ee96-498d-aed8-d4e019e8da64


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Volume.Unprotect

Disables UWF protection of the volume after the next system restart.

## Syntax

```powershell
UInt32 Unprotect();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](http://go.microsoft.com/fwlink/p/?LinkID=208318) or a [WMI error constant](http://go.microsoft.com/fwlink/p/?LinkID=208317).

## Remarks

Unprotecting the volume does not remove the [UWF\_Volume](uwf-volume.md) entry or any configuration settings from the UWF configuration registry. This means that you can unprotect a volume, and then protect it again later, while keeping any file exclusions or volume configurations that you have defined.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[UWF\_Volume](uwf-volume.md)

[Unified Write Filter](unified-write-filter.md)
