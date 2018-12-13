---
title: Building images for FWVGA panels with static software buttons
description: OEMs can build images for FWVGA (480 x 854) display panels where the Back, Home, and Search buttons are rendered on the screen by the OS instead of using hardware buttons.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: dc9467d4-8593-4939-a223-d1c69adab320
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# Building images for FWVGA panels with static software buttons


OEMs can build images for FWVGA (480 x 854) display panels where the Back, Home, and Search buttons are rendered on the screen by the OS instead of using hardware buttons. In these types of images, the bottom 54 scan lines of the display panel are reserved to render the software buttons.

<a href="" id="constraints---none"></a>**Constraints:** None  

<a href="" id="instructions-"></a>**Instructions:**  
To build an FWVGA image with software-rendered buttons:

1.  Create a customization answer file using the contents shown in the following code sample.

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>  
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name="FWVGASoftwareButtons"  
                         Description="Use to generate an image that supports an FWVGA display panel and software Back, Start, and Search buttons."  
                         Owner=""  
                         OwnerType="OEM">   
      <Static>  

        <Settings Path="Graphics/D3D/DisplayResolutionOverride">  
          <Setting Name="DisplayPanelOverrideWidth" Value="0x1E0" />  
          <Setting Name="DisplayPanelOverrideHeight" Value="0x356" />  
          <Setting Name="TouchPanelOverrideWidth" Value="0x1E0" />  
          <Setting Name="TouchPanelOverrideHeight" Value="0x356" />  
        </Settings>  

        <Settings Path="Input/Touch/CapButtons">  

          <Setting Name="ButtonCount" Value="" />   
          <Setting Name="ButtonAreaTotal" Value="" />   

          <Setting Name="Name0" Value="" />   
          <Setting Name="VKey0" Value="" />
          <Setting Name="Area0" Value="" />   

          <Setting Name="Name1" Value="" />   
          <Setting Name="VKey1" Value="" />   
          <Setting Name="Area1" Value="" />   

          <Setting Name="Name2" Value="" />   
          <Setting Name="VKey2" Value="" />   
          <Setting Name="Area2" Value="" />   

          <Setting Name="VibrateSupport" Value="" />   
          <Setting Name="VibrateDuration" Value="" />   
          <Setting Name="VibrateIntensity" Value="" />   

        </Settings>  

        <Settings Path="Shell/NavigationBar">  
          <Setting Name="Color" Value="" />  
        </Settings>  

      </Static>
    </ImageCustomizations>
    ```

2.  Specify an `Owner` value in the customization answer file.

3.  Do not change the `DisplayPanelOverrideWidth`, `DisplayPanelOverrideHeight`, `TouchPanelOverrideWidth`, and `TouchPanelOverrideHeight` values shown in the example.

4.  For the `ButtonCount`, `ButtonAreaTotal`, `Area`*n*, `Name`*n*, and `VKey`*n* settings, specify values as described in [Defining capacitive button behavior](defining-capacitive-button-behavior.md).

5.  **Optional**. To enable the built-in vibration feedback mechanism for the buttons, include the `VibrateSupport`, `VibrateDuration`, and `VibrateIntensity` settings and specify values as described in [Defining capacitive button behavior](defining-capacitive-button-behavior.md). If you do not want to enable vibration feedback, you can omit these settings from the customization answer file.

6.  **Optional**. To specify the default color of the software-rendered Back, Home, and Search buttons, include the `Color` setting and set `Value` to one of the following values. If you do not want to specify the default color, you can omit the `Color` setting and its parent `Settings` element.

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
    <td><p>0</p></td>
    <td><p>The buttons are black. This is the default value.</p></td>
    </tr>
    <tr class="even">
    <td><p>1</p></td>
    <td><p>The color of the buttons matches the current theme chosen by the user (black for dark theme, white for light theme).</p></td>
    </tr>
    <tr class="odd">
    <td><p>2</p></td>
    <td><p>The color of the buttons matches the current accent color chosen by the user.</p></td>
    </tr>
    </tbody>
    </table>

     

7.  If you have not done so already, create an OEMInput XML file to define the set of packages to include in your phone image, and configure your computer to use the imaging tools. For more information, see [Building a mobile image using ImgGen.cmd](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/building-a-phone-image-using-imggencmd).

8.  In your OEMInput XML file, set the value of the **Resolution** element to 480x800. This configuration ensures that WVGA assets are used for the FWVGA image. Only WVGA assets can be used in FWVGA images that use software-rendered buttons.

9.  In your OEMInput XML file, add the **NAVIGATIONBAR** feature to the **Microsoft** element that is a child of the **Features** element. This feature adds a phone setting that enables users to configure the color of the software buttons.

    ```XML
    <Features>
      <Microsoft>
        <Feature>NAVIGATIONBAR</Feature>
      </Microsoft>
    </Features>
    ```

    For more information, see [Optional features for building images](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/optional-features-for-building-images).

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
