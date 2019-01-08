---
title: UWF\_Servicing.Disable
description: UWF\_Servicing.Disable
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6196d90a-1414-4e6b-b2f2-79cf0dd6d184


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Servicing.Disable

Disables Unified Write Filter (UWF) servicing mode.

## Syntax

```powershell
UInt32 Disable();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](http://go.microsoft.com/fwlink/p/?LinkID=208318) or a [WMI error](http://go.microsoft.com/fwlink/p/?LinkID=208317).

## Remarks

When this method is called, the system will leave servicing mode in the next session after a restart.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[UWF\_Servicing](uwf-servicing.md)

[Unified Write Filter](unified-write-filter.md)
