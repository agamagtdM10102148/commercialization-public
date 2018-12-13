---
title: Network Time Protocol support
description: Use to automatically set the time using an NTP client in a mobile device that doesn't support NITZ, or when cellular data is not available.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d044ca8c-91af-4767-b7c3-4a281161d465
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# Network Time Protocol support


Use to automatically set the time using an NTP client in a mobile device that doesn't support NITZ, or when cellular data is not available.

Mobile devices primarily rely on Network Identify and Time zone (NITZ), which is provided by the mobile operator, to automatically update the time on the device. When NITZ is available from the cellular network, there are no issues maintaining accurate time in devices. However, for devices that do not have a SIM or have had the SIM removed for some time, or for devices that have a SIM but NITZ is not supported, the device may run into issues maintaining accurate time on the device.

The OS includes support for Network Time Protocol (NTP), which enables devices to receive time when NITZ is not supported or when cellular data is not available. NTP gets the time by querying a server at a specified time interval. NTP is based on Coordinated Universal Time (UTC) and doesn't support time zone or daylight saving time so users will need to manually update the time zone after an update from NTP if users move between time zones.

For mobile devices that do not support NITZ and have NTP enabled, the user is required to select the time zone, date, and time during initial device setup before the Wi-Fi connections page. The Wi-Fi connection requires certificate validation, which needs accurate time.

If NTP is enabled, the first NTP query happens post-shell ready. After that, the default regular sync interval then applies.

<a href="" id="constraints---none"></a>**Constraints:** None  

<a href="" id="instructions-"></a>**Instructions:**  
1.  Create a customization answer file using the contents shown in the following code sample.

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>  
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name="NTPSettings"  
                         Description="Use to automatically set the time, using an NTP client, in a Windows Phone device that 
                                      doesn't support NITZ or when cellular data is not available."  
                         Owner=""  
                         OwnerType="OEM"> 

      <Static>  
        <Settings Path="AutomaticTime"> 
          <Setting Name="NTPEnabled" Value="" /> 
          <Setting Name="NTPRegularSyncInterval" Value="" />   
          <Setting Name="NTPRetryInterval" Value="" />   
          <Setting Name="NTPServers" Value="" />     

        </Settings>  
      </Static>

    </ImageCustomizations>
    ```

2.  Specify an `Owner`.

3.  To enable or disable the NTP client, set `NTPEnabled` to one of the following values:

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Value</th>
    <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>0 or 'Disabled'</p></td>
    <td><p>Disables the NTP client.</p></td>
    </tr>
    <tr class="even">
    <td><p>1 or 'Enabled'</p></td>
    <td><p>Enables the NTP client.</p></td>
    </tr>
    </tbody>
    </table>



~~~
**Note**  
Microsoft recommends explicitly setting a value for `NTPEnabled` depending on the user experience you want to enable or requirements you need to meet.
~~~



4.  To set the regular sync interval, in hours, set `NTPRegularSyncInterval` to a value between 1 and 168 hours (inclusive). The default sync interval value is 12 hours.

5.  To set the retry interval, in hours, if the regular sync fails, set `NTPRetryInterval` to a value between 1 and 24 hours (inclusive).

6.  To enumerate the NTP source server(s) used by the NTP client, set the value for `NTPServer`. For example, the value can be *ntpserver1.contoso.com;ntpserver2.fabrikam.com;ntpserver3.contoso.com* and so on. The default NTP source server value time.windows.com.

<a href="" id="testing-"></a>**Testing:**  
1.  Flash the build containing this customization to a device that does not support NITZ nor has a cellular data connection.

2.  During initial device setup, verify that you see the **Time and region** screen. Set the correct time zone, date, and time for the device.

3.  Verify that the Wi-Fi connection screen shows up after the **Time and region** screen. Connect to a Wi-Fi network so that the NTP client can connect to the NTP source server.

4.  If you enabled NTP support, and depending on the values that you set for the regular sync interval, verify that the time on the device remains accurate after the sync interval has been reached. If the sync fails, verify if the correct time is set after the retry interval has passed.

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
