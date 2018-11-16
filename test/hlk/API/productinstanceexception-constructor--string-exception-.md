---
title: ProductInstanceException Constructor (String, Exception)
description: ProductInstanceException Constructor (String, Exception)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 73195f8a-bf8a-4bc0-8165-f780adcc089a
author: dawn.wood
ms.author: dawnwood
ms.date: 10/15/2017
ms.topic: article


---

# ProductInstanceException Constructor (String, Exception)


This constructor initializes a new instance of the **ProductInstanceException** class.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>Usage


**Visual Basic**

`Dim message As String`

`Dim except As Exception`

`Dim instance As New ProductInstanceException (message, except)`

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Sub New ( _`

          `message As String _`

          `except As Exception _`

`)`

**C#**

`public ProductInstanceException (`

          `string message`

          `Exception except`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*message*

     A string that represents the message for the exception.

*except*

     An exception object.

 

 






