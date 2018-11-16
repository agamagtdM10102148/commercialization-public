---
title: ITargetInformation.XmlData Property
description: ITargetInformation.XmlData Property
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: fd5e95ab-bfc7-4d65-a59e-12a5e0a0b1f8
author: dawn.wood
ms.author: dawnwood
ms.date: 10/15/2017
ms.topic: article


---

# ITargetInformation.XmlData Property


This property gets the target information in the raw XML format.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim instance As ITargetInformation`

`Dim value As String`

`value = instance.XmlData`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`ReadOnly Property XmlData As String`

          

**C#**

`string XmlData { get; }`

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **String**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


The XML data is collected using sysparse and is collected on the client machine. The data is gathered from many sources by the Client software and returned to the controller (stored in XML format).

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






