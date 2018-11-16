---
title: IFilterTargetData.AllInboxDrivers Property
description: IFilterTargetData.AllInboxDrivers Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 82ba5716-0cfc-4566-9fc0-168f09f02a99
author: dawn.wood
ms.author: dawnwood
ms.date: 10/15/2017
ms.topic: article


---

# IFilterTargetData.AllInboxDrivers Property


This property indicates whether all of the drivers associated with this device are signed.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As IFilterTargetData`

`Dim value As TargetDriversType`

`value = instance.AllInboxDrivers`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`ReadOnly Property AllInboxDrivers As TargetDriversType`

**C#**

`TargetDriversType AllInboxDrivers { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **TargetDriversType**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


If all drivers associated with the target are signed, the result is InboxDrivers.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






