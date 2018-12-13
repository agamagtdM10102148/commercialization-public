---
title: Disable video upgrade Store navigation
description: Disable automatic navigation to the Microsoft Store when the user attempts a video upgrade for which there is no installed app.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f31e85b2-d003-4c63-abcf-db48f79ac4bd
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# Disable video upgrade Store navigation


Disable automatic navigation to the Microsoft Store when the user attempts a video upgrade for which there is no installed app.

By default, if there are no compatible video upgrade apps installed on the phone, when a user taps the video upgrade button during a phone call, a dialog is launched and the phone will navigate to the Microsoft Store. Partners can change this behavior so that if the user taps the video upgrade button, a dialog is launched that informs the user that no video app is installed, but the phone will not navigate to the Microsoft Store directly.

<a href="" id="constraints---firstvariationonly"></a>**Constraints:** FirstVariationOnly  

<a href="" id="instructions-"></a>**Instructions:**  
1.  Create a customization answer file using the contents shown in the following code sample.

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>  
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name="DisableVideoUpgradeStoreNavigation"  
                         Description="Use to configure whether tapping the video upgrade button will launch a dialog to navigate
                                      to the Windows Phone Store or inform the user that no app is installed."  
                         Owner=""  
                         OwnerType="OEM"> 
      
      <Static>  

        <Settings Path="Phone/PhoneSettings">  
          <Setting Name="DisableVideoUpgradeStoreNavigation" Value="" />
        </Settings>  

      </Static>

    </ImageCustomizations>
    ```

2.  Specify an `Owner`.

3.  Set the `DisableVideoUpgradeStoreNavigation` value to one of the following:

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
    <td><p>Tapping the video upgrade button launches a dialog that navigates to the Store if no compatible video upgrade apps are installed on the phone.</p>
    <p>This is the default behavior.</p></td>
    </tr>
    <tr class="even">
    <td><p>1 or 'True'</p></td>
    <td><p>Tapping the video upgrade button launches a dialog that informs the user that there is no video app is installed. The phone does not navigate to the Store.</p></td>
    </tr>
    </tbody>
    </table>

     

<a href="" id="testing-steps-"></a>**Testing steps:**  
1.  Flash the build containing this customization to a phone that has a UICC or Wi-Fi connection.

2.  Make sure that there are no compatible video upgrade apps installed on the phone and then open the **Phone** app and call someone.

    -   If `DisableVideoUpgradeStoreNavigation` is set to 0 or 'False' (or you did not change the default OS behavior), verify that a dialog is launched and that the phone navigates to the Store.

    -   If `DisableVideoUpgradeStoreNavigation` is set to 1 or 'True', verify that a dialog is launched that informs the user that no video app is installed and the phone does not automatically navigate to the Store.

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
