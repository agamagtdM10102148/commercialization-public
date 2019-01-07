---
title: UWF\_Overlay.GetOverlayFiles
description: UWF\_Overlay.GetOverlayFiles
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6f8f544d-0f97-47ca-8ab4-f452e457e788


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Overlay.GetOverlayFiles

Returns a list of files of a volume that were cached in the Unified Write Filter (UWF) overlay.

## Syntax

```powershell
UInt32 GetOverlayFiles(
    [in] string Volume,
    [out, EmbeddedInstance("UWF_OverlayFile")] string OverlayFiles[]
);
```

## Parameters

<a href="" id="volume"></a>*Volume*
A string that specifies the drive letter or volume name.

<a href="" id="overlayfiles"></a>*OverlayFiles*
An array of **UWF\_OverlayFiles** objects embedded as strings.

## Return Value

Returns an HRESULT value that indicates [WMI status](http://go.microsoft.com/fwlink/p/?LinkID=208318) or a [WMI error](http://go.microsoft.com/fwlink/p/?LinkID=208317).

## <a href="" id="bkmk-remarks"></a>Remarks

You must use an administrator account to access this method.

The **GetOverlayFiles** method is intended to be used as a diagnostic tool.

Do not base decisions about what to commit based on this method’s output.

You should be aware of the following limitations:

* This method is only supported on the NTFS file system.
* This method requires a significant amount of free system memory to succeed (in a linear relationship to overlay usage). The method call fails when there is insufficient memory available to complete the call.
* This method requires significant time to complete (in an exponential relationship to overlay usage).
* This method may show files that are affected by seemingly unrelated operations to both registry and file exclusions and commits.

You should also be aware of the following items when you use the **GetOverlayFiles** method:

* Files that were committed with the `uwfmgr.exe file commit` command are also contained in the overlay files list.
* Excluded files may be contained in the overlay files list.
* Files that are smaller than the cluster size (for example, 4 KB in most cases) will not be listed even if they are cached in overlay.
* Changes and deletions in excluded directories, excluded files, or excluded registry items add to overlay usage.
* File and registry commits add to overlay usage.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[UWF\_Overlay](uwf-overlay.md)

[Unified Write Filter](unified-write-filter.md)
