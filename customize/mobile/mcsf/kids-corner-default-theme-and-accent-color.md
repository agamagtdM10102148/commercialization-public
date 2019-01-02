---
title: Kid's Corner default theme and accent color
description: Partners can set the default theme, including the background color (light or dark) and the accent color for Kid’s Corner.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: cf8ec46a-4168-47a4-91e0-76fd21c2b2e4


ms.date: 05/02/2017
ms.topic: article


---

# Kid's Corner default theme and accent color


Partners can set the default theme, including the background color (light or dark) and the accent color for Kid’s Corner.

<a href="" id="constraints---firstvariationonly"></a>**Constraints:** FirstVariationOnly  

<a href="" id="instructions-"></a>**Instructions:**  
1.  Create a customization answer file using the contents shown in the following code sample.

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>  
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name="KidsCornerThemeAndAccent"
                         Description="Use to set the default theme and accent color for Kid's Corner."  
                         Owner=""  
                         OwnerType="OEM"> 
      
      <Static>  

        <Settings Path="KidsCorner">  
          <Setting Name="DefaultThemeBackground" Value="" /> 
          <Setting Name="DefaultThemeAccentColor" Value="" />
        </Settings>  

      </Static>
    </ImageCustomizations>
    ```

2.  Specify an `Owner`.

3.  Set `DefaultThemeBackground` to specify a theme. The possible values are:

    -   **0** for light

    -   **1** for dark

4.  Set `DefaultThemeAccentColor` to specify an accent color ID. You can use either the corresponding decimal value or the corresponding hexadecimal value (with the 0x prefix) as shown in the following table.

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Accent color ID (in hexadecimal)</th>
    <th>Accent color ID (in decimal)</th>
    <th>Color name</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>0x0</p></td>
    <td><p>0</p></td>
    <td><p>Lime</p></td>
    </tr>
    <tr class="even">
    <td><p>0x1</p></td>
    <td><p>1</p></td>
    <td><p>Green</p></td>
    </tr>
    <tr class="odd">
    <td><p>0x2</p></td>
    <td><p>2</p></td>
    <td><p>Emerald</p></td>
    </tr>
    <tr class="even">
    <td><p>0x3</p></td>
    <td><p>3</p></td>
    <td><p>Teal</p></td>
    </tr>
    <tr class="odd">
    <td><p>0x4</p></td>
    <td><p>4</p></td>
    <td><p>Cyan</p></td>
    </tr>
    <tr class="even">
    <td><p>0x5</p></td>
    <td><p>5</p></td>
    <td><p>Cobalt</p></td>
    </tr>
    <tr class="odd">
    <td><p>0x6</p></td>
    <td><p>6</p></td>
    <td><p>Indigo</p></td>
    </tr>
    <tr class="even">
    <td><p>0x7</p></td>
    <td><p>7</p></td>
    <td><p>Violet</p></td>
    </tr>
    <tr class="odd">
    <td><p>0x8</p></td>
    <td><p>8</p></td>
    <td><p>Pink</p></td>
    </tr>
    <tr class="even">
    <td><p>0x9</p></td>
    <td><p>9</p></td>
    <td><p>Magenta</p></td>
    </tr>
    <tr class="odd">
    <td><p>0xA</p></td>
    <td><p>10</p></td>
    <td><p>Crimson</p></td>
    </tr>
    <tr class="even">
    <td><p>0xB</p></td>
    <td><p>11</p></td>
    <td><p>Red</p></td>
    </tr>
    <tr class="odd">
    <td><p>0xC</p></td>
    <td><p>12</p></td>
    <td><p>Orange</p></td>
    </tr>
    <tr class="even">
    <td><p>0xD</p></td>
    <td><p>13</p></td>
    <td><p>Amber</p></td>
    </tr>
    <tr class="odd">
    <td><p>0xE</p></td>
    <td><p>14</p></td>
    <td><p>Yellow</p></td>
    </tr>
    <tr class="even">
    <td><p>0xF</p></td>
    <td><p>15</p></td>
    <td><p>Brown</p></td>
    </tr>
    <tr class="odd">
    <td><p>0x10</p></td>
    <td><p>16</p></td>
    <td><p>Olive</p></td>
    </tr>
    <tr class="even">
    <td><p>0x11</p></td>
    <td><p>17</p></td>
    <td><p>Steel</p></td>
    </tr>
    <tr class="odd">
    <td><p>0x12</p></td>
    <td><p>18</p></td>
    <td><p>Mauve</p></td>
    </tr>
    <tr class="even">
    <td><p>0x13</p></td>
    <td><p>19</p></td>
    <td><p>Taupe</p></td>
    </tr>
    <tr class="odd">
    <td><p>0x65</p></td>
    <td><p>101</p></td>
    <td><p>CustomAccentColor1</p></td>
    </tr>
    <tr class="even">
    <td><p>0x66</p></td>
    <td><p>102</p></td>
    <td><p>CustomAccentColor2</p></td>
    </tr>
    <tr class="odd">
    <td><p>0x67</p></td>
    <td><p>103</p></td>
    <td><p>CustomAccentColor3</p></td>
    </tr>
    <tr class="even">
    <td><p>0x68</p></td>
    <td><p>104</p></td>
    <td><p>CustomAccentColor4</p></td>
    </tr>
    </tbody>
    </table>


<a href="" id="testing-"></a>**Testing:**  
1.  Flash the build containing this customization to a device.

2.  Launch **Kid’s Corner**.

3.  Verify that the Kid’s Corner theme and accent color match the defaults you set in the registry.

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
