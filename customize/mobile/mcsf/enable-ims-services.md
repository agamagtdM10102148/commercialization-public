---
title: Enable IMS services
description: Partners can identify which IP Multimedia Subsystem (IMS) services, if any, are enabled on the device by default. The IMS services that can be identified are IMS, SMs over IMS, Voice over IMS, and Video over IMS.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 83232fe7-7922-42e8-a26b-55b32d84dfe3
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# Enable IMS services


Partners can identify which IP Multimedia Subsystem (IMS) services, if any, are enabled on the device by default. The IMS services that can be identified are: IMS, SMs over IMS, Voice over IMS, and Video over IMS.

To allow configuration of the default values of IMS services out of the box using multivariant, the `IMSServices` setting is mapped as follows:

```
IMSServices 
{
     IMS  ----------------> RILDMCONFIG_IMS_TEST_NODE_STATUS -> NV 67264 subitem ‘RegConfigTestMode’ (// 1 means disabling IMS and 0 means enabling it) 
     SMS_OverIMS --------->  RILDMCONFIG_SMSOVER_IP_NW_INDICATION -> NV 67259 subitem ‘iSMSOverIPNetworkIndication’
     Voice_Over_IMS ------> [RILDMCONFIG_IMS_VOICE_ENABLED -> NV 67348 subitem ‘volte_disabled’] 
     Video_Over_IMS ------> [RILDMCONFIG_IMS_VIDEO_ENABLED -> NV 67348 subitem ‘VT calling enabled’] 
}; 
```

**Note**  
All values need to be set at once. For example, you cannot just set the value for Voice\_Over\_IMS. You must send a value for all. The OS applies the value to the corresponding NV item only if the value is changing.



wpblue\_gdr2 allows configuration of the OMA DM services mask (sub-item of NV 69750) separately. You can use a new setting similar to `IMSServices` called `IMSOMADMServices` which will be directly mapped to RIL\_IMS\_NW\_ENABLED\_FLAGS on the modem side. See the SoC modem documentation for more details about the flags.

```
IMSOMADMServices
{
     0 = NONE
     1 = OMA_DM  -----------> RIL_IMS_NW_ENABLED_FLAG_PROVISION (Bit 0 - Enable(1)/Disable(0) OMA DM services)
     2 = VOICE  ------------> RIL_IMS_NW_ENABLED_FLAG_VOICE (Bit 1-  VoLTE enable(1)/disable(0) by OMA-DM)
     4 = VIDEO -------------> RIL_IMS_NW_ENABLED_FLAG_VIDEO (Bit 2 - VT enable(1)/disable(0) by OMA-DM)
     8 = EAB_PRESENCE ------> RIL_IMS_NW_ENABLED_FLAG_EAB (Bit 3 - Presence enable(1)/disable(0) by OMA-DM)
     15 = Enable all above services
}
```

All the other settings for VoLTE and VT, such as `ShowVoLTEToggle`, `SwitchIMS`, and so on remain unchanged. For more information about these settings, see [Settings for IMS services](settings-for-ims-services.md).

<a href="" id="constraints---none"></a>**Constraints:** None  
This customization supports: **per-IMSI** value

<a href="" id="instructions-"></a>**Instructions:**  
1.  Create a customization answer file using the contents shown in the following code sample.

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>  
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name="EnableIMSServices"  
                         Description="Use to configure which IMS services are enabled."  
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

        <Settings Path="CellCore/PerIMSI/$(__IMSI)/VoLTE">  
          <Setting Name="IMSServices" Value="" />

          <-- To configure the OMA DM services mask. -->
          <Setting Name="IMSOMADMServices" Value="" />
        </Settings>  

      </Variant>

    </ImageCustomizations>
    ```

2.  Specify an `Owner`.

3.  For the **per-IMSI** case:

    1.  Define **Targets** or conditions for when a variant can be applied, such as keying off a SIM's Mobile Country Code (MCC), Mobile Network Code (MNC), and Service Provider Name (SPN).

    2.  Define the settings for a **Variant**, which are applied if the associated target's conditions are met.

4.  Set the value for the `IMSServices` setting to any combination of the following flags or bitmasks:

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Service</th>
    <th>Flag (decimal)</th>
    <th>Bitmask (binary)</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>IMS</p></td>
    <td><p>1</p></td>
    <td><p>0001</p></td>
    </tr>
    <tr class="even">
    <td><p>SMS over IMS</p></td>
    <td><p>2</p></td>
    <td><p>0010</p></td>
    </tr>
    <tr class="odd">
    <td><p>Voice over IMS</p></td>
    <td><p>4</p></td>
    <td><p>0100</p></td>
    </tr>
    <tr class="even">
    <td><p>Video over IMS</p></td>
    <td><p>8</p></td>
    <td><p>1000</p></td>
    </tr>
    </tbody>
    </table>



~~~
You can set `IMSServices` to any decimal value formed by a combination of the bitmasks. For example, a bitmask of 1111 (or a decimal value of 15) means that all services are enabled. A bitmask of 0101 (or a decimal value of 5) means that IMS and Voice over IMS are enabled by default and SMS over IMS and Video over IMS are disabled, and so on.
~~~

5.  To configure the OMA DM services mask, set the `IMSOMADMServices` setting to one of the following values:

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Service</th>
    <th>Flag (decimal)</th>
    <th>Bitmask (binary)</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>None</p></td>
    <td><p>0</p></td>
    <td><p>00000</p></td>
    </tr>
    <tr class="even">
    <td><p>OMA DM</p></td>
    <td><p>1</p></td>
    <td><p>00001</p></td>
    </tr>
    <tr class="odd">
    <td><p>Voice</p></td>
    <td><p>2</p></td>
    <td><p>00010</p></td>
    </tr>
    <tr class="even">
    <td><p>Video</p></td>
    <td><p>4</p></td>
    <td><p>00100</p></td>
    </tr>
    <tr class="odd">
    <td><p>EAB presence</p></td>
    <td><p>8</p></td>
    <td><p>01000</p></td>
    </tr>
    <tr class="even">
    <td><p>Enable all services</p></td>
    <td><p>15</p></td>
    <td><p>10000</p></td>
    </tr>
    </tbody>
    </table>



<a href="" id="testing-"></a>**Testing:**  
Work with your mobile operator partner to test this customization on the operator's network.


## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
