---
title: cpudisk
description: cpudisk
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2332140d-cc89-4896-b877-d0478af890a8
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.author: eliotgra
ms.date: 05/05/2017
ms.topic: article


---

# cpudisk


This action produces a text report that summarizes the various metrics regarding the CPU and disk.

```
-a cpudisk [-thread] [-exc_dpcisr] [-pids ...] [-exes ..] [-marks ..] [-times ..]
```

## Options


<a href="" id="-thread"></a>**-thread**  
Thread-level report.

<a href="" id="-exc-dpcisr"></a>**-exc\_dpcisr**  
Excludes DPC/ISR time from process/thread time if DPC/ISR events are present in the trace.

<a href="" id="-pids-pid-"></a>**-pids**<em>&lt;pid&gt;</em>  
Process identifiers to include in the report.

<a href="" id="-exes-name-"></a>**-exes**<em>&lt;name&gt;</em>  
Process names to include in the report.

<a href="" id="-marks-mark-"></a>**-marks**<em>&lt;mark&gt;</em>  
Marks that determine the time intervals in the report.

<a href="" id="-timest1-t2"></a>**-times***T1 T2*  
Timestamps that determine the time intervals in the report.

## Remarks


If no **-pids** or **-exes** are specified, all processes are included in the report.

If no **-marks** or **-times** are specified, all marks in the traces, or the trace start and end time if fewer than two marks are present in the trace, are used to determine the report time intervals.

To disable marks in the trace, specify an empty **–marks** option.

## Related topics


[Xperf Actions](xperf-actions.md)

[Time and Timestamp Formats](time-and-timestamp-formats.md)

 

 







