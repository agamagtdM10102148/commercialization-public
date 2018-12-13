---
title: ProductInstance Members
description: ProductInstance Members
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: debffe68-d92b-4f79-bd57-05fde26c4ff7
author: dawn.wood
ms.author: dawnwood
ms.date: 10/15/2017
ms.topic: article


---

# ProductInstance Members


The following table lists the members exposed by the [ProductInstance Class](productinstance-class.md).

## <span id="Public_Properties"></span><span id="public_properties"></span><span id="PUBLIC_PROPERTIES"></span>Public Properties


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="productinstanceisvalid-property.md" data-raw-source="[IsValid](productinstanceisvalid-property.md)">IsValid</a></p></td>
<td><p>Indicates whether or not this Product Instance is valid.</p></td>
</tr>
<tr class="even">
<td><p><a href="productinstancemachinepool-property.md" data-raw-source="[MachinePool](productinstancemachinepool-property.md)">MachinePool</a></p></td>
<td><p>This property represents the machine (the test computer) that this product instance has been detected on.</p></td>
</tr>
<tr class="odd">
<td><p><a href="productinstancename-property.md" data-raw-source="[Name](productinstancename-property.md)">Name</a></p></td>
<td><p>This property represents the product name for this <strong>ProductInstance</strong> object.</p></td>
</tr>
<tr class="even">
<td><p><a href="productinstanceosplatform-property.md" data-raw-source="[OSPlatform](productinstanceosplatform-property.md)">OSPlatform</a></p></td>
<td><p>This property represents the platform (operating system plus the architecture value) for this <strong>ProductInstance</strong> object.</p></td>
</tr>
<tr class="odd">
<td><p><a href="productinstanceproject-property.md" data-raw-source="[Project](productinstanceproject-property.md)">Project</a></p></td>
<td><p>This property represents the reference to the <strong>Project</strong> object containing this product instance.</p></td>
</tr>
</tbody>
</table>

 

## <span id="Protected_Properties"></span><span id="protected_properties"></span><span id="PROTECTED_PROPERTIES"></span>Protected Properties


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>LockObject</strong></p></td>
<td><p>(Inherited from <strong>NotificationBase</strong>)</p></td>
</tr>
</tbody>
</table>

 

## <span id="Public_Methods"></span><span id="public_methods"></span><span id="PUBLIC_METHODS"></span>Public Methods


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="productinstance-addtests-method.md" data-raw-source="[AddTests](productinstance-addtests-method.md)">AddTests</a></p></td>
<td>Adds the given Tests to this Product Instance.
<div class="alert">
<strong>Warning</strong>  This functionality is being deprecated. Please use playlists to create custom test pass lists.
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p><a href="productinstancecancreatetarget-method.md" data-raw-source="[CanCreateTarget](productinstancecancreatetarget-method.md)">CanCreateTarget</a></p></td>
<td><p>This method determines if a target can be created from <strong>TargetData</strong> object provided. The target is not added to the product instance.</p></td>
</tr>
<tr class="odd">
<td><p><a href="productinstancecreatetarget-method.md" data-raw-source="[CreateTarget](productinstancecreatetarget-method.md)">CreateTarget</a></p></td>
<td>This method creates a target from <strong>TargetData</strong>, and adds it to this product instance.
<div class="alert">
<strong>Warning</strong>  This functionality is being deprecated.
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p><a href="productinstancecreatetargetfamily-method.md" data-raw-source="[CreateTargetFamily](productinstancecreatetargetfamily-method.md)">CreateTargetFamily</a></p></td>
<td><p>This method creates and adds a target family to the existing product instance, using the supplied <strong>DeviceFamily</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><a href="productinstancedeletetarget-method.md" data-raw-source="[DeleteTarget](productinstancedeletetarget-method.md)">DeleteTarget</a></p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="even">
<td><p><a href="productinstancedeletetargetfamily-method.md" data-raw-source="[DeleteTargetFamily](productinstancedeletetargetfamily-method.md)">DeleteTargetFamily</a></p></td>
<td><p>This method deletes a target family.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Equals</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p><a href="productinstancefindtargetfromcontainer-method.md" data-raw-source="[FindTargetFromContainer](productinstancefindtargetfromcontainer-method.md)">FindTargetFromContainer</a></p></td>
<td><p>This method creates a list of targets containing the specific container ID. There are two special container Ids to consider. The first is the system containerId (00000000-0000-0000-ffff-ffffffffffff). If this is passed in, then the method will return a list with just a single &quot;system&quot; target. The second is a zero-decorated GUID (00000000-0000-0000-0000-000000000000). This is an invalid GUID.</p></td>
</tr>
<tr class="odd">
<td><p><a href="productinstancefindtargetfromdevicefamily-method.md" data-raw-source="[FindTargetFromDeviceFamily](productinstancefindtargetfromdevicefamily-method.md)">FindTargetFromDeviceFamily</a></p></td>
<td><p>This method finds a list of target data that matches the family specified.</p></td>
</tr>
<tr class="even">
<td><p><a href="productinstancefindtargetfromid-method.md" data-raw-source="[FindTargetFromId](productinstancefindtargetfromid-method.md)">FindTargetFromId</a></p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="odd">
<td><p><a href="productinstancefindtargetfromsystem-method.md" data-raw-source="[FindTargetFromSystem](productinstancefindtargetfromsystem-method.md)">FindTargetFromSystem</a></p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="even">
<td><p><a href="productinstancegetfeatures-method.md" data-raw-source="[GetFeatures](productinstancegetfeatures-method.md)">GetFeatures</a></p></td>
<td><p>This method retrieves a collection of features detected for this product instance.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetHashCode</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p><a href="productinstancegetmachines-method.md" data-raw-source="[GetMachines](productinstancegetmachines-method.md)">GetMachines</a></p></td>
<td><p>This method retrieves all of the machines in a Product Instance. Machines are associated with Product Instances via their test targets. To add or remove a machine, you must add or remove the associated test target.</p></td>
</tr>
<tr class="odd">
<td><p><a href="productinstance-getplaylists-method.md" data-raw-source="[GetPlaylists](productinstance-getplaylists-method.md)">GetPlaylists</a></p></td>
<td><p>Gets the applied playlists for this <a href="productinstance-class.md" data-raw-source="[ProductInstance](productinstance-class.md)">ProductInstance</a>.</p></td>
</tr>
<tr class="even">
<td><p><a href="productinstancegetproducttypes-method.md" data-raw-source="[GetProductTypes](productinstancegetproducttypes-method.md)">GetProductTypes</a></p></td>
<td><p>This method attempts to detect product types this product instance belongs to.</p></td>
</tr>
<tr class="odd">
<td><p><a href="productinstancegettargetfamilies-method.md" data-raw-source="[GetTargetFamilies](productinstancegettargetfamilies-method.md)">GetTargetFamilies</a></p></td>
<td><p>This method retrieves an enumerable list of TargetFamilies that expose the product to the system.</p></td>
</tr>
<tr class="even">
<td><p><a href="productinstancegettargets-method.md" data-raw-source="[GetTargets](productinstancegettargets-method.md)">GetTargets</a></p></td>
<td><p>This method retrieves an enumerable list of targets that expose the product to the system.</p></td>
</tr>
<tr class="odd">
<td><p><a href="productinstancegettests-method---.md" data-raw-source="[GetTests](productinstancegettests-method---.md)">GetTests</a></p></td>
<td><p>This method retrieves all tests needed for this node.</p></td>
</tr>
<tr class="even">
<td><p><strong>GetType</strong></p></td>
<td><p>(Inherited from Object)</p></td>
</tr>
<tr class="odd">
<td><p><a href="productinstancequeuetest-method.md" data-raw-source="[QueueTest](productinstancequeuetest-method.md)">QueueTest</a></p></td>
<td><p>Overloaded.</p></td>
</tr>
<tr class="even">
<td><p><a href="productinstance-removetests-method.md" data-raw-source="[RemoveTests](productinstance-removetests-method.md)">RemoveTests</a></p></td>
<td>Removes the given Tests from the <a href="productinstance-class.md" data-raw-source="[ProductInstance](productinstance-class.md)">ProductInstance</a>.
<div class="alert">
<strong>Warning</strong>  This functionality is being deprecated. Please use playlists to create custom test pass lists.
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p><a href="productinstancesetcommonparameters-method.md" data-raw-source="[SetCommonParameters](productinstancesetcommonparameters-method.md)">SetCommonParameters</a></p></td>
<td><p>This method sets all of the parameters with a given name to the same value for all child jobs.</p></td>
</tr>
<tr class="even">
<td><p><strong>ToString</strong></p></td>
<td><p>(Inherited from Object)</p></td>
</tr>
</tbody>
</table>

 

## <span id="Protected_Methods"></span><span id="protected_methods"></span><span id="PROTECTED_METHODS"></span>Protected Methods


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Finalize</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="even">
<td><p><strong>MemberwiseClone</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
</tbody>
</table>

 

 

 






