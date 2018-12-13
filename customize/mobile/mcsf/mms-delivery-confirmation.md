---
title: MMS delivery confirmation
description: Partners can specify whether users receive notification that MMS messages could not be delivered, and determine whether users can control this by using the MMS delivery confirmation toggle in the Messaging settings screen.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1752e1b0-cc22-4770-bd1d-d27ed7d195bb
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# MMS delivery confirmation


Partners can specify whether users receive notification that MMS messages could not be delivered, and determine whether users can control this by using the **MMS delivery confirmation** toggle in the **Messaging** settings screen. By default, this user setting is visible but turned off.

<a href="" id="constraints---none"></a>**Constraints:** None  
This customization supports: **per-SIM** value

<a href="" id="instructions-"></a>**Instructions:**  
1.  Create a customization answer file using the contents shown in the following code sample.

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>  
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name="MMSDeliveryConfirmation"  
                         Description="Use to specify whether users receive notification that MMS messages could 
                                      not be delivered, and determine whether users can control this by using the
                                      'MMS delivery confirmation' toggle in the messaging settings screen."  
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

      <!-- Specify the Variant -->
      <Variant Name=""> 
        <TargetRefs>
          <TargetRef Id="" /> 
        </TargetRefs>

        <Settings Path="Messaging/PerSimSettings/$(__ICCID)/RequestDeliveryReport">  
          <Setting Name="RequestDeliveryReportIsSupported" Value="" />      
          <Setting Name="RequestDeliveryReport" Value="" />  
        </Settings>  

      </Variant>

    </ImageCustomizations>
    ```

2.  Specify an `Owner`.

3.  Define **Targets** or conditions for when a variant can be applied, such as keying off a SIM's MCC, MNC, and SPN.

4.  Define settings for a **Variant**, which are applied if the associated target's conditions are met.

5.  To hide or show the toggle for MMS delivery confirmation, set the value of `RequestDeliveryReportIsSupported` to one of the following:

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
    <td><p>0 or 'False'</p></td>
    <td><p>Hides the toggle.</p></td>
    </tr>
    <tr class="even">
    <td><p>1 or 'True'</p></td>
    <td><p>Shows the toggle.</p></td>
    </tr>
    </tbody>
    </table>

     

6.  To set the default value for the MMS delivery confirmation toggle, set the value of `RequestDeliveryReport` to one of the following:

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
    <td><p>0 or 'False'</p></td>
    <td><p>Sets the default value to off.</p></td>
    </tr>
    <tr class="even">
    <td><p>1 or 'True'</p></td>
    <td><p>Sets the default value to on.</p></td>
    </tr>
    </tbody>
    </table>

     

<a href="" id="testing-"></a>**Testing:**  
1.  Flash the build containing this customization to a device.

2.  Go to the settings screen in the **Messaging** app.

3.  Verify the **MMS delivery confirmation** toggle default value or check that it is no longer visible depending on the settings and values that you used.

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
