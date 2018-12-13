---
title: Default highest connection speed
description: Partners can set the default value for the Highest connection speed option in the Settings Cellular SIM SIM screen by specifying the bitmask for any combination of radio technology to be excluded from the default value.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 697d235e-b498-4c2a-b4b0-4e0677391f40
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# Default highest connection speed


Partners can set the default value for the **Highest connection speed** option in the **Settings** &gt; **Cellular & SIM** &gt; **SIM** screen by specifying the bitmask for any combination of radio technology to be excluded from the default value. The connection speed that has not been excluded will show up as the highest connection speed.

Users can later change the highest connection speed setting on the device.

**Note**  
On dual SIM devices that only support up to 3G connection speeds, the **Highest connection speed** option is replaced by a 3G on/off toggle based on the per-device setting. **On** means that 3G is preferred and **Off** means 2G only.

 

<a href="" id="constraints---none"></a>**Constraints:** None  
This customization supports: **per-IMSI** value, **per-device** value

<a href="" id="instructions-"></a>**Instructions:**  
1.  Create a customization answer file using the contents shown in the following code sample.

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>  
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name="DefaultHighestConnectionSpeed"  
                         Description="Use to set the default value for the highest connection speed in the cellular Settings CPL."  
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
          <Setting Name="ExcludedSystemTypesByDefault" Value="" />
        </Settings>  
      </Variant>

    -->

    <!-- Use for the per-device case

      <Static>  
        <Settings Path="CellCore/PerDevice/General">  
          <Setting Name="ExcludedSystemTypesByDefault" Value="" />
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

4.  Specify the `ExcludedSystemTypesByDefault``Value` to set a default value for the **Highest connection speed** option in the **Settings** &gt; **Cellular** screen.

    1.  Refer to [RILSYSTEMTYPE] and note the values for the corresponding radio technology that you want to exclude.

        For example, on an LTE network the default setting for the highest connection speed is 4G. The other available options that show up also include 3G and 2G. However, if you want to change the default to 2G, you will need to exclude RIL\_SYSTEMTYPE\_LTE (4G) and RIL\_SYSTEMTYPE\_UMTS (3G) to set the default to 2G. To do this, note the values for RIL\_SYSTEMTYPE\_LTE (4G) and RIL\_SYSTEMTYPE\_UMTS (3G) in hexadecimal and convert these to binary.

        <table>
        <colgroup>
        <col width="33%" />
        <col width="33%" />
        <col width="33%" />
        </colgroup>
        <thead>
        <tr class="header">
        <th></th>
        <th>Hexadecimal</th>
        <th>Binary</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td><p>RIL_SYSTEMTYPE_LTE (4G)</p></td>
        <td><p>0x10</p></td>
        <td><p>10000</p></td>
        </tr>
        <tr class="even">
        <td><p>RIL_SYSTEMTYPE_UMTS (3G)</p></td>
        <td><p>0x8</p></td>
        <td><p>01000</p></td>
        </tr>
        </tbody>
        </table>

         

    2.  Perform a bitwise **OR** operation on the radio technologies you want to exclude.

        For example, a bitwise **OR** operation on RIL\_SYSTEMTYPE\_LTE (4G) and RIL\_SYSTEMTYPE\_UMTS (3G) results in the value 11000 (binary) or 0x18 (hexadecimal). This means that for this example, `ExcludedSystemTypesByDefault``Value` must be set to 0x18 to change the default highest connection speed to 2G.

        Partners should note that there is no 3G only option for the highest connection speed. The architecture is designed such that 3G means 3G is preferred and 2G is allowed.

<a href="" id="testing-"></a>**Testing:**  
1.  Flash the build containing this customization to a device.

2.  Go to the **Settings** &gt; **Celluar & SIM** &gt; **SIM** screen.

3.  Verify that the **Highest connection speed** shows the correct default value that you set.

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
