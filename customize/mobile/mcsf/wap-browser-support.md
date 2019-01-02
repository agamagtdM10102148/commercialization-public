---
title: WAP browser support (CN and IN only)
description: For phones that will ship in China and India, OEMs can add one preloaded WAP browser to the phone, which will automatically be launched when the user tries to open a WAP link.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 6be34aeb-bbaa-4675-8861-d80965393805


ms.date: 05/02/2017
ms.topic: article


---

# WAP browser support (CN and IN only)


For phones that will ship in China and India, OEMs can add one preloaded WAP browser to the phone, which will automatically be launched when the user tries to open a WAP link. The WAP browser must be written as an application, and must go through the standard Microsoft Store submission process.

<a href="" id="constraints---none"></a>**Constraints:** None  

<a href="" id="instructions-"></a>**Instructions:**  
1.  Create a WAP browser application and ensure that the following settings are configured properly:

    1.  Add the **ID\_CAP\_NETWORKING** capability to the application manifest of the WAP browser application.

    2.  Add the following XML to the **App** element of the application manifest.

        ```XML
        <Extensions> 
           <Protocol Name="wap" Category="phone.protocol" TaskID="_default" NavUriFragment="uri=%s"/>
           <FileTypeAssociation Name="TestFileAssoc1" Category="phone.fileTypeAssociation" TaskID="_default" 
              NavUriFragment="fileID=%s">
              <DisplayName>Test Assoc1</DisplayName> 
              <Logo>res://StartMenu!AppIconMail.png</Logo>
              <SupportedFileTypes> 
                 <FileType ContentType="text/vnd.wap.wml">.wml</FileType> 
              </SupportedFileTypes> 
           </FileTypeAssociation> 
        </Extensions>
        ```

        You can replace the values for following elements:

        -   **FileTypeAssociation Name**

        -   **DisplayName**

        -   **Logo**

    3.  The WAP browser application manifest file should look like the following XML.

        ```XML
        <?xml version="1.0" encoding="UTF-8"?>
        <Deployment AppPlatformVersion="8.0" xmlns="http://schemas.microsoft.com/windowsphone/2009/deployment"> 
           <App xmlns="" Publisher="TestWAPApp" Description="Sample description" Author="TestWAPApp author" 
              Genre="apps.normal" Version="1.0.0.0" RuntimeType="Silverlight" Title="TestWAPApp" 
              ProductID="{bca7dae7-f8c3-4dc2-9a98-d6bf62b81a29}"> 
              <IconPath IsResource="false" IsRelative="true">ApplicationIcon.png</IconPath> 
              <Capabilities> <Capability Name="ID_CAP_NETWORKING"/> </Capabilities> 
              <Extensions> 
                 <Protocol Name="wap" Category="phone.protocol" TaskID="_default" NavUriFragment="uri=%s"/>
                 <FileTypeAssociation Name="TestFileAssoc1" Category="phone.fileTypeAssociation" 
                    TaskID="_default" NavUriFragment="fileID=%s">
                    <DisplayName>Test Assoc1</DisplayName> 
                    <Logo>res://StartMenu!AppIconMail.png</Logo>
                    <SupportedFileTypes> 
                       <FileType ContentType=" text/vnd.wap.wml ">.wml</FileType> 
                    </SupportedFileTypes> 
                 </FileTypeAssociation> 
              </Extensions> 
              <Tasks>
                 <DefaultTask Name="_default" NavigationPage="MainPage.xaml"/>
              </Tasks> 
              <Tokens> 
                 <PrimaryToken TaskName="_default" TokenID="CustomUriTargetManagedApp1Token">
                    <TemplateType5> 
                       <BackgroundImageURI IsResource="false" IsRelative="true">Background.png</BackgroundImageURI> 
                       <Count>0</Count> 
                       <Title>TestWAPApp</Title> 
                    </TemplateType5> 
                 </PrimaryToken> 
              </Tokens> 
           </App> 
        </Deployment>
        ```

        For more information about file and URI associations, see the Windows 10 SDK documentation.

2.  After you have created the WAP browser application and gone through the Microsoft Store submission process to obtain your application license, follow these steps to preload the WAP browser application to the phone.

    1.  Create a customization answer file using the contents shown in the following code sample.

        ```XML
        <?xml version="1.0" encoding="utf-8" ?>  
        <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                             Name="WAPBrowser"  
                             Description="Use to preload a WAP browser to the phone, which will be automatically launched when the user tries to open a WAP link."  
                             Owner=""  
                             OwnerType="OEM"> 
          
          <Static>  
            <Applications>
              <Application Source="C:\Path\OEM_WAPBrowser.xap"
                           License="C:\Path\OEM_WAPBrowser_License.xml"
                           ProvXML="C:\Path\MPAP_OEM_WAPBrowser.provxml" />
            </Applications>
          </Static>

        </ImageCustomizations>
        ```

    2.  Specify an `Owner`.

    3.  Set the `Source` value to the path and file name of your .xap or .appx file. For example, *C:\\Path\\OEM\_WAPBrowser.xap*.

    4.  Set the `License` value to the path and file name of license file for your WAP browser app. For example, *C:\\Path\\OEM\_WAPBrowser\_License.xml*.

    5.  Set the `ProvXML` value to the path and file name for your WAP browser app. For example, *C:\\Path\\MPAP\_OEM\_WAPBrowser.provxml*.

<a href="" id="testing-"></a>**Testing:**  
1.  Flash the build containing this customization to a phone with a SIM or with a data connection over Wi-Fi.

2.  Open Microsoft Edge and enter a WAP link. The WAP browser should open automatically and display your web page.

## Related topics

[Prepare for Windows mobile development](https://docs.microsoft.com/en-us/windows-hardware/manufacture/mobile/preparing-for-windows-mobile-development)

[Customization answer file overview](https://docs.microsoft.com/en-us/windows-hardware/customize/mobile/mcsf/customization-answer-file)
