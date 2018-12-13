---
title: Extract phone numbers in strings
description: Partners can extend the entity extraction feature that recognizes phone numbers in text. This customization allows strings of numbers that are concatenated to a string to be recognized.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 070330f1-34a8-4cdf-a987-7f2cadeb7450
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# Extract phone numbers in strings


Partners can extend the entity extraction feature that recognizes phone numbers in text. This customization allows strings of numbers that are concatenated to a string to be recognized.

Windows supports entity extraction in the Messaging app (which is also shared with the Email and Calendar apps). This feature can detect a sequence of numbers, which can be a phone number, in a received SMS or MMS message and enable the user to call the phone number by making it a target that the user can tap and easily save, or call without retyping the number.

This customization extends entity extraction by enabling OEMs to specify whether a sequence of numbers that is concatenated to a string (in a left-to-right device language including English, French, Italian, Simplified Chinese, Traditional Chinese, and other left-to-right languages) should be detected as a phone number. The minimum amount of numbers that the OS considers as a phone number is five (5).

When this feature is enabled, only the numeric sequence is underlined and shown as a tappable string; the non-numeric character is not underlined. When this feature is enabled on devices that have dual SIMs, it is applied to both SIM slots.

<a href="" id="constraints---firstvariationonly"></a>**Constraints:** FirstVariationOnly  

<a href="" id="instructions-"></a>**Instructions:**  
1.  Create a customization answer file using the contents shown in the following code sample.

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>  
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name="ExtractPhoneNumbersInStrings"  
                         Description="Use to tag any 5-or-more digit number as a phone number that users can tap even when 
                                      there is no space between the string and the number."  
                         Owner=""  
                         OwnerType="OEM"> 
      
      <Static>  

        <Settings Path="Messaging/GlobalSettings">  
          <Setting Name="ExtractPhoneNumbersInStrings" Value="" /> 
       </Settings>  

      </Static>

    </ImageCustomizations>
    ```

2.  Specify an `Owner`.

3.  Set `ExtractPhoneNumbersInStrings` to one of the following values:

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
    <td><p>Specifies that the OS should not detect a sequence of five or more digits concatenated to a string as a tappable phone number.</p>
    <p>For example, when the value is set to 0 or 'False', a sequence of digits such as 55512 is detected as a phone number, but P55512 or ABC55512EFG are not.</p></td>
    </tr>
    <tr class="even">
    <td><p>1 or 'True'</p></td>
    <td><p>Specifies that the OS should detect a sequence of five or more digits concatenated to a string as a tappable phone number.</p>
    <p>For example, when the value is set to 1 or 'True', a sequence of digits such as 55512 is detected as a phone number while the sequence '55512' in the strings P55512 or ABC55512EFG are also detected as a phone number.</p></td>
    </tr>
    </tbody>
    </table>

     

<a href="" id="testing-steps-"></a>**Testing steps:**  
Work with your mobile operator partner to fully test this customization on their network.

1.  Flash the build containing this customization to a device with at least one active SIM or UICC.

2.  Make sure that the device language is set to a language that has left-to-right characters, such as English, French, Italian, Simplified Chinese, and Traditional Chinese.

3.  Open the Messaging app.

4.  Receive several SMS or MMS messages that contain a sequence of digits that are:

    1.  Less than 5 digits

    2.  More than 5 digits

    3.  Less than 5 digits and have the digits concatenated to one or more non-numerical characters, such as P1234 or PhoneNumber1234.

    4.  More than 5 digits and with the digits concatenated to one or more non-numerical characters, such as P55512 or PhoneNumber55512.

5.  For each case specified in the previous step, verify whether the sequence of numbers is detected as a phone number by the OS based on the value you specified for the `ExtractPhoneNumbersInStrings` setting.

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
