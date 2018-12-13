---
title: IFilterResult.Filter Property
description: IFilterResult.Filter Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c8b95ca1-ddbb-44ac-9def-10f5c85390e1
author: dawn.wood
ms.author: dawnwood
ms.date: 10/15/2017
ms.topic: article


---

# IFilterResult.Filter Property


This property represents the filter ID number for the applied filter. The Filter ID number uniquely identifies a filter.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As IFilterResult`

`Dim value As IFilter`

`value = instance.Filter`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`ReadOnly Property Filter As IFilter`

**C#**

`IFilter Filter { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns [IFilter Interface](ifilter-interface.md).

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






