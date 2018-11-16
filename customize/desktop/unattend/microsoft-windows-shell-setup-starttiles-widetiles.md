---
title: WideTiles
description: WideTiles
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 10deeec8-f0e0-4298-96c4-5be47a74548c
ms.mktglfcycl: deploy
ms.sitesec: msdn
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---
# WideTiles

`WideTiles` defines the default Microsoft Store apps to appear as wide tiles on the **Start** screen.

To use this setting you must include the `AppId`. The `AppId` is the `AppUserModelID` found in the application's AUMIDs.txt file, which is located in the app package downloaded from the OEM channel partner portal of the Microsoft Store. You can also include the `FirstRunTask` setting to set a background task to run for each app tile on the **Start** screen that you want to be active, or live, by default.

If you skip a setting, Windows will rearrange the flow of your app tiles around the position of that setting on the **Start** screen. The flow rearrangement is based on columns and is designed to eliminate gaps. This position may vary based on the screen size, resolution, and DPI of the PC. For more information about these settings, see the associated [StartTiles](microsoft-windows-shell-setup-starttiles.md) settings topics.

## Child Elements

| Setting                 | Description                                                                           |
|:------------------------|:--------------------------------------------------------------------------------------|
| [WideTile1](microsoft-windows-shell-setup-starttiles-widetiles-widetile1.md) | Specifies the application that appears on the <strong>Start</strong> menu, in position WideTile1. |
| [WideTile2](microsoft-windows-shell-setup-starttiles-widetiles-widetile2.md) | Specifies the application that appears on the <strong>Start</strong> menu, in position WideTile2. |
| [WideTile3](microsoft-windows-shell-setup-starttiles-widetiles-widetile3.md) | Specifies the application that appears on the <strong>Start</strong> menu, in position WideTile3. |
| [WideTile4](microsoft-windows-shell-setup-starttiles-widetiles-widetile4.md) | Specifies the application that appears on the <strong>Start</strong> menu, in position WideTile4. |
| [WideTile5](microsoft-windows-shell-setup-starttiles-widetiles-widetile5.md) | Specifies the application that appears on the <strong>Start</strong> menu, in position WideTile5. |
| [WideTile6](microsoft-windows-shell-setup-starttiles-widetiles-widetile6.md) | Specifies the application that appears on the <strong>Start</strong> menu, in position WideTile6. |

## Valid Configuration Passes

specialize

auditUser

oobeSystem

## Parent Hierarchy

[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md) | [StartTiles](microsoft-windows-shell-setup-starttiles.md) | **WideTiles**

## Applies To

For a list of the Windows editions and architectures that this component supports, see [Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md).

## XML Example

The following XML output shows how to use the `<WideTiles>` component and its settings.

```XML
     <WideTiles>
          <WideTile1>
               <AppId>12345ChannelFabrikam.channel-ABC_defghij6789!App</AppId>
               <FirstRunTask>backgroundtask.js</FirstRunTask>
          </WideTile1>
          <WideTile2>
               <AppId>34567ChannelFabrikam.channel-DEF_012ghijk345!App</AppId>
               <FirstRunTask>Fabrikam.FirstRunTask</FirstRunTask>
          </WideTile2>
          <WideTile3>
               <AppId>56789ChannelFabrikam.channel-GHI_67890jklmno!App</AppId>
          </WideTile3>
     </WideTiles>
```

## Related topics

[StartTiles](microsoft-windows-shell-setup-starttiles.md)

[SquareTiles](microsoft-windows-shell-setup-starttiles-squaretiles.md)
