---
title: CProfileCollection
description: CProfileCollection
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 4c7bae41-afe1-4e8c-bce6-41c37991261b
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.author: eliotgra
ms.date: 05/05/2017
ms.topic: article


---

# CProfileCollection


Represents a collection of [CProfile](cprofile.md) objects. This class implements the [IProfileCollection](iprofilecollection.md) and [IErrorInfo](http://go.microsoft.com/fwlink/p/?linkid=217161) interfaces. The client instantiates a new instance for every collection of profiles that it wants the control manager to run.

## Syntax


```
{
  [default] interface IProfileCollection;
  interface IEnumProfile;
  interface IErrorInfo;
};
```

## Related topics


[Classes](classes.md)

 

 







