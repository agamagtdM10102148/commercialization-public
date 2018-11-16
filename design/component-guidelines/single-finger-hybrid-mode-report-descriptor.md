---
title: Single Finger Hybrid Mode Report Descriptor
description: Single Finger Hybrid Mode Report Descriptor
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 976B0C02-C663-42C0-81C4-BD9B9E191EF2
ms.author: eliotgra
ms.date: 05/02/2017
ms.topic: article


---

# Single Finger Hybrid Mode Report Descriptor


The Single Finger Hybrid Mode Multi-touch Devices sample report descriptor contains a single logical collection. For many categories of devices, end users may operate with a single finger in most scenarios. For this type of device, this mode is the most optimal.

**Note**  HID I2C multi-touch devices are required to follow this mode.

 

```
0x05, 0x0d,                         // USAGE_PAGE (Digitizers)          
    0x09, 0x04,                         // USAGE (Touch Screen)             
    0xa1, 0x01,                         // COLLECTION (Application)         
    0x85, 0x01,                         //   REPORT_ID (Touch)              
    0x09, 0x22,                         //   USAGE (Finger)                 
    0xa1, 0x02,                         //     COLLECTION (Logical)  
    0x09, 0x42,                         //       USAGE (Tip Switch)           
    0x15, 0x00,                         //       LOGICAL_MINIMUM (0)          
    0x25, 0x01,                         //       LOGICAL_MAXIMUM (1)          
    0x75, 0x01,                         //       REPORT_SIZE (1)              
    0x95, 0x01,                         //       REPORT_COUNT (1)             
    0x81, 0x02,                         //       INPUT (Data,Var,Abs) 
    0x95, 0x07,                         //       REPORT_COUNT (7)  
    0x81, 0x03,                         //       INPUT (Cnst,Ary,Abs)
    0x75, 0x08,                         //       REPORT_SIZE (8)
    0x09, 0x51,                         //       USAGE (Contact Identifier)
    0x95, 0x01,                         //       REPORT_COUNT (1)             
    0x81, 0x02,                         //       INPUT (Data,Var,Abs) 
    0x05, 0x01,                         //       USAGE_PAGE (Generic Desk..
    0x26, 0xff, 0x0f,                   //       LOGICAL_MAXIMUM (4095)         
    0x75, 0x10,                         //       REPORT_SIZE (16)             
    0x55, 0x0e,                         //       UNIT_EXPONENT (-2)           
    0x65, 0x13,                         //       UNIT(Inch,EngLinear)                  
    0x09, 0x30,                         //       USAGE (X)                    
    0x35, 0x00,                         //       PHYSICAL_MINIMUM (0)         
    0x46, 0xb5, 0x04,                   //       PHYSICAL_MAXIMUM (1205)
    0x95, 0x02,                         //       REPORT_COUNT (2)         
    0x81, 0x02,                         //       INPUT (Data,Var,Abs)         
    0x46, 0x8a, 0x03,                   //       PHYSICAL_MAXIMUM (906)
    0x09, 0x31,                         //       USAGE (Y)                    
    0x81, 0x02,                         //       INPUT (Data,Var,Abs)
    0x05, 0x0d,                         //       USAGE_PAGE (Digitizers)
    0x09, 0x48,                         //       USAGE (Width)                
    0x09, 0x49,                         //       USAGE (Height)               
    0x81, 0x02,                         //       INPUT (Data,Var,Abs)
    0x95, 0x01,                         //       REPORT_COUNT (1)
    0x55, 0x0C,                         //       UNIT_EXPONENT (-4)           
    0x65, 0x12,                         //       UNIT (Radians,SIROtation)        
    0x35, 0x00,                         //       PHYSICAL_MINIMUM (0)         
    0x47, 0x6f, 0xf5, 0x00, 0x00,       //       PHYSICAL_MAXIMUM (62831)      
    0x15, 0x00,                         //       LOGICAL_MINIMUM (0)      
    0x27, 0x6f, 0xf5, 0x00, 0x00,       //       LOGICAL_MAXIMUM (62831)        
    0x09, 0x3f,                         //       USAGE (Azimuth[Orientation]) 
    0x81, 0x02,                         //       INPUT (Data,Var,Abs)  
    0xc0,                               //     END_COLLECTION
    0x05, 0x0d,                         //   USAGE_PAGE (Digitizers)
    0x55, 0x0C,                         //   UNIT_EXPONENT (-4)           
    0x66, 0x01, 0x10,                   //   UNIT (Seconds)        
    0x47, 0xff, 0xff, 0x00, 0x00,       //   PHYSICAL_MAXIMUM (65535)
    0x27, 0xff, 0xff, 0x00, 0x00,       //   LOGICAL_MAXIMUM (65535) 
    0x75, 0x10,                         //   REPORT_SIZE (16)             
    0x95, 0x01,                         //   REPORT_COUNT (1) 
    0x09, 0x56,                         //   USAGE (Scan Time)
    0x81, 0x02,                         //   INPUT (Data,Var,Abs)         
    0x09, 0x54,                         //   USAGE (Contact count)
    0x25, 0x7f,                         //   LOGICAL_MAXIMUM (127) 
    0x95, 0x01,                         //   REPORT_COUNT (1)
    0x75, 0x08,                         //   REPORT_SIZE (8)    
    0x81, 0x02,                         //   INPUT (Data,Var,Abs)
    0x85, REPORTID_MAX_COUNT,           //   REPORT_ID (Feature)              
    0x09, 0x55,                         //   USAGE(Contact Count Maximum)
    0x95, 0x01,                         //   REPORT_COUNT (1)
    0x25, 0x02,                         //   LOGICAL_MAXIMUM (2)
    0xb1, 0x02,                         //   FEATURE (Data,Var,Abs)
    0x85, 0x44,                         //   REPORT_ID (Feature)
    0x06, 0x00, 0xff,                   //   USAGE_PAGE (Vendor Defined)  
    0x09, 0xC5,                         //   USAGE (Vendor Usage 0xC5)    
    0x15, 0x00,                         //   LOGICAL_MINIMUM (0)          
    0x26, 0xff, 0x00,                   //   LOGICAL_MAXIMUM (0xff) 
    0x75, 0x08,                         //   REPORT_SIZE (8)             
    0x96, 0x00, 0x01,                   //   REPORT_COUNT (0x100 (256))             
    0xb1, 0x02,                         //   FEATURE (Data,Var,Abs) 
    0xc0,                               // END_COLLECTION
```

**Note**  the REPORTID\_MAX\_COUNT and REPORTID\_MOUSE referenced in the above descriptors don’t signify any particular value. Report identifiers are optional and should be assigned according to the needs of every report descriptor. Please see the [Device Class Definition for Human Interface Devices (HID) Version 1.11](http://www.usb.org/developers/hidpage/HID1_11.pdf) document for more information about report identifiers.

 

The following example shows 2 frames of 5 reports each for single-finger hybrid device representing 5 counts.

| X    | Y   | Tip  | Scan Time | Contact ID | Contact Count |
|------|-----|------|-----------|------------|---------------|
| 517  | 350 | TRUE | 3472      | 0          | 5             |
| 706  | 217 | TRUE | 3472      | 1          | 0             |
| 510  | 640 | TRUE | 3472      | 2          | 0             |
| 1113 | 317 | TRUE | 3472      | 3          | 0             |
| 866  | 218 | TRUE | 3472      | 4          | 0             |
| 517  | 350 | TRUE | 3561      | 0          | 5             |
| 706  | 217 | TRUE | 3561      | 1          | 0             |
| 510  | 640 | TRUE | 3561      | 2          | 0             |
| 1113 | 317 | TRUE | 3561      | 3          | 0             |
| 866  | 218 | TRUE | 3561      | 4          | 0             |

 

 

 






