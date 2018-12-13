---
title: PackageWriter.SavePartialPackage Method (string, List Test )
description: PackageWriter.SavePartialPackage Method (string, List Test )
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 3CC80CA1-FDC1-450E-87FC-E8710D4401CB
author: dawn.wood
ms.author: dawnwood
ms.date: 10/15/2017
ms.topic: article


---

# PackageWriter.SavePartialPackage Method (string, List{Test})


Creates a debug HCK package only containing data in the given test(s).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public void SavePartialPackage (`

          `string packageFile,`

          `List<Test> testList`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*packageFile*

Name of file to where the package will be saved.

*testList*

List of tests to save.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


This function cannot be used for Submission Packages and Update Packages.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






