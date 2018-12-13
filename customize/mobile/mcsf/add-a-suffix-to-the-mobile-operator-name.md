---
title: Add a suffix to the mobile operator name
description: To meet branding requirements for some mobile operators, OEMs can add a suffix to the network name that is displayed on the phone.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: ddf2ee03-455e-4678-9c38-ee91510ae4d4
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# Add a suffix to the mobile operator name


To meet branding requirements for some mobile operators, OEMs can add a suffix to the network name that is displayed on the phone. For example, from **ABC** to **ABC 3G** when under 3G coverage. This feature can be applied for any radio access technology (RAT).

For TD-SCDMA RAT, a 3G suffix is always appended by default, but partners can also customize this the same way as with any other RAT.

<a href="" id="constraints---none"></a>**Constraints:** None  
This customization supports: **per-IMSI** value, **per-device** value

<a href="" id="instructions-"></a>**Instructions:**  
1.  Create a customization answer file using the contents shown in the following code sample.

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>  
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name="NetworkSuffix"  
                         Description="Use to add a suffix to the network name that is displayed on the device."  
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

        <Settings Path="CellCore/PerIMSI/$(__IMSI)/General">  
          <Setting Name="NetworkSuffix/$(SYSTEMTYPE)" Value="" />      
        </Settings>  

      </Variant>

    -->

    <!-- Use for the per-device case

      <Static>  
        <Settings Path="CellCore/PerDevice/General">  
          <Setting Name="NetworkSuffix/$(SYSTEMTYPE)" Value="" />   
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

4.  In the setting name, set *$(SYSTEMTYPE)* to the network type that you want to append the network name to, and set the value for that network type as shown in the following table:

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>$(SYSTEMTYPE)</th>
    <th>Value</th>
    <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>4</p></td>
    <td><p>2G</p></td>
    <td><p>Represents RIL_SYSTEMTYPE_GSM (GSM connection).</p></td>
    </tr>
    <tr class="even">
    <td><p>8</p></td>
    <td><p>3G</p></td>
    <td><p>Represents RIL_SYSTEMTYPE_UMTS (UMTS connection).</p></td>
    </tr>
    <tr class="odd">
    <td><p>16</p></td>
    <td><p>LTE</p></td>
    <td><p>Represents RIL_SYSTEMTYPE_LTE (LTE connection).</p></td>
    </tr>
    <tr class="even">
    <td><p>32</p></td>
    <td><p>3G</p></td>
    <td><p>Represents RIL_SYSTEMTYPE_TDSCDMA (TD-SCDMA connection).</p>
    <p>Partners do not need to set this registry value.</p>
    <p>By default, this registry setting is set to “ 3G”.</p></td>
    </tr>
    </tbody>
    </table>



~~~
For example, if you would like the mobile operator name (ABC) and the suffix (3G) to appear as **ABC 3G** (there is a space between the network name and the connection type) rather than **ABC3G** (no space between the network name and connection type), you need to include a space when setting the values.
~~~

<a href="" id="testing-steps-"></a>**Testing steps:**  
1.  Flash a build containing this customization to a device with a SIM.

2.  In the Start screen, verify that the phone tile shows the mobile operator name followed one of the suffixes that you set.

    The suffix will depend on the network.

3.  Go to the **Settings** screen and scroll down until you see **Cellular & SIM**. Verify that the mobile operator name is followed by the correct suffix. This should match what you see in the phone tile in the Start screen.

4.  Tap **Cellular & SIM** and verify that the **Active network** shows the mobile operator name and correct suffix.

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
