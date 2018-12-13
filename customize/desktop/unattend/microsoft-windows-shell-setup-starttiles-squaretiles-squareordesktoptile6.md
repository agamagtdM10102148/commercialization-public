---
title: SquareOrDesktopTile6
description: SquareOrDesktopTile6
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: eaba1fd7-a7ad-4350-971e-26949ec402a4
ms.mktglfcycl: deploy
ms.sitesec: msdn
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---
# SquareOrDesktopTile6

`SquareOrDesktopTile6` specifies which application appears as a square tile on the **Start** menu, in position SquareOrDesktopTile6. This position may vary based on the screen size, resolution, and DPI of the target device.

## Child Elements

| Setting                 | Description                                                                           |
|:------------------------|:--------------------------------------------------------------------------------------|
| [AppIdOrPath](microsoft-windows-shell-setup-starttiles-squaretiles-squareordesktoptile6-appidorpath.md) | Specifies the <code>AppID</code> of the Microsoft Store apps, or the path to the desktop apps, which appear as square tiles on the <strong>Start</strong> screen. |
| [FirstRunTask](microsoft-windows-shell-setup-starttiles-squaretiles-squareordesktoptile6-firstruntask.md) | Specifies the background task that is active, or live, by default for a tile when a user signs in to Windows for the first time. |

## Valid Configuration Passes

specialize

auditUser

oobeSystem

## Parent Hierarchy

[Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md)| [StartTiles](microsoft-windows-shell-setup-starttiles.md) | [SquareTiles](microsoft-windows-shell-setup-starttiles-squaretiles.md) | **SquareOrDesktopTile6**

## Applies To

For a list of the Windows editions and architectures that this component supports, see [Microsoft-Windows-Shell-Setup](microsoft-windows-shell-setup.md).

## XML Example

The following XML output shows how to use the `<SquareOrDesktopTile6>` component.

```XML
<SquareTiles>
          <SquareOrDesktopTile1>
               <AppIdOrPath>C:\programdata\microsoft\windows\start menu\programs\desktoptile1.lnk</AppIdOrPath>
               <FirstRunTask>backgroundtask.js</FirstRunTask>
          </SquareOrDesktopTile1>
          <SquareOrDesktopTile2>
               <AppIdOrPath>67890ChannelFabrikam.channel-JKL_mnop1234789!App</AppIdOrPath>
               <FirstRunTask>Fabrikam.FirstRunTask</FirstRunTask>
          </SquareOrDesktopTile2>
          <SquareOrDesktopTile3>
               <AppIdOrPath>C:\programdata\microsoft\windows\start menu\programs\desktoptile3.lnk</AppIdOrPath>
          </SquareOrDesktopTile3>
          <SquareTile1>
               <AppId>12345ChannelFabrikam.channel-ABC_defghij6789!App</AppId>
               <FirstRunTask>backgroundtask.js</FirstRunTask>
          </SquareTile1>
          <SquareTile2>
               <AppId>34567ChannelFabrikam.channel-DEF_012ghijk345!App</AppId>
               <FirstRunTask>Fabrikam.FirstRunTask</FirstRunTask>
          </SquareTile2>
          <SquareTile3>
               <AppId>56789ChannelFabrikam.channel-GHI_67890jklmno!App</AppId>
          </SquareTile3>
     </SquareTiles>
```

## Related topics

[StartTiles](microsoft-windows-shell-setup-starttiles.md)

[RegionalOverrides](microsoft-windows-shell-setup-starttiles-regionaloverrides.md)

[SquareTiles](microsoft-windows-shell-setup-starttiles-squaretiles.md)
