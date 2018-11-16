---
title: Prefix
description: Prefix
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 1ace83c5-d399-4c82-8612-8eaa59ae9046
ms.mktglfcycl: deploy
ms.sitesec: msdn
author: themar-msft
ms.author: themar
ms.date: 05/02/2017
ms.topic: article


---

# Prefix


The `Prefix` specifies which destination IP addresses for NextHop uses the specified route.

The prefix length is specified in bits. All bits of the prefix address after the first *n* bits (where *n* is the prefix length) must be zero.

**Note**  
For the IPv6 protocol, the prefix length is **64**, with one exception. If the first 16 bits of the prefix address are zero, the prefix length can vary between **0** and **128**.

 

The settings under [Route](http://go.microsoft.com/fwlink/?LinkId=254767) must be added in the following order: [Identifier](http://go.microsoft.com/fwlink/?LinkId=224315), [Metric](http://go.microsoft.com/fwlink/?LinkId=224320), [NextHopAddress](http://go.microsoft.com/fwlink/?LinkId=224322), and then [Prefix](http://go.microsoft.com/fwlink/?LinkId=224326). After saving your Unattend file in Windows SIM, verify in the XML file that the output is shown in the correct order, as shown in the XML example below.

## Values


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><em>Prefix</em></p></td>
<td><p>Specifies the prefix for the route. <em>Prefix</em> is a string with a maximum length of 49 characters.</p></td>
</tr>
</tbody>
</table>

 

You can enter the prefix in one of the following ways:

- **As an integer.**

  The value of Prefix is the number of bits that must match in the IP address. For example, if the NextHop IP address is **12.34.0.0** and the Prefix is 16 (commonly written: **12.34.0.0/16**), then any traffic sent to a **12.34.\*.\\*** address goes through that route (subject to strong host model and routing metrics). **12.34.0.0** is the part of the address to compare against, and 16 is the number of bits that must match.

- **As a string.**

  When Prefix is set as a string, you do not need to set the [NextHopAddress](microsoft-windows-tcpip-interfaces-interface-routes-route-nexthopaddress.md) value.

This string type does not support empty elements. Do not create an empty value for this setting.

## Valid Configuration Passes


specialize

windowsPE

## Parent Hierarchy


[Microsoft-Windows-TCPIP](microsoft-windows-tcpip.md) | [Interfaces](microsoft-windows-tcpip-interfaces.md) | [Interface](microsoft-windows-tcpip-interfaces-interface.md) | [Routes](microsoft-windows-tcpip-interfaces-interface-routes.md) | [Route](microsoft-windows-tcpip-interfaces-interface-routes-route.md) | **Prefix**

## Applies To


For the list of the Windows editions and architectures that this component supports, see [Microsoft-Windows-TCPIP](microsoft-windows-tcpip.md).

## XML Example


The following XML output shows how to configure the network route TCP/IP prefix as an integer.

```
<Prefix>16</Prefix>
```

The following XML output shows how to configure an IP v4 network prefix as a string.

```
<Prefix>192.168/16</Prefix>
```

The following XML output shows how to configure the TCP/IP interfaces, including route prefixes in integer format.

```
<Interfaces>
   <Interface wcm:action="add">
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
      <Identifier>123</Identifier>
      <UnicastIpAddresses>
        <IpAddress wcm:action="add" wcm:keyValue="1">192.168.0.1/24</IpAddress>
        <IpAddress wcm:action="add" wcm:keyValue="2">ffff:1::3/48</IpAddress>
      </UnicastIpAddresses>      <Routes>
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
      <Identifier>456</Identifier>
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
```

The following XML output shows how to configure the TCP/IP interfaces, including route prefixes in string format.

```
<Interfaces>
   <Interface wcm:action="add">
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
      <Identifier>123</Identifier>
      <UnicastIpAddresses>
        <IpAddress wcm:action="add" wcm:keyValue="1">192.168.0.1/24</IpAddress>
        <IpAddress wcm:action="add" wcm:keyValue="2">ffff:1::3/48</IpAddress>
      </UnicastIpAddresses>      <Routes>
         <Route wcm:action="add">
            <Identifier>1</Identifier> 
            <Metric>10</Metric> 
            <Prefix>12.34/16</Prefix> 
         </Route>
         <Route wcm:action="add">
            <Identifier>10</Identifier> 
            <Metric>29</Metric> 
            <Prefix>12.34.56/24</Prefix> 
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
      <Identifier>456</Identifier> 
      <UnicastIpAddresses>
         <IpAddress wcm:action="add" wcm:keyValue="1">123.45.67.8</IpAddress> 
         </UnicastIpAddresses>
      <Routes>
         <Route wcm:action="add">
            <Identifier>1</Identifier> 
            <Metric>10</Metric> 
            <Prefix>12.34/16</Prefix> 
         </Route>
      </Routes>
   </Interface>
</Interfaces>
```

## Related topics


[Route](microsoft-windows-tcpip-interfaces-interface-routes-route.md)

 

 







