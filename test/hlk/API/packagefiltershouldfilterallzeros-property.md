---
title: PackageFilter.ShouldFilterAllZeros Property
description: PackageFilter.ShouldFilterAllZeros Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 5e6aa38c-3b64-4bad-beba-cccdc647efe8
author: dawn.wood
ms.author: dawnwood
ms.date: 10/15/2017
ms.topic: article


---

# PackageFilter.ShouldFilterAllZeros Property


This property represents a value indicating whether the filter should be applied if the pass and fail count are both zero.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageFilter`

`Dim value As Boolean`

`value = instance.ShouldFilterAllZeros`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`<DataMemberAttribute> _`

`Public Property ShouldFilterAllZeros As Boolean`

**C#**

`[DataMemberAttribute]`

`public bool ShouldFilterAllZeros { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **Boolean**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






