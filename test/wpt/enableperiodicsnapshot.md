---
title: EnablePeriodicSnapshot 
description: EnablePeriodicSnapshot
ms.author: dawnwood
ms.date: 11/15/2018
ms.topic: article
---

# EnablePeriodicSnapshot

Enables periodic snapshot of SnapshotType for the specified process ids with the given interval in seconds. The snapshot has to be configured prior to calling this API and also needs to be disabled once the desired scenario completes.

## Syntax

```
HRESULT EnablePeriodicSnapshot
([in] SnapshotType snapshotType,
[in] ULONG interval,
[in] ULONG* pids,
  [in] ULONG cPids);
```

## Parameters

snapshotType
[in] SnapshotType. 
Note : Currently only available SnapshotType is SnapshotType_Heap
interval
[in] frequency value in seconds.
pids
[in] The pointer to an array of process ids. Up to 8 process ids can be specified 
cPids
[in] The number of process ids in the array. Maximum number is 8.

## Return Value

|Return Value | Description|
|-------------|------------|
|S_OK	| The configuration was successful for the specified process. |

## Related Topics

* [ISnapshotManager3](isnapshotmanager3.md)
* [ConfigSnapshotByPID](configsnapshotbypid.md)
* [ConfigSnapshotByPIDEx](configsnapshotbypidex.md)
* [ConfigSnapshotByProcess](configsnapshotbyprocess.md)
* [ConfigSnapshotByProcessEx](configsnapshotbyprocessex.md)
* [EnablePeriodicSnapshot](enableperiodicsnapshot.md)
* [SnapshotOnDemand](snapshotondemand.md)
* [VerifySnapshotSupported](verifysnapshotsupported.md)
