---
title: Sample Report Descriptors
description: This topic presents a sample report descriptor and sample descriptor excerpts for a Windows Precision Touchpad device.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 92DF6D05-E6CC-4D7C-9CA4-0409A16B9F03
ms.author: eliotgra
ms.date: 05/02/2017
ms.topic: article


---

# Sample Report Descriptors


This topic presents a sample report descriptor and sample descriptor excerpts for a Windows Precision Touchpad device.

## Sample Report Descriptor


All the values and parameters specified in the following sample descriptor are mandatory.

```
//TOUCH PAD input TLC
    0x05, 0x0d,                         // USAGE_PAGE (Digitizers)          
    0x09, 0x05,                         // USAGE (Touch Pad)             
    0xa1, 0x01,                         // COLLECTION (Application)         
    0x85, REPORTID_TOUCHPAD,            //   REPORT_ID (Touch pad)              
    0x09, 0x22,                         //   USAGE (Finger)                 
    0xa1, 0x02,                         //   COLLECTION (Logical)  
    0x15, 0x00,                         //       LOGICAL_MINIMUM (0)
    0x25, 0x01,                         //       LOGICAL_MAXIMUM (1)
    0x09, 0x47,                         //       USAGE (Confidence) 
    0x09, 0x42,                         //       USAGE (Tip switch)
    0x95, 0x02,                         //       REPORT_COUNT (2)
    0x75, 0x01,                         //       REPORT_SIZE (1)
    0x81, 0x02,                         //       INPUT (Data,Var,Abs)
    0x95, 0x01,                         //       REPORT_COUNT (1)
    0x75, 0x02,                         //       REPORT_SIZE (2)
    0x25, 0x02,                         //       LOGICAL_MAXIMUM (2)
    0x09, 0x51,                         //       USAGE (Contact Identifier)
    0x81, 0x02,                         //       INPUT (Data,Var,Abs)
    0x75, 0x01,                         //       REPORT_SIZE (1)
    0x95, 0x04,                         //       REPORT_COUNT (4)             
    0x81, 0x03,                         //       INPUT (Cnst,Var,Abs)
    0x05, 0x01,                         //       USAGE_PAGE (Generic Desk..
    0x15, 0x00,                         //       LOGICAL_MINIMUM (0)
    0x26, 0xff, 0x0f,                   //       LOGICAL_MAXIMUM (4095)         
    0x75, 0x10,                         //       REPORT_SIZE (16)             
    0x55, 0x0e,                         //       UNIT_EXPONENT (-2)           
    0x65, 0x13,                         //       UNIT(Inch,EngLinear)                  
    0x09, 0x30,                         //       USAGE (X)                    
    0x35, 0x00,                         //       PHYSICAL_MINIMUM (0)         
    0x46, 0x90, 0x01,                   //       PHYSICAL_MAXIMUM (400)
    0x95, 0x01,                         //       REPORT_COUNT (1)         
    0x81, 0x02,                         //       INPUT (Data,Var,Abs)         
    0x46, 0x13, 0x01,                   //       PHYSICAL_MAXIMUM (275)
    0x09, 0x31,                         //       USAGE (Y)                    
    0x81, 0x02,                         //       INPUT (Data,Var,Abs)    
    0xc0,                               //    END_COLLECTION
    0x55, 0x0C,                         //    UNIT_EXPONENT (-4)           
    0x66, 0x01, 0x10,                   //    UNIT (Seconds)        
    0x47, 0xff, 0xff, 0x00, 0x00,      //     PHYSICAL_MAXIMUM (65535)
    0x27, 0xff, 0xff, 0x00, 0x00,         //  LOGICAL_MAXIMUM (65535) 
    0x75, 0x10,                           //  REPORT_SIZE (16)             
    0x95, 0x01,                           //  REPORT_COUNT (1) 
    0x05, 0x0d,                         //    USAGE_PAGE (Digitizers)
    0x09, 0x56,                         //    USAGE (Scan Time)    
    0x81, 0x02,                           //  INPUT (Data,Var,Abs)         
    0x09, 0x54,                         //    USAGE (Contact count)
    0x25, 0x7f,                           //  LOGICAL_MAXIMUM (127) 
    0x95, 0x01,                         //    REPORT_COUNT (1)
    0x75, 0x08,                         //    REPORT_SIZE (8)    
    0x81, 0x02,                         //    INPUT (Data,Var,Abs)
    0x05, 0x09,                         //    USAGE_PAGE (Button)         
    0x09, 0x01,                         //    USAGE_(Button 1)     
    0x09, 0x02,                         //    USAGE_(Button 2)     

    0x09, 0x03,                         //    USAGE_(Button 3)     
    0x25, 0x01,                         //    LOGICAL_MAXIMUM (1)          
    0x75, 0x01,                         //    REPORT_SIZE (1)              
    0x95, 0x01,                         //    REPORT_COUNT (1)             
    0x81, 0x02,                         //    INPUT (Data,Var,Abs)
    0x95, 0x07,                          //   REPORT_COUNT (7)                 
    0x81, 0x03,                         //    INPUT (Cnst,Var,Abs)
    0x05, 0x0d,                         //    USAGE_PAGE (Digitizer)
    0x85, REPORTID_MAX_COUNT,            //   REPORT_ID (Feature)              
    0x09, 0x55,                         //    USAGE (Contact Count Maximum)
    0x09, 0x59,                         //    USAGE (Pad TYpe)
    0x75, 0x04,                         //    REPORT_SIZE (4) 
    0x95, 0x02,                         //    REPORT_COUNT (2)
    0x25, 0x0f,                         //    LOGICAL_MAXIMUM (15)
    0xb1, 0x02,                         //    FEATURE (Data,Var,Abs)
    0x06, 0x00, 0xff,                   //    USAGE_PAGE (Vendor Defined)
    0x85, REPORTID_PTPHQA,               //    REPORT_ID (PTPHQA)  
    0x09, 0xC5,                         //    USAGE (Vendor Usage 0xC5)    
    0x15, 0x00,                         //    LOGICAL_MINIMUM (0)          
    0x26, 0xff, 0x00,                   //    LOGICAL_MAXIMUM (0xff) 
    0x75, 0x08,                         //    REPORT_SIZE (8)             
    0x96, 0x00, 0x01,                   //    REPORT_COUNT (0x100 (256))             
    0xb1, 0x02,                         //    FEATURE (Data,Var,Abs)
    0xc0,                               // END_COLLECTION
    //CONFIG TLC
    0x05, 0x0d,                         //    USAGE_PAGE (Digitizer)
    0x09, 0x0E,                         //    USAGE (Configuration)
    0xa1, 0x01,                         //   COLLECTION (Application)
    0x85, REPORTID_FEATURE,             //   REPORT_ID (Feature)              
    0x09, 0x22,                         //   USAGE (Finger)              
    0xa1, 0x02,                         //   COLLECTION (logical)     
    0x09, 0x52,                         //    USAGE (Input Mode)         
    0x15, 0x00,                         //    LOGICAL_MINIMUM (0)      
    0x25, 0x0a,                         //    LOGICAL_MAXIMUM (10)
    0x75, 0x08,                         //    REPORT_SIZE (8)         
    0x95, 0x01,                         //    REPORT_COUNT (1)         
    0xb1, 0x02,                         //    FEATURE (Data,Var,Abs    
    0xc0,                               //   END_COLLECTION
    0x09, 0x22,                         //   USAGE (Finger)              
    0xa1, 0x00,                         //   COLLECTION (physical)     
    0x85, REPORTID_FUNCTION_SWITCH,     //     REPORT_ID (Feature)              
    0x09, 0x57,                         //     USAGE(Surface switch)
    0x09, 0x58,                         //     USAGE(Button switch)
    0x75, 0x01,                         //     REPORT_SIZE (1)
    0x95, 0x02,                         //     REPORT_COUNT (2)
    0x25, 0x01,                         //     LOGICAL_MAXIMUM (1)
    0xb1, 0x02,                         //     FEATURE (Data,Var,Abs)
    0x95, 0x06,                         //     REPORT_COUNT (6)             
    0xb1, 0x03,                         //     FEATURE (Cnst,Var,Abs)
    0xc0,                               //   END_COLLECTION
    0xc0,                               // END_COLLECTION
    //MOUSE TLC
    0x05, 0x01,                         // USAGE_PAGE (Generic Desktop)     
    0x09, 0x02,                         // USAGE (Mouse)                    
    0xa1, 0x01,                         // COLLECTION (Application)        
    0x85, REPORTID_MOUSE,               //   REPORT_ID (Mouse)              
    0x09, 0x01,                         //   USAGE (Pointer)                
    0xa1, 0x00,                         //   COLLECTION (Physical)          
    0x05, 0x09,                         //     USAGE_PAGE (Button)          
    0x19, 0x01,                         //     USAGE_MINIMUM (Button 1)     
    0x29, 0x02,                         //     USAGE_MAXIMUM (Button 2)     
    0x25, 0x01,                         //     LOGICAL_MAXIMUM (1)          
    0x75, 0x01,                         //     REPORT_SIZE (1)              
    0x95, 0x02,                         //     REPORT_COUNT (2)             
    0x81, 0x02,                         //     INPUT (Data,Var,Abs)         
    0x95, 0x06,                         //     REPORT_COUNT (6)             
    0x81, 0x03,                         //     INPUT (Cnst,Var,Abs)         
    0x05, 0x01,                         //     USAGE_PAGE (Generic Desktop) 
    0x09, 0x30,                         //     USAGE (X)                    
    0x09, 0x31,                         //     USAGE (Y)                    
    0x75, 0x10,                         //     REPORT_SIZE (16)             
    0x95, 0x02,                         //     REPORT_COUNT (2)             
    0x25, 0x0a,                          //    LOGICAL_MAXIMUM (10)      
    0x81, 0x06,                         //     INPUT (Data,Var,Rel)         
    0xc0,                               //   END_COLLECTION                 
    0xc0,                                //END_COLLECTION
```

## Sample Report Descriptor Excerpt - (Latency Mode Feature Report)


The following excerpt is from the descriptor for the Windows Precision Touchpad top-level collection. This descriptor excerpt is for the optional (but highly recommended) support of the latency mode feature report.

```
    0x05, 0x0d,                         //    USAGE_PAGE (Digitizer)
    0x85, REPORTID_LATENCY,             //    REPORT_ID (Latency)              
    0x09, 0x60,                         //    USAGE(Latency Mode)
    0x75, 0x01,                         //    REPORT_SIZE (1) 
    0x95, 0x01,                         //    REPORT_COUNT (1)
    0x15, 0x00,                         //    LOGICAL_MINIMUM (0)
    0x25, 0x01,                         //    LOGICAL_MAXIMUM (1)
    0xb1, 0x02,                         //    FEATURE (Data,Var,Abs)
    0x95, 0x07,                         //    REPORT_COUNT (7)             
    0xb1, 0x03,                         //    FEATURE (Cnst,Var,Abs)            
```

## Sample Report Descriptor Excerpt - (Segmented Device Certification Status Feature Report)


The following excerpt is from the descriptor for the Windows Precision Touchpad top-level collection, for a segmented version of the device certification status feature report. This allows the certification status blob to be split into eight 32-byte segments, versus a single 256-byte segment. The host indicates which segment \# it would like returned in a SET FEATURE. In response, the device returns the segment \#, along with the associated segment in GET FEATURE.

```
    0x06, 0x00, 0xff,                   //     USAGE_PAGE (Vendor Defined)  
    0x85, REPORTID_PTPHQA,              //     REPORT_ID (PTPHQA)              
    0x09, 0xC6,                         //     USAGE (Vendor usage for segment #) 
    0x25, 0x08,                         //     LOGICAL_MAXIMUM (8)
    0x75, 0x08,                         //     REPORT_SIZE (8)
    0x95, 0x01,                         //     REPORT_COUNT (1) 
    0xb1, 0x02,                         //     FEATURE (Data,Var,Abs) 
    0x09, 0xC7,                         //     USAGE (Vendor Usage) 
    0x26, 0xff, 0x00,                   //     LOGICAL_MAXIMUM (0xff)                 
    0x95, 0x20,                         //     REPORT_COUNT (32)             
    0xb1, 0x02,                         //     FEATURE (Data,Var,Abs)
```

## Related topics


[Configuration Collection](touchpad-configuration-collection.md)

[Mouse Collection](touchpad-mouse-collection.md)

[Windows Precision Touchpad Collection](touchpad-windows-precision-touchpad-collection.md)

 

 







