---
title: Additional alarms
description: Partners can add one additional alarm sound to the phone for use in the Alarm Clocks app. Partners can also set a new default alarm.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1141bd50-7a2b-4095-b708-4bed7151f083
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# Additional alarms


Partners can add one additional alarm sound to the phone for use in the **Alarm & Clocks** app. Partners can also set a new default alarm.

Alarms should be a maximum of 100 KB and have a length of 5 to 15 seconds. They must be in .wma format, with a compression of 128 kbit/s for stereo or 64 kbit/s mono. Partner sounds should play at an appropriate volume relative to other sounds and ringtones, and there should be minimal distortion from the device speaker, at full volume.

**Limitations and restrictions:**

-   The names of the sounds must be localized for all display languages that ship on the device.

-   Sound files must be approved by Microsoft.

-   Partners must not move, delete, or modify the alarms provided by Microsoft.

Partners must keep the following design considerations in mind when implementing additional alarms:

**File size:** Ringtone recommended maximum 150 KB; Alarm 100 KB (others as small as possible)

**Format:** .wma

**Compression:** WMA (128 kbps/stereo; 64 kbps/mono)

**Sound length:** Ringtones 5-15 seconds; Alarm 5-15 seconds; Calendar 1-3 seconds; Alerts 0.5-1.5 seconds

**Appropriate volumes:** Sounds should be appropriately balanced with ringtones and system sounds that ships as part of the OS.

**Minimal distortion** from phone speaker, at full volume.

<a href="" id="constraints---firstvariationonly"></a>**Constraints:** FirstVariationOnly  

<a href="" id="instructions-"></a>**Instructions:**  
**To add an additional alarm sound**

1. Create a .dll that contains the alarm display name. For more information on how to do this, see [Create a resource-only .dll for localized strings](create-a-resource-only-dll-for-localized-strings.md).

2. Create a customization answer file using the contents shown in the following code sample.

   ```XML
   <?xml version="1.0" encoding="utf-8" ?>
   <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                        Name="AdditionalAlarms"  
                        Description="Use to add additional alarm sounds and set a new default alarm sound."  
                        Owner=""  
                        OwnerType="OEM"> 
      
      <Static>  

       <Settings Path="Localization/MUI">  
         <!-- Use to add your base MUI DLL file -->
         <Asset Name="BaseDll" Source="" />

         <!-- Use to specify the language MUI packages (*.dll.mui) for the languages you are supporting and have localized strings for -->
         <Asset Name="LanguageDll/$(langid)" Source="" />
         <Asset Name="LanguageDll/$(langid)" Source="" />
         <Asset Name="LanguageDll/$(langid)" Source="" />
         <!-- Add as many as you need -->         
       </Settings>  

       <!-- Use to add one additional alarm sound -->
       <Settings Path="EventSounds">  
         <Asset Name="AlarmSounds" DisplayName="@DisplayStrings.dll,-Offset" Source="" />
       </Settings>

      </Static>

   </ImageCustomizations>
   ```

3. Specify an `Owner`.

4. Add the resource-only .dll that contains the alarm display name by setting the `BaseDll` asset to point to the location of your base MUI DLL file. For example: *C:\\Path\\DisplayStrings.dll*.

5. Add the language MUI packages (\*.dll.mui) for all the languages you are supporting and have localized strings for. To do this:

   -   Set the asset's `Name` to `LanguageDll/`*$(langid)* where *$(langid)* corresponds to the language. For example: *LanguageDll/en-US*.

   -   Set the asset's `Source` to the location of the .dll.mui file for that language. For example: *C:\\Path\\en-us\\DisplayStrings.dll.mui*.

   -   Repeat the previous steps for the other languages.

       The following example shows the customization answer file entries for en-US, fr-CA, and es-MX languages:

       ```XML
       <Asset Name="LanguageDll/en-US" Source="C:\Path\en-us\DisplayStrings.dll.mui” />
       <Asset Name="LanguageDll/fr-CA" Source="C:\Path\fr-CA\DisplayStrings.dll.mui" />
       <Asset Name="LanguageDll/es-MX" Source="C:\Path\es-MX\DisplayStrings.dll.mui" />
       ```

6. Add one additional alarm sound by adding an `AlarmSounds` asset. To do this:

   - Set the asset's `Name` to `AlarmSounds`.

   - Set the `DisplayName` to the name of the resource-only .dll file and specify the string offset. Replace *DisplayStrings.dll* with the name of your .dll file and replace *Offset* with the correct offset for the localized string. For example: <em>@DisplayStrings.dll,-104</em>

   - Set `Source` to the full path to the custom alarm sound on your development machine. For example: *C:\\Path\\NewAlarmSound.wma*.

If you are setting the default alarm sound in addition to adding other alarm sound files, see the *To set a new default alarm* section.

**To set a new default alarm**

1.  Create a customization answer file using the contents shown in the following example:

    ```XML
        <!-- Use to set a new default alarm sound -->
        <Settings Path="EventSounds">  
          <Setting Name="DefaultAlarmSound" Value="" /> 
        </Settings>  
    ```

2.  Set the `Value` of the default alarm sound to the file name of the default alarm sound you want to use. For example: *NewAlarmSound.wma*

<a href="" id="testing-"></a>**Testing:**  
1.  Flash the build containing this customization and multiple display languages to a mobile device.

2.  Go to **Alarms & Clock** in the apps list.

3.  Tap the **+** or add button to create a new alarm.

4.  Choose **Pick from ringtones** and verify the custom alarm sound is in the **Sounds** list.

5.  If a new default alarm sound is set, verify the **Sound** drop-down list defaults to the specified alarm sound.

6.  Verify the custom alarm name is correct for all display languages on the device.

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
