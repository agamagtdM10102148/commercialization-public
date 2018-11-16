---
title: Ipv6Settings
description: Ipv6Settings
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 602a335f-e897-4278-b513-2d8f8c59f371
ms.mktglfcycl: deploy
ms.sitesec: msdn
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---
# Ipv6Settings

`Ipv6Settings` contains settings for the IPv6 protocol.

> [!Note]
> The settings in [Interface](microsoft-windows-tcpip-interfaces-interface.md) must be added in the following order: [Ipv6Settings](microsoft-windows-tcpip-interfaces-interface-ipv6settings.md),  [Identifier](microsoft-windows-tcpip-interfaces-interface-identifier.md), [UnicastIpAddresses](microsoft-windows-tcpip-interfaces-interface-unicastipaddresses.md), and then [Routes](microsoft-windows-tcpip-interfaces-interface-routes.md), as shown in the XML example below.

## Child Elements

| Setting                 | Description                                                                           |
|:------------------------|:--------------------------------------------------------------------------------------|
| [DhcpEnabled](microsoft-windows-tcpip-interfaces-interface-ipv6settings-dhcpenabled.md) | Specifies whether the Dynamic Host Configuration Protocol (DHCP) is enabled for the IPv6 protocol. |
| [Metric](microsoft-windows-tcpip-interfaces-interface-ipv6settings-metric.md) | Specifies the metric used to distinguish between multiple matching routes of the same prefix length. |
| [RouterDiscoveryEnabled](microsoft-windows-tcpip-interfaces-interface-ipv6settings-routerdiscoveryenabled.md) | Specifies whether the router discovery protocol—which informs hosts of the existence of routers—is enabled for the IPv6 protocol. |

## Valid Configuration Passes

specialize

windowsPE

## Parent Hierarchy

[Microsoft-Windows-TCPIP](microsoft-windows-tcpip.md) | [Interfaces](microsoft-windows-tcpip-interfaces.md) | [Interface](microsoft-windows-tcpip-interfaces-interface.md) | **Ipv6ettings**

## Applies To

For a list of the Windows editions and architectures that this component supports, see [Microsoft-Windows-TCPIP](microsoft-windows-tcpip.md).

## XML Example

The following XML output shows how to configure TCPIP.

```XML
<component name="Microsoft-Windows-TCPIP" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <Interfaces>
   <!-- Add static IP address (192.168.0.1/24, ffff:1::3/48) & route (12.34.0.0/16) to interface with identifier "Ethernet 1" -->      <Interface wcm:action="add">
         <Ipv4Settings>
            <DhcpEnabled>true</DhcpEnabled> 
            <Metric>20</Metric> 
            <RouterDiscoveryEnabled>false</RouterDiscoveryEnabled> 
         </Ipv4Settings>
         <Ipv6Settings>
            <DhcpEnabled>false</DhcpEnabled> 
            <Metric>30</Metric> 
            <RouterDiscoveryEnabled>true</RouterDiscoveryEnabled> 
         </Ipv6Settings>
      <Identifier>Ethernet 1</Identifier>
         <UnicastIpAddresses>
           <IpAddress wcm:action="add" wcm:keyValue="1">192.168.0.1/24</IpAddress>
           <IpAddress wcm:action="add" wcm:keyValue="2">ffff:1::3/48</IpAddress>
         </UnicastIpAddresses>
         <Routes>
            <Route wcm:action="add">
               <Identifier>1</Identifier> 
               <Metric>10</Metric> 
               <NextHopAddress>12.34.0.0</NextHopAddress> 
               <Prefix>16</Prefix> 
            </Route>
            <Route wcm:action="add">
               <Identifier>10</Identifier> 
               <Metric>29</Metric> 
               <NextHopAddress>12.34.56.0</NextHopAddress> 
               <Prefix>24</Prefix> 
            </Route>
         </Routes>
      </Interface>
      <Interface wcm:action="add">
         <Ipv4Settings>
            <DhcpEnabled>true</DhcpEnabled> 
            <Metric>20</Metric> 
            <RouterDiscoveryEnabled>false</RouterDiscoveryEnabled> 
         </Ipv4Settings>
         <Ipv6Settings>
            <DhcpEnabled>false</DhcpEnabled> 
            <Metric>10</Metric> 
            <RouterDiscoveryEnabled>true</RouterDiscoveryEnabled> 
         </Ipv6Settings>
         <Identifier>Local Area Connection</Identifier> 
         <UnicastIpAddresses>
            <IpAddress wcm:action="add" wcm:keyValue="1">123.45.67.8</IpAddress> 
            </UnicastIpAddresses>
         <Routes>
            <Route wcm:action="add">
               <Identifier>1</Identifier> 
               <Metric>10</Metric> 
               <NextHopAddress>12.34.0.0</NextHopAddress> 
               <Prefix>16</Prefix> 
            </Route>
         </Routes>
      </Interface>
   </Interfaces>
</component>
```

## Related topics

[Interface](microsoft-windows-tcpip-interfaces-interface.md)
