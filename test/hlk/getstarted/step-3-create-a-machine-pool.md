---
title: Step 3 Create a machine pool
description: Step 3 Create a machine pool
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 0403fdec-08e1-43b9-ba50-9e176c0a9632
author: dawn.wood
ms.author: dawnwood
ms.date: 10/15/2017
ms.topic: article


---

# Step 3: Create a machine pool

A *machine pool* is a logical grouping of one or more test systems. After you install Windows HLK Client on each test system, the computers are automatically added to the default machine pool. Before you can work with a test system, you must move it to a working machine pool.

Every project needs a machine pool. A machine pool can be used for multiple projects. A project can reference multiple machine pools.

The following image shows the Studio **Configuration** page.

![hlk studio configuration page](images/hlk-studio-configuration-page.png)

## To create a machine pool


1.  In Windows HLK Studio, choose **Configuration**.

2.  To create the first new pool, right click on the $(Root) node and then choose **Create Machine Pool**.     Change the default name, if desired, and then press Enter to finish.

    Once a new pool is created, you can also right click on it and chose **Create Machine Pool**. The Archive and Default pools have special roles, so they cannot be used to create a new pool.


3.  Choose **Default Pool**, and confirm that each test system appears in the main pane on the right. If you've installed the Client on multiple test systems, you can add any of them to the pool. A computer can only be in one pool at a time.

4.  Move a test system into the new pool by first selecting it and then dragging it onto the newly-created pool.

5.  In the pane on the right, right-click the test system under the **Machines** column, choose **Change Machine Status**, and then choose **Ready**.

    The **Status** column changes to **Ready**.

    >[!WARNING]
    >- You cannot schedule a test against a computer with status equal to **NotReady**.
    >- A computer cannot be set to **Ready** while in the **Default** pool.

6.  Repeat the previous two steps for each test system that you want to include in the pool.

7.  Once you've added all of the test systems to the desired machine pool, choose the back arrow to return to the main area of Windows HLK Studio.

After all of the test systems are placed in a pool, you're ready to conduct testing against those computers.

To learn more about the different options on this page including distributed and multi-device support, see [HLK Studio - Configuration Page](../user/hlk-studio---configuration-page.md).

 

 






