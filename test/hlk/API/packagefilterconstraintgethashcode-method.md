---
title: PackageFilterConstraint.GetHashCode Method
description: PackageFilterConstraint.GetHashCode Method
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d154f1b3-f0f2-4c23-88dc-68e3a86ee930
author: dawn.wood
ms.author: dawnwood
ms.date: 10/15/2017
ms.topic: article


---

# PackageFilterConstraint.GetHashCode Method


This method serves as a hash function for a particular package filter type.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel.Submission (in Microsoft.Windows.Kits.Hardware.ObjectModel.Submission)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As PackageFilterConstraint`

`Dim returnValue As Integer`

`returnValue = instance.GetHashCode`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Overrides Function GetHashCode As Integer`

**C#**

`public override int GetHashCode ()`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **Int32**, which is a unique number which is the **PackageFilterConstraint** hash code.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






