---
title: IFilterLogNode.ChildNodes Property
description: IFilterLogNode.ChildNodes Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 761dc9f9-2c53-4b3a-a73f-81cccecf8fda
author: dawn.wood
ms.author: dawnwood
ms.date: 10/15/2017
ms.topic: article


---

# IFilterLogNode.ChildNodes Property


This property represents the child nodes for the filter log node.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As IFilterLogNode`

`Dim value As ReadOnlyCollection(Of IFilterLogNode)`

`value = instance.ChildNodes`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`ReadOnly Property ChildNodes As ReadOnlyCollection(Of IFilterLogNode)`

**C#**

`ReadOnlyCollection<IFilterLogNode> ChildNodes { get; }`

## <span id="Property_Value"></span><span id="property_value"></span><span id="PROPERTY_VALUE"></span>Property Value


Returns **ReadOnlyCollection**.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






