---
title: Configure OEM lens apps to launch above the lock screen
description: OEM can configure lens apps to launch above the lock screen.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 80c52bdf-dce2-4f93-b11a-f0f3a5422ead


ms.date: 05/02/2017
ms.topic: article


---

# Configure OEM lens apps to launch above the lock screen


OEM can configure lens apps to launch above the lock screen.

For lens apps that OEMs have configured to be user selectable default camera app, OEMs can add functionality to launch these lens apps above the lock screen when the user presses the camera button.

Microsoft recommends that OEMs configure only up to five (5) lens apps capable of running above the lock screen. The lens apps can be preloaded by OEMs or installed by users from the Microsoft Store.

<a href="" id="constraints---none"></a>**Constraints:** None  

<a href="" id="instructions-"></a>**Instructions:**  
The steps for configuring an OEM lens app to run above the lock screen are very similar to [Adding OEM lens apps as options for the default camera](adding-oem-lens-apps-as-options-for-the-default-camera.md), but with the additional step of designating it as a lens app that can run above the lock screen.

1.  Create a customization answer file using the contents shown in the following code sample.

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>  
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name="OEMLensAboveLock"  
                         Description="Use to configure an OEM lens app to launch above the lock screen when the user presses the camera button."  
                         Owner=""  
                         OwnerType="OEM"> 
      
      <Static>  

       <!-- Preload an OEM lens app -->
       <Applications>
          <!-- For each app, specify the source (.xap/.appx), license, and ProvXML files. -->
          <Application Source=""
                       License=""
                       ProvXML="" />
       </Applications>

       <!-- Replace $(LensAppGuid) with the app ID of the lens app you want to show in the camera CPL -->
       <Settings Path="Photos/LensApps/$(LensAppGuid)">  
         
          <!-- Set the value to the friendly name of the OEM lens app -->
          <Setting Name="Title" Value="" />

          <!-- Set this to the version of the OEM lens app version that you want to launch above the lock screen -->
          <Setting Name="MinVersionAboveLock" Value="" />  
       </Settings>  

       <!-- You can add up to 5 OEM lens apps to show in the camera CPL. For other OEM lens apps that you want to enable to run 
            above the lock screen, you must set the MinVersionAboveLock setting for each of these. -->
      </Static>

    </ImageCustomizations>
    ```

2.  Specify an `Owner`.

3.  If you are preloading a lens app, add an **Applications** parent element and add an **Application** child element to correspond to each lens app that you are preloading. For each **Application**, specify the `Source` (.xap/.appx), `License`, and `ProvXML` files that correspond to the lens app you are preloading.

4.  **To specify the OEM lens app to show in the camera CPL:**

    1.  Replace *$(LensAppGuid)* with the app ID of the lens app you want to show in the camera CPL.

    2.  Replace *Title* with the friendly name of the lens app. For example, *Contoso Fish Eye Lens*.

    3.  Specify up to 5 lens apps by creating a registry entry for each as shown in the preceding example. For example, to configure two lens apps to show in the camera CPL, you need to add the following registry entries:

        ```
           <Settings Path="Photos/LensApps/{00000000-0000-0000-0000-000000000000}">       
              <Setting Name="Title" Value="Contoso Fish Eye Lens" />  
           </Settings> 

           <Settings Path="Photos/LensApps/{00000000-0000-0000-1000-000000000000}">       
              <Setting Name="Title" Value="Contoso Sepia Lens" />  
           </Settings> 
        ```

5.  **To designate an OEM lens app to run above the lock screen:**

    1.  Add the `MinVersionAboveLock` setting within the settings group for the OEM lens app.

    2.  Set the value of `MinVersionAboveLock` to a string that is equal to the version of the first published OEM lens app version that fully complies with the guidelines and requirements outlined in the previous section. If the lens app has an equal or higher version to the value that you set for `MinVersionAboveLock`, the lens app will launch above the lock screen when the camera button is pressed on a PIN-locked screen. Otherwise, the PIN unlock screen shows when the camera button is pressed, and if the user enters the correct password, the lens app will launch.

        OEMs may set the value for `MinVerAboveLock` to a sufficiently large version string so that you may release the phone first and later publish an updated lens app to the Windows Phone Store that fully complies with the requirements and guidelines for OEM lens apps that launch above the lock screen.

        In the following example, the Contoso Sepia Lens app has been designated as the OEM lens app to run above the lock screen.

        ```XML
           <Settings Path="Photos/LensApps/{00000000-0000-0000-0000-000000000000}">       
              <Setting Name="Title" Value="Contoso Fish Eye Lens" />  
           </Settings> 

           <Settings Path="Photos/LensApps/{00000000-0000-0000-1000-000000000000}">       
              <Setting Name="Title" Value="Contoso Sepia Lens" />  
              <Setting Name="MinVersionAboveLock" Value="1.0.0.0" />  
           </Settings>
        ```

<a href="" id="testing-"></a>**Testing:**  
1.  Flash the build that contains this customization to a phone.

2.  Install the OEM lens app(s).

3.  Go to the **Settings** &gt; **applications** &gt; **photos+camera** screen and verify that the lens apps that you have specified show up as one of the choices under **Pressing the camera button opens**.

    Choose a lens app that you have configured to run above the lock screen and set it as the default camera.

4.  Go to **Settings** &gt; **lock screen**, turn **Password** on, then set a password or PIN.

5.  Lock the phone.

6.  Press and hold the camera button while the phone is locked. Verify that the lens app that you chose in Step 3 is launched.

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
