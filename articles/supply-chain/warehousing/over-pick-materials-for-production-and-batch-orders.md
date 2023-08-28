---
title: Over-picking for production and batch orders
description: This article explains how to enable over-picking for production and batch orders.
author: JohanHoffmann
ms.date: 24/08/2023
ms.topic: article
ms.search.form: WHSRFMenuItem
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: gfedorova
ms.search.validFrom: 2023-08-24
ms.dyn365.ops.version: 10.0.21
---

# Over-pick materials for production and batch orders

[!include [banner](../includes/banner.md)]

This article explains how warehouse managers can configure Dynamics 365 Supply Chain Management to permit over-picking raw materials and set limits on over-picking. Over-picking occurs when a worker picks slightly more material than specified for production. By enabling the feature, workers using the Warehouse Management mobile app will be able to over-pick raw materials for production orders as needed and they will be notified if they exceed the thresholds defined by the warehouse manager. Over-picking can be relevant in situations where it is more efficient for workers to over-pick by rounding up to the nearest packing unit or in situations where it is efficient to pick the full content of nearly empty locations to free up space. 

### Turn on the feature for your system

Before you can use the feature, it must be turned on in your system. Admins can use the Feature management workspace to check the status of the feature and turn it on. In the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace, the feature is listed in the following way.

- **Module:** Warehouse Management
- **Feature name:** Over-pick materials for production orders and batch orders 

### Set up the feature in the system

Use the following procedures to configure the use of the feature.

### Enable the feature for the worker
1.	Go to **Warehouse management \> Setup \> Worker**.
1.	Select the worker for who you want to enable the feature.
1.	On the **Users** FastTab, select the warehouse on which the worker should be enabled to do over-picking.
1.	On the **Work** FastTab, set the **Allow production over picking** field to *Yes*.

### Enable over-picking on the mobile device menu item
1.	Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1.	Select a mobile device menu item that in the **Work classes** FastTab has a **work class** with a work order type *Raw material picking* associated. (In the USMF demo data set, you can use the mobile device menu item *Production pick*)
3.	On the **General** FastTab, set the **Allow over pick** field to *Yes*.


### Set an allowed threshold for over-picking
You can set a threshold that controls the extent to which a worker is permitted to exceed the quantity to be picked. The threshold is defined as a percentage of the designated quantity for the production order. You can set the threshold on the product and override the threshold for the product on bill of material lines using the product. When a production order, that uses the product in it's bill of material, is created, the threshold is copied to the production order bill of material line either from the product, or the overridden value on the bill of material line.  

### Set allowed threshold on the product
1.	Go to **Product Information management \> Products \> Released products**
1.	On the **Warehouse** FastTab, set the allow threshold for over-picking in the **Material over-picking (%)** field.

### Override the threshold on the Bill of material line
1.	Go to **Product Information management \> Bill of materials and formulas \> Bill of materials** 
1.	In the BOM column, click on one of the BOM ID’s to navigate to the details Bill of materials details page.
1.	In the details page, select one of the BOM’s
1.	In the **Bill of material lines** FastTab, select one of the BOM lines
1.	In the **Line details** FastTab, on the **Setup** tab
o	set the **Override field** to *Yes*.
o	In the **Material over-picking (%)** field, set a new threshold that overrides the threshold from the product.


### Policies for staging and over-picking

Warehouse managers can setup a policies for how material picked on license plate and non-license plate controlled locations should be allocated.

#### Policy for over-picking in license plate controlled locations
Go to **Product Information management \> Products \> Released products** 
1.	In the **Warehouse** FastTab, find the **Material picking in license plate controlled locations** field. Select one of the following values:

**Staging** : The full quanity of the scanned license plate is staged to the production input location. The original estimated quantity is allocated the production order and the remaining quanity on the license plate is un-allocated on the production input location. Using this policy, the over-picking option is not available in the workflow for raw material picking on the warehouse managment mobile app.
**Order-picking** : The full quantity that is being picked is allocated to the production order.

#### Policy for over-picking in non-license plate controlled locations

Go to **Product Information management \> Products \> Released products** 
1.	In the **Warehouse** FastTab, find the **Material picking in non-license plate controlled locations** field. Select one of the following values:

**Staging** : The original estimated quantity is allocated the production order and the remaining quanity is un-allocated on the production input location.
**Order-picking** : The full quantity that is being picked is allocated to the production order.

