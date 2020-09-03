---
# required metadata

title: Create transfer order from the  Warehouse app
description: This topic describes the Create and process transfer orders from the warehouse app feature 
author: perlynne
manager: tfehr
ms.date: 09/02/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSMobileDeviceQueueEvent 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2020-10-09
ms.dyn365.ops.version: 10.0.15

---

# Create transfer orders from the warehouse app

[!include [banner](../includes/banner.md)]

This feature lets warehouse workers create and process transfer orders directly from the warehouse app. The warehouse workers start by selecting the destination warehouse and can following scan one or more license plates using the app.
When the warehouse worker selects the **Complete order** a batch job will create the required transfer order and order lines based on the on-hand inventory registered for those license plates.


## Enable the create transfer orders from Warehouse app feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - Warehouse management
- **Feature name** - Create and process transfer orders from the warehouse app 

The feature is dependent on having the feature [Process warehouse app events](warehouse-app-events.md) enabled.


### Set up a mobile device menu item to create transfer orders

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
2. Select **New** to add a new menu item. Then make the following settings to get started:
    - Menu item name - Assign a name as it should appear in Supply Chain Management
    - Title - Assign a menu name as it should be presented to workers in the warehouse app.
    - Mode - Set to **Indirect** (this warehouse app will not create work)
    - Activity code - Set to **Create transfer order from license plates** to enable the warehouse workers to create a transfer order based on one or more scanned license plates.
3. Use the **Order line creation policy** setting to control how transfer order lines will be created by this menu item. The lines will get created/updated based on the on-hand inventory registered for the scanned license plates. Choose one of the following values:
    - **No reservation** - The transfer order lines will not get reserved.
    - **License plate guided with line reservation** – The transfer order lines will get reserved and use the License plate guided strategy option, which stores the relevant license plate IDs associated with the order lines. Located license plate ID values can therefore be used as part of the work creation process for the transfer order lines.
4. Use the **Outbound shipment policy** setting to add more automation to the outbound transfer order shipment process, as needed. When a worker selects the **Complete order** button, the app creates the **Complete order** warehouse app event, which will save the value you choose here in the Outbound shipment policy field for each line in the current transfer order. Later, when the event queue is processed by a batch job to create the transfer order, the value stored in this field can be read by the batch job, and may therefore control how that job processes each line. Choose one of the following:
    - **None**
    - **Release to warehouse**
    - **Ship confirm**
    - **Release and ship confirm**

You can read in detail about the automated batch job setup process in the example #####


