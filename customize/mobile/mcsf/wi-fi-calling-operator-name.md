---
title: Wi-Fi calling operator name
description: OEMs can customize the display name for the mobile operator when the device is using Wi-Fi calling.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 01CC71CE-5C1F-4278-8066-A08A64808788
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# Wi-Fi calling operator name


OEMs can customize the display name for the mobile operator when the device is using Wi-Fi calling.

<a href="" id="constraints---none"></a>**Constraints:** None  
This customization supports: **per-IMSI** value

<a href="" id="instructions-"></a>**Instructions:**  
1. Create a customization answer file using the contents shown in the following code sample.

   ```XML
   <?xml version="1.0" encoding="utf-8" ?>  
   <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                        Name="WiFiCallingOperatorName"  
                        Description="Use to customize the mobile operator name that's visible when the phone 
                                     is using Wi-Fi calling."  
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

       <!-- Add the resource-only dll file and language MUI packages -->
       <Settings Path="Localization/MUI">  
         <!-- Use to add your base MUI DLL file -->
         <Asset Name="BaseDll" Source="" />

         <!-- Use to specify the language MUI packages (*.dll.mui) for the languages you are supporting and have 
              localized strings for -->
         <Asset Name="LanguageDll/$(langid)" Source="" />
         <Asset Name="LanguageDll/$(langid)" Source="" />
         <Asset Name="LanguageDll/$(langid)" Source="" />
         <!-- Add as many as you need -->         
       </Settings>
     </Static>

     <!-- Specify the Variant -->
     <Variant Name=""> 
       <TargetRefs>
         <TargetRef Id="" /> 
       </TargetRefs>

       <Settings Path="Phone/PerSimSettings/$(__IMSI)">  
         <Setting Name="WiFiCallingOperatorName" Value="" />      
       </Settings>  

     </Variant>

   </ImageCustomizations>
   ```

2. Specify an `Owner`.

3. Add the resource-only .dll file and the language MUI packages (\*.dll.mui) for the languages you are supporting. To do this, follow these steps:

   1.  Add the resource-only .dll that contains the custom display string by setting the `BaseDll` asset to point to the location of your base MUI DLL file. For example: *C:\\Path\\DisplayStrings.dll*.

   2.  Add the language MUI packages (\*.dll.mui) for all the languages you are supporting and have localized strings for. To do this:

       -   Set the asset's `Name` to `LanguageDll/`*$(langid)* where *$(langid)* corresponds to the language. For example: *LanguageDll/en-US*.

       -   Set the asset's `Source` to the location of the .dll.mui file for that language. For example: *C:\\Path\\en-us\\DisplayStrings.dll.mui*.

       -   Repeat the previous steps for the other languages.

           The following example shows the customization answer file entries for en-US, fr-CA, and es-MX languages:

           ```
           <Asset Name="LanguageDll/en-US" Source="C:\Path\en-us\DisplayStrings.dll.mui" />
           <Asset Name="LanguageDll/fr-CA" Source="C:\Path\fr-CA\DisplayStrings.dll.mui" />
           <Asset Name="LanguageDll/es-MX" Source="C:\Path\es-MX\DisplayStrings.dll.mui" />
           ```

       For more information, see [Create a resource-only .dll for localized strings](create-a-resource-only-dll-for-localized-strings.md).

4. For the **per-IMSI** case:

   1.  Define **Targets** or conditions for when a variant can be applied, such as keying off a SIM's MCC, MNC, and SPN.

   2.  Define settings for a **Variant**, which are applied if the associated target's conditions are met.

5. To customize the name of the mobile operator when the phone is using Wi-Fi calling, you can set the value for `WiFiCallingOperatorName` to:

   - Use a localized MUI string – To do this, set value to the name of the resource-only .dll file and specify the string offset that corresponds to the mobile operator name. For example: <em>@DisplayStrings.dll,-Offset</em>.

   - Use a non-localized string – To do this, set value to the string that corresponds to the mobile operator name. For example: *Contoso*.

   If you don't set the value for `WiFiCallingOperatorName`, the device will always display "*SIMServiceProviderName* Wi-Fi", where *SIMServiceProviderName* is a string that corresponds to the SPN for the SIM on the device. If the service provider name in the SIM is not set, only "Wi-Fi" will be displayed.

<a href="" id="testing-steps-"></a>**Testing steps:**  
1.  Flash a build containing this customization to a device that has Wi-Fi calling enabled.

2.  If you used a localized MUI string, verify that the localized string for the Wi-Fi calling mobile operator name is displayed on the dialer.

    If you used a non-localized string, verify that this string is displayed on the dialer.

    If you did not set the value, verify that "*SIMServiceProviderName* Wi-Fi" is displayed on the dialer.

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
