---
title: Full error messages for SMS and MMS
description: Partners can choose to display additional content in the conversation view when an SMS or MMS message fails to send.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2baeb22a-85d5-470e-a6d9-531a380065ed
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# Full error messages for SMS and MMS


Partners can choose to display additional content in the conversation view when an SMS or MMS message fails to send. This content includes a specific error code in decimal format that the user can report to technical support. Common errors also include a friendly string to help the user self-diagnose and fix the problem.

<a href="" id="constraints---none"></a>**Constraints:** None  
This customization supports: **per-SIM** value

<a href="" id="instructions-"></a>**Instructions:**  
1.  Create a customization answer file using the contents shown in the following code sample.

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>  
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name="SMSErrorMessages"  
                         Description="Use to display additional content in the conversation view when an SMS or MMS message fails to send."  
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

        <Settings Path="Messaging/PerSimSettings/$(__ICCID)">  
          <Setting Name="ErrorCodeEnabled" Value="" />    
        </Settings>  

      </Variant>

    </ImageCustomizations>
    ```

2.  Specify an `Owner`.

3.  Define **Targets** or conditions for when a variant can be applied, such as keying off a SIM's MCC, MNC, and SPN.

4.  Define settings for a **Variant**, which are applied if the associated target's conditions are met.

5.  The `LimitRecipients` setting limits the maximum number of recipients that a user can send messages to, and this value is in the range 0 &lt; `LimitRecipients` &lt;= 500 (decimal). When setting the value for `LimitRecipients`, you can use either decimal or the equivalent hexadecimal value (with a 0x prefix).

    Set `ErrorCodeEnabled` to one of the following values:

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
    <td><p>1 or 'True'</p></td>
    <td><p>Displays the error messages with an explanation of the problem and the decimal-format error codes.</p></td>
    </tr>
    <tr class="even">
    <td><p>0 or 'False'</p></td>
    <td><p>Does not display the full error message.</p></td>
    </tr>
    </tbody>
    </table>

     

<a href="" id="testing-steps-"></a>**Testing steps:**  
1.  Flash the build containing this customization to a device.

2.  Ensure that the device is able to send SMS or MMS messages.

3.  Open the messaging application to send SMS or MMS messages.

4.  Work with your mobile operator to create error scenarios for messaging.

5.  The error message displayed on the messaging screen should start with an explanation in words of the problem, and end in either "MMS error: \#\#\#\#" or "SMS error: \#\#\#\#".

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
