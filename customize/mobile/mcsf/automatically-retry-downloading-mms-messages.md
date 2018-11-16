---
title: Automatically retry downloading MMS messages
description: Partners can configure the messaging app to automatically retry downloading an MMS message if the initial download attempt fails.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: c76dc5f5-4355-472e-9db2-5f5a9bb02ae4
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# Automatically retry downloading MMS messages


Partners can configure the messaging app to automatically retry downloading an MMS message if the initial download attempt fails.

When this customization is enabled, the download is retried 3 times at 20-, 40-, and 60-second intervals. The following example shows how the retry intervals work using a random download time:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Time</th>
<th>Activity</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>00:00:00</p></td>
<td><p>Initial download starts</p></td>
</tr>
<tr class="even">
<td><p>00:00:11</p></td>
<td><p>Initial download fails due to a transient error. First wait starts and is scheduled for 20 seconds.</p></td>
</tr>
<tr class="odd">
<td><p>00:00:31</p></td>
<td><p>First wait times out, first retry download starts.</p></td>
</tr>
<tr class="even">
<td><p>00:00:49</p></td>
<td><p>First retry download fails due to a transient error. Second wait starts and is scheduled for 40 seconds.</p></td>
</tr>
<tr class="odd">
<td><p>00:01:29</p></td>
<td><p>Second wait times out, second retry download starts.</p></td>
</tr>
<tr class="even">
<td><p>00:01:34</p></td>
<td><p>Second retry download fails due to a transient error. Third wait starts and is scheduled for 60 seconds.</p></td>
</tr>
<tr class="odd">
<td><p>00:02:34</p></td>
<td><p>Third wait times out, third retry download starts.</p></td>
</tr>
</tbody>
</table>

 

If the MMS download fails after the third retry attempt, the message persists in the appropriate thread with a link that the user can tap to retry the download manually. If the user’s manual download attempt fails, the automatic retries are triggered again.

<a href="" id="constraints---none"></a>**Constraints:** None  
This customization supports: **per-SIM** value

<a href="" id="instructions-"></a>**Instructions:**  
1.  Create a customization answer file using the contents shown in the following code sample.

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>  
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name="AutoRetryDownloadForMMS"  
                         Description="Use to configure the messaging app to automatically retry downloading an MMS message if the initial download attempt fails."  
                         Owner=""  
                         OwnerType="OEM"> 
      
      <!-- Define the Targets --> 
      <Targets>
         <Target Id="">
            <TargetState>
               <Condition Name="" Value="" />
               <Condition Name="" Value="" />
            </TargetState>
         </Target>
      </Targets>
      
      <Static>
        <Settings Path="Multivariant">
          <Setting Name="Enable" Value="1" />
        </Settings>
        <Settings Path="AutoDataConfig">
          <Setting Name="Enable" Value="0" />
        </Settings>
      </Static>

      <!-- Define the Variant -->
      <Variant Name=""> 
        <TargetRefs>
          <TargetRef Id="" /> 
        </TargetRefs>

        <Settings Path="Messaging/PerSimSettings/$(__ICCID)">  
          <!-- Set to 1 to enable or 0 to disable -->
          <Setting Name="AutoRetryDownload" Value="" />         
        </Settings>  

      </Variant>

    </ImageCustomizations>
    ```

2.  Specify an `Owner`.

3.  Define **Targets** or conditions for when a variant can be applied, such as keying off a SIM's MCC, MNC, and SPN.

4.  Define settings for a **Variant**, which are applied if the associated target's conditions are met.

5.  Set `AutoRetryDownload` to one of the following values:

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
    <td><p>1 or 0x1</p></td>
    <td><p>Enable automatically retry downloading MMS messages.</p></td>
    </tr>
    <tr class="even">
    <td><p>0 or 0x0</p>
    <p>Or if the <code>AutoRetryDownload</code> setting is missing</p></td>
    <td><p>Disables automatically retry downloading MMS messages.</p></td>
    </tr>
    </tbody>
    </table>

     

<a href="" id="testing-steps-"></a>**Testing steps:**  
1.  Flash the build containing this customization to a device with a UICC or CDMA connection.

2.  Successfully testing this customization requires the MMS message to fail, so work with mobile operator partner to test this customization on their network.

    Be sure to test the scenario where the automatic retry attempt fails for a third time to verify the appearance of the manual download link.

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
