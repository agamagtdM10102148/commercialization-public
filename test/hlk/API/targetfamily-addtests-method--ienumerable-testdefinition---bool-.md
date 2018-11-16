---
title: TargetFamily.AddTests Method (IEnumerable TestDefinition , bool)
description: TargetFamily.AddTests Method (IEnumerable TestDefinition , bool)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 5D74F3C2-BC30-4466-97B3-BAED93602C69
author: dawn.wood
ms.author: dawnwood
ms.date: 10/15/2017
ms.topic: article


---

# TargetFamily.AddTests Method (IEnumerable{TestDefinition}, bool)

>[!WARNING]
>  This functionality is being deprecated. Please use playlists to create custom test pass lists.

 

Adds the given Tests to this [TargetFamily](targetfamily-class.md).

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**C#**

`public virtual void AddTests (`

          `IEnumerable<TestDefinition> tests,`

          `bool disableFeatureDetection`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*tests*

 The tests to be added.

*disableFeatureDetection*

Flag that causes all the tests to be added to Targets regardless of feature detection.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






