---
title: WideTile6
description: WideTile6
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 633fd59c-18ed-495b-b82b-7dced237d0cb
ms.mktglfcycl: deploy
ms.sitesec: msdn
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---
# WideTile6

`WideTile6` specifies which application appears as a wide tile on the **Start** menu, in position WideTile6. This position may vary based on the screen size, resolution, and DPI of the target Windows 8 PC.

## Child Elements

| Setting                 | Description                                                                           |
|:------------------------|:--------------------------------------------------------------------------------------|
| [AppId](microsoft-windows-shell-setup-starttiles-widetiles-widetile6-appid.md) | Specifies the Microsoft Store apps appearing on wide tiles on the <strong>Start</strong> screen. |
| [FirstRunTask](microsoft-windows-shell-setup-starttiles-widetiles-widetile6-firstruntask.md) | Specifies the background task that is active, or live, by default for the tile. |

## Valid Configuration Passes

specialize

auditUser

oobeSystem

## Parent Hierarchy

[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md)| [StartTiles](microsoft-windows-shell-setup-starttiles.md) | [WideTiles](microsoft-windows-shell-setup-starttiles-widetiles.md) | **WideTile6**

## Applies To

For a list of the Windows editions and architectures that this component supports, see [Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md).

## XML Example

The following XML output shows how to use the `<WideTile6>` component.

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

[RegionalOverrides](microsoft-windows-shell-setup-starttiles-regionaloverrides.md)

[WideTiles](microsoft-windows-shell-setup-starttiles-regionaloverrides-regionaloverride-widetiles.md)

[WideTiles](microsoft-windows-shell-setup-starttiles-widetiles.md)
