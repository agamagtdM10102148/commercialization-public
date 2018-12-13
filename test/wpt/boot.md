---
title: boot
description: boot
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c6bf946c-9da7-4147-a37e-c117e1ea1fff
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.author: eliotgra
ms.date: 05/05/2017
ms.topic: article


---

# boot


This action produces an XML report that summarizes the various metrics in boot.

```
-a boot [-minCPUToShow <n>] [-maxFilesToShow <n>] [-expectedProcessesFile <file name>] [-minIntervalToShow <n>] [-userShellExecutable]
```

## Options


<a href="" id="-mincputoshow-n-"></a>**-minCPUToShow**<em>&lt;n&gt;</em>  
*&lt;n&gt;* indicates the minimum percentage of CPU usage to show, in the range 0-100.

<a href="" id="-maxfilestoshow-n-"></a>**-maxFilesToShow**<em>&lt;n&gt;</em>  
*&lt;n&gt;* indicates the maximum number of files to show.

<a href="" id="-expectedprocessesfile-file-name-"></a>**-expectedProcessesFile**<em>&lt;file name&gt;</em>  
*&lt;file name&gt;* specifies a text file that contains a list of expected process names.

<a href="" id="-minintervaltoshow-n-"></a>**-minIntervalToShow**<em>&lt;n&gt;</em>  
*&lt;n&gt;* indicates the minimum interval time to show, in microseconds. The default value is 10.

<a href="" id="-usershellexecutable"></a>**-userShellExecutable**  
User shell executable to locate in the trace. The default is Explorer.exe.

## Related topics


[Xperf Actions](xperf-actions.md)

 

 







