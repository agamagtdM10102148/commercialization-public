---
title: LoadWeight
description: LoadWeight
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 36e3863c-0a9f-4645-aa02-3f23bf81419b
ms.mktglfcycl: deploy
ms.sitesec: msdn
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# LoadWeight


`LoadWeight` specifies a number for the load. You can increase or decrease the load for each node in the cluster relative to other nodes in the cluster. This setting will be applied only if the `EqualLoad` setting is set to **false**.

**Note**  
To enable this Network Load Balancing setting, the NetworkLoadBalancingFullServer package must be enabled in the Windows image you are installing. To do this, use Windows System Image Manager to add the Microsoft-Windows-Foundation-Package to your answer file, and then configure the NetworkLoadBalancingFullServer package to enable it. For more information about adding and configuring packages, see the [Windows Assessment and Deployment (Windows ADK) Technical Reference](http://go.microsoft.com/fwlink/?LinkId=206587).

 

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>LoadWeight</em></p></td>
<td><p>Specifies a number for the load. This number will be applied only if the <a href="microsoft-windows-networkloadbalancing-core-clusters-cluster-portrules-portrule-equalload.md" data-raw-source="[EqualLoad](microsoft-windows-networkloadbalancing-core-clusters-cluster-portrules-portrule-equalload.md)">EqualLoad</a> setting is set to <strong>false</strong>. If the <code>EqualLoad</code> setting is set to <strong>true</strong>, a default load weight of <strong>50</strong> will be applied to each node in the cluster.</p></td>
</tr>
</tbody>
</table>

 

## Valid Configuration Passes


specialize

## Parent Hierarchy


[microsoft-windows-networkloadbalancing-core-](microsoft-windows-networkloadbalancing-core.md) | [Clusters](microsoft-windows-networkloadbalancing-core-clusters.md) | [Cluster](microsoft-windows-networkloadbalancing-core-clusters-cluster.md) | [Portrules](microsoft-windows-networkloadbalancing-core-clusters-cluster-portrules.md) | [Portrule](microsoft-windows-networkloadbalancing-core-clusters-cluster-portrules-portrule.md) | **LoadWeight**

## Applies To


For list of the supported Windows editions and architectures that this component supports, see [microsoft-windows-networkloadbalancing-core-](microsoft-windows-networkloadbalancing-core.md).

## XML Example


The following example specifies that the load weight for the cluster is 100.

```
<LoadWeight>100</LoadWeight>
```

## Related topics


[Portrule](microsoft-windows-networkloadbalancing-core-clusters-cluster-portrules-portrule.md)

 

 







