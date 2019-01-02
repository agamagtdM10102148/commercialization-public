---
title: IMS retry
description: For networks that support it, when an outgoing SMS message fails to send due to a transient error, partners can specify the threshold for the number of attempts to resend the SMS over IMS before switching over to 3GPP or 3GPP2.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1acaf8e5-3db3-46b5-b4c1-b987334aaa3a


ms.date: 05/02/2017
ms.topic: article


---

# IMS retry


For networks that support it, when an outgoing SMS message fails to send due to a transient error, partners can specify the threshold for the number of attempts to resend the SMS over IMS before switching over to 3GPP or 3GPP2. Partners can also specify to retry sending the SMS message once over 3GPP or 3GPP2 without a user prompt if the original message was sent over IMS and failed.

<a href="" id="constraints---none"></a>**Constraints:** None  
This customization supports: **per-IMSI** value, **per-device** value

<a href="" id="instructions-"></a>**Instructions:**  
1.  Create a customization answer file using the contents shown in the following code sample.

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>  
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name="IMSRetry"  
                         Description="Use to specify settings related to SMS messages sent over IMS."  
                         Owner=""  
                         OwnerType="OEM"> 
      
    <!-- Use for the per-IMSI case 
      
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

        <Settings Path="CellCore/PerIMSI/$(__IMSI)/SMS">  
          <!-- Use to specify the threshold for the number of attempts to resend the SMS over IMS -->
          <Setting Name="3GPP/IMS/AttemptThresholdForIMS" Value="" />

          <!-- Use to retry sending the SMS message once wihtout a user prompt -->
          <Setting Name="3GPP/IMS/RetryEnabled" Value="" />
        </Settings>  

      </Variant>

    -->

    <!-- Use for the per-device case

      <Static>  
        <Settings Path="CellCore/PerDevice/SMS">  
          <!-- Use to specify the threshold for the number of attempts to resend the SMS over IMS -->
          <Setting Name="3GPP/IMS/AttemptThresholdForIMS" Value="" />

          <!-- Use to retry sending the SMS message once without a user prompt -->
          <Setting Name="3GPP/IMS/RetryEnabled" Value="" />
        </Settings>  
      </Static>

    -->

    </ImageCustomizations>
    ```

2.  Specify an `Owner`.

3.  Determine if you need to use the **per-IMSI** or **per-device** setting.

    For the **per-IMSI** case:

    1.  Define **Targets** or conditions for when a variant can be applied, such as keying off a SIM's MCC, MNC, and SPN.

    2.  Define settings for a **Variant**, which are applied if the associated target's conditions are met.

4.  Set the `3GPP/IMS/AttemptThresholdForIMS``Value` to specify the threshold for the number of attempts to resend the SMS over IMS. If you need to enable SMS over IMS, then you must set the value to 1 or higher integer.

    For example, if you set this value to 2, this will result in two total attempts. If the value is set to N, it will result in N number of attempts. This value will vary for each mobile operator so work with your mobile operator partner to obtain the correct or required value. If the threshold is exceeded, the SMS will no longer be sent over IMS, but will be sent using the available 3GPP or 3GPP2 channel.

5.  Set the `3GPP/IMS/RetryEnabled``Value` to retry sending the SMS message once without a user prompt if the original message was sent over IMS and failed with RIL\_E\_IMSTEMPFAILURE. The client is not notified of the initial failure. The retry attempt will not be over IMS.

    The default value is 1, which means this behavior is enabled by default. Set to 0 to disable this behavior.

<a href="" id="testing-"></a>**Testing:**  
1.  Flash the build containing this customization to a device with a UICC or CDMA connection.

2.  Successfully testing this customization requires the message to fail so please work with your mobile operator to test this customization on their network.

    During testing, resending the failed SMS message requires the UI. Verification of the tests need to be done using the logs at the network and modem levels.

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
