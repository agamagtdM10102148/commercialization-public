---
title: services
description: services
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 139a09db-6c62-449a-9369-2219cc99e823
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.author: eliotgra
ms.date: 05/05/2017
ms.topic: article


---

# services


This action produces a text file that summarizes metrics related to services.

```
-a services [-range T1 T2] [-poiThreshold_ContainerInit <t>] [-poiThreshold_ImageLoad <t>] [-poiThreshold_ServiceInit <t>]
```

## Parameters


<a href="" id="-ranget1-t2"></a>**-range***T1 T2*  
Shows data between times *T1* and *T2*, both in microseconds.

<a href="" id="-poithreshold-containerinit-t-"></a>**-poiThreshold\_ContainerInit**<em>&lt;t&gt;</em>  
Flags any container initialization time greater than *t*, in microseconds, as a point of interest.

<a href="" id="-poithreshold-imageload-t-"></a>**-poiThreshold\_ImageLoad**<em>&lt;t&gt;</em>  
Flags any image load time greater than *t*, in microseconds, as a point of interest.

<a href="" id="-poithreshold-serviceinit-t-"></a>**-poiThreshold\_ServiceInit**<em>&lt;t&gt;</em>  
Flags any service initialization time greater than *t*, in microseconds, as a point of interest.

## Remarks


The default is to not flag any services as points of interest. All times are displayed in milliseconds.

## Related topics


[Xperf Actions](xperf-actions.md)

 

 







