---
title: Test.AddTests Method (IEnumerable TestDefinition , bool)
description: Test.AddTests Method (IEnumerable TestDefinition , bool)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: DB74BFFF-CCFA-4665-A82E-FBBF357C5868
author: dawn.wood
ms.author: dawnwood
ms.date: 10/15/2017
ms.topic: article


---

# Test.AddTests Method (IEnumerable{TestDefinition}, bool)

>[!WARNING]
>  This functionality is being deprecated. Please use playlists to create custom test pass lists.

 

This method should not be called.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`  public virtual void AddTests (`

          `IEnumerable<TestDefinition> tests`

          `bool featureDetectionEnabled`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*tests*

The tests to be added.

*featureDetectionEnabled*

Whether the tests should be added with feature detection or not.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






