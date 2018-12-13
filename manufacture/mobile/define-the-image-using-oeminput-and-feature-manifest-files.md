---
title: Define the image using OEMInput and feature manifest files
description: Learn how to create an OEMInput and feature manifest files to fully define the contents of your mobile image.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: A3E05C3B-450D-4AFD-8368-241EAB7F8036
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# Define the image using OEMInput and feature manifest files


Learn how to create an OEMInput and feature manifest files to fully define the contents of your mobile image.

## In this section


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Topic</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="oeminput-file-contents.md">OEMInput file contents</a></p></td>
<td><p>An OEMInput.xml file contains the required and optional elements used to define a mobile image. The OS uses this file to determine the applications processor, build type, UI languages, default region format, resolution, and other properties to include in the image that will be generated.</p>
<p>This topic provides a full listing of the XML schema for the file.</p></td>
</tr>
<tr class="even">
<td><p><a href="optional-features-for-building-images.md">Optional features for building mobile images</a></p></td>
<td><p>You can add optional features to images by including them under the <strong>Features</strong> element in the OEMInput XML file.</p></td>
</tr>
<tr class="odd">
<td><p><a href="feature-manifest-file-contents.md">Feature manifest file contents</a></p></td>
<td><p><em>Feature manifest (FM) files</em> are used to define specific types of image builds that contain different sets of optional packages. This topic describes the required and optional elements in a FM file.</p></td>
</tr>
<tr class="even">
<td><p><a href="create-a-feature-and-include-it-in-an-image.md">Create a feature and include it in an image</a></p></td>
<td><p>This topic shows you how to create a feature and add it to an image.</p></td>
</tr>
<tr class="odd">
<td><p><a href="adding-a-driver-to-a-test-image.md">Adding a driver to a test image</a></p></td>
<td><p>This topic shows you how to create a feature and add it to a test image.</p></td>
</tr>
<tr class="even">
<td><p><a href="feature-groupings-and-constraints.md">Feature groupings and constraints</a></p></td>
<td><p>Feature groups and feature constraints allow additional logic to be added to the build system to support intelligent processing of the OEMInput XML.</p></td>
</tr>
<tr class="odd">
<td><p><a href="set-device-platform-information.md">Set device platform information</a></p></td>
<td><p>Learn about the prerequisites for building an image that can be flashed to a mobile device, including additional device platform information such as partner names, version numbers, and device names, before the image is finalized for retail devices.</p></td>
</tr>
</tbody>
</table>

 

## Related topics


[Building and flashing mobile images](building-and-flashing-images.md)

 

 







