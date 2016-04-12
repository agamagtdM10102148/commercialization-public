---
Description: 'This guide walks you through creating Windows 10 IoT Core (IoT Core) images that can be flashed to retail devices and maintained after they have been delivered to your customers.'
MS-HAID: 'p\_iot\_core.iot\_core\_manufacturing\_guide'
MSHAttr: 'PreferredLib:/library'
title: IoT Core manufacturing guide
---

# IoT Core manufacturing guide


\[Some information relates to pre-released product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here. An app that calls an API introduced in Windows 10 Anniversary SDK Preview Build 14295 cannot be ingested into the Windows Store during the Preview period.\]

This guide walks you through creating Windows 10 IoT Core (IoT Core) images that can be flashed to retail devices and maintained after you've sent them to your customers.

To do this, we'll show you how to wrap your apps, files, settings, and drivers into packages. Packages help OEMs, ODMs, developers, and Microsoft all work together to deliver security and feature updates to your devices without stomping on each other's work.

This guide is written toward OEMs, but ODMs and developers can use the same processes to test IoT Core apps, drivers, board support packages (BSPs).

## <span id="Scenarios"></span><span id="scenarios"></span><span id="SCENARIOS"></span>Scenarios


Want to jump right in? Start here: [Get the tools needed to customize Windows IoT Core](set-up-your-pc-to-customize-iot-core.md), and then try out our scenarios.

-   [Step 1: Create a basic image](create-a-basic-image.md): Make sure the tools you installed work, and load the basic IoT Core image onto a test device. While you're here, learn about the tools built into the basic image.
-   [Step 2: Add an app to your image](deploy-your-app-with-a-standard-board.md): Take one of our sample apps, package it up, make a fresh image, and load it onto the device.
-   [Step 3: Add a file and a registry setting to an image](add-a-registry-setting-to-an-image.md): Same drill, this time with sample files and registry keys.
-   [Step 4: Add a provisioning package to an image](add-a-provisioning-package-to-an-image.md): Update Windows settings such as presetting Wi-Fi.

## <span id="Concepts"></span><span id="concepts"></span><span id="CONCEPTS"></span>Concepts


We'll use the samples in these guides to build the following structure for your images. You can use the same structure to build your retail images. In general terms:

1.  Add each of your customizations (drivers, apps, settings) into signed package files.
2.  Create a summary list of these packages, called a feature manifest (FM), which lists your packages by feature name.
3.  Get IoT Core's packages and FMs from us.
4.  Get the packages and FMs from your hardware manufacturer, such as a board support package (BSP) and the BSPFM.
5.  List the FMs and features you want to install in an OEMInput file.
6.  Create a flashable image file (FFU) using ImgGen and the OEMInput file.
7.  Flash the image to your devices.

![iot core image creation process](images/oemworkflow.png)

### <span id="Packages"></span><span id="packages"></span><span id="PACKAGES"></span>Packages

Packages are the logical building blocks of IoT Core. They contain all the files, libraries, registry settings, executables, and data on the device. From device drivers to system files, every component must be contained in a package. This modular architecture allows for precise control of updates: a package is the smallest serviceable unit on the device.

Each package contains:

-   The contents of the package, such as a signed driver binary or a signed appx binary.
-   A package definition (.pkg.xml) file specifies the contents of the package and where they should be placed in the final image. See %SRC\_DIR%\\Packages\\ directory for various samples of package files.
-   A signature. This can be a test or retail certificate.

The `pkggen` tool combines these items into signed packages. Our samples include scripts: `createpkg`, `createprovpkg` and `createupdatepkgs`, which call pkggen to create packages for our drivers, apps, and settings.

The process is similar to that used by Windows 10 Mobile. To learn more about creating packages, see [Creating mobile packages](https://msdn.microsoft.com/library/dn756642).

### <span id="Feature_manifests__FMs_"></span><span id="feature_manifests__fms_"></span><span id="FEATURE_MANIFESTS__FMS_"></span>Feature manifests (FMs)

After you've put everything into packages, you'll use FM files to list which of your packages belong in the final image.

You can use as many FMs into an image as you want. In this guide, we refer to the following FMs:

-   **OEMFM.xml** includes features an OEM might add to a device, such as the app and a provisioning package.
-   **BSPFM.xml** includes features that a hardware manufacturer might use to define a board. For example, OEM\_RPi2FM.xml includes all of the features used for the Raspberry Pi 2.
-   **ProdFM.xml** includes features that make up IoT Core. ProdFM refers to a fully-signed version of the OS.

The process is similar to that used by Windows 10 Mobile. To learn more, see [Feature manifest file contents](https://msdn.microsoft.com/library/windows/hardware/dn756745).

You'll list which of the features to add by using these tags:

-   &lt;BasePackages&gt;: Packages that you always included in your images, for example, your base app.
-   &lt;Features&gt;\\&lt;OEM&gt;: Other individual packages that might be specific to a particular product design.

### <span id="Creating_the_image__ImgGen_and_the_image_configuration_file__OEMInput.xml_"></span><span id="creating_the_image__imggen_and_the_image_configuration_file__oeminput.xml_"></span><span id="CREATING_THE_IMAGE__IMGGEN_AND_THE_IMAGE_CONFIGURATION_FILE__OEMINPUT.XML_"></span>Creating the image: ImgGen and the image configuration file (OEMInput.xml)

To create the final image, you'll use the `imggen` tool with an image configuration file, **OEMInput.xml file**.

These are the same tools used to create Windows 10 Mobile images. To learn more, see [OEMInput file contents](https://msdn.microsoft.com/library/windows/hardware/dn756778).

The image configuration file lists:

-   The feature manifests (FMs) and the packages that you want to install from each one.
-   An **SoC** chip identifier, which is used to help set up the device partitions. This value is required, even if you're not using one of the devices listed. Start with the value for the hardware that most closely resembles your device:

    **RPi2**: Raspberry Pi 2 or Raspberry Pi 3 (ARM)

    **MBM**: Intel Minnowboard Max (x86)

    **DB**: Qualcomm DragonBoard (ARM32)

-   The ReleaseType (either **Production** or **Test**).

    **Retail builds**: We recommend creating retail images early on in your development process to verify that everything will work when you are ready to ship.

    These builds contain all of the security features enabled.

    To use this build type, all of your code must be signed using retail (not test) code signing certificates.

    For a sample, see %SRC\_DIR%\\Products\\SampleA\\RetailOEMInput.xml.

    **Test builds**: Use these to try out new versions of your apps and drivers created by you and your hardware manufacturer partners.

    These builds have some security features disabled, which allows you to use either test-signed or production-signed packages.

    These builds also include developer tools such as debug transport, SSH, and PowerShell, that you can use to help troubleshoot issues.

    For a sample, see %SRC\_DIR%\\Products\\SampleA\\TestOEMInput.xml.

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"></th>
    <th align="left">Retail builds</th>
    <th align="left">Test builds</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left">Image release type</td>
    <td align="left">ReleaseType: <strong>Production</strong></td>
    <td align="left">ReleaseType: <strong>Test</strong></td>
    </tr>
    <tr class="even">
    <td align="left">Package release type</td>
    <td align="left">Only Production Type packages are supported</td>
    <td align="left">Both Production Type or Test Type are supported</td>
    </tr>
    <tr class="odd">
    <td align="left">Test-signed packages</td>
    <td align="left">Not supported</td>
    <td align="left">Supported.
    <p>IOT_ENABLE_TESTSIGNING feature must be included.</p></td>
    </tr>
    <tr class="even">
    <td align="left">Code integrity check</td>
    <td align="left">Supported. By default, this is enabled.</td>
    <td align="left">Not supported.
    <p>IOT_DISABLE_UMCI feature must be included.</p></td>
    </tr>
    </tbody>
    </table>

     

## <span id="OK__let_s_try_it_"></span><span id="ok__let_s_try_it_"></span><span id="OK__LET_S_TRY_IT_"></span>OK, let's try it!


Start here: [Get the tools needed to customize Windows IoT Core](set-up-your-pc-to-customize-iot-core.md).

## <span id="related_topics"></span>Related topics


[What's in the Windows ADK IoT Core Add-ons](iot-core-adk-addons.md)

[IoT Core feature list](iot-core-feature-list.md)

[Command-line options to manufacture IoT Core images](command-line-options-to-manufacture-iot-core-images.md)

 

 


