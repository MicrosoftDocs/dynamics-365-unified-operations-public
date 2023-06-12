---
# required metadata

title: Manage warehouse workers
description: This article describes how you can use the Warehouse Management mobile app to help control and monitor the work that's carried out by employees in your warehouses.
author: perlynne
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmWorker, InventLocation, WHSLaborStandards, WHSWorker, WHSWorkTable, WHSWorkTableListPage, WHSResetUserPassword
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: feaa6f15-49d2-41f5-9b87-453463c52e4e
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Manage warehouse workers

[!include [banner](../includes/banner.md)]

This article describes how you can use the Warehouse Management mobile app to help control and monitor the work that's carried out by employees in your warehouses.

If you're using the functionality in Warehouse management, all warehouse worker operations are referred to as *work*. Work such as picking, moving, and counting on-hand inventory is recorded by using mobile devices. Before a warehouse worker can perform work, they must be associated with a worker in Human resources. Each **Worker** account can have multiple warehouse work users associated with it. Those work users can work in different warehouses and can have different levels of access to the various mobile device menus. You can think of the warehouse work users as multiple logons for the selected worker. Each work user has a default warehouse, and specific workflows are exposed by the menus items that are available to that work user. 

To create a new work user, on the **Workers** page, on the **General** tab, in the **Warehouses** section, click **Worker**. You must specify a user ID, a user name, a default warehouse, and a menu name. This menu is loaded when the user signs in to the Warehouse Mobile Device Portal, and lets you define which menu items the user has access to. 

As part of the setup for each work user, you can also define specific process workflows. For example, you can use the **Is a cycle count supervisor** field to specify whether the user can process adjustments to cycle counting discrepancies during a counting operation, or whether these adjustments must first be reviewed by another person.

## Defining labor standards
The **Labor standards** page lets you define the calculation methods that the system uses to calculate the estimated time that a particular type of work should require. This definition can be set on a generic level or on a specific level. For example, you can define the time that should be required in order to process a sales order pick per weight for a specific unit definition when a specific picking process is used. At the same time, you can record the time, based on another calculation method, for the put operation of the on-hand inventory that is picked. 

To enable the labor standards that you've defined, you must select the **Allow labor standards** option for each warehouse where labor standards will be used.

## Monitoring and controlling warehouse work
The **All work** page lets you monitor and maintain all work that is planned, in progress, and completed. From this page, you can update various processes, such as warehouse work user assignments and work priority. You can also drill down into the details that are related to the work header and work lines to gain an understanding of the expected or completed work processes. 

If you enable the **Labor standards** option, you can see the calculated estimated time for the work. Then, when the work is processed, the actual time will also be shown for each work operation. In this way, you can compare the estimated time calculations to the actual time. 

Additionally, you can use the estimated time in the rules for automatically splitting work during work creation. In this way, you can load balance work, based on the expected time to complete the tasks. 

Analysis of the time that is used to process work items can help drive improvements in the warehouse workers’ efficiency. The following reports are available to help with this analysis:

-   **Labor by user** – This report shows worker productivity, based on actual times against expected times.
-   **Labor by work transaction type** – You can use this report to investigate inefficiencies in specific warehouse processes. For example, you notice that picks for transfer orders are taking longer this week than in previous weeks. You can then use this information for further investigation.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]