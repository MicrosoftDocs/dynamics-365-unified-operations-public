---
title: The unit and unit quantity aren't working correctly in the inventory journal
description: The unit and unit quantity aren't working correctly in the inventory journal
author: sherry-zheng
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: chuzheng
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.16
---


# The unit and unit quantity aren't working correctly in the inventory journal

## Symptoms

You might encounter one or both of the following issues when you work with units and quantities in an inventory journal:

- You don't see units or unit quantities in the inventory journal while a unit of conversion is set up for the released product, and you can't change the unit in the inventory journal.
- You see the **Quantity** and **Unit** fields in the inventory journal, but you don't see the **Unit quantity** field. If you change the unit, enter a quantity, and post the journal, the journal still shows the original unit of measurement for that quantity.

## Resolution

To fix this issue, follow these steps.

1. In the **Feature management** workspace, make sure that the *Using unit of measure and unit quantity in inventory journals* feature is turned on. This feature adds the **Unit** and **Unit quantity** fields to the journal. (As of Supply Chain Management version 10.0.21, this feature is turned on by default.)
1. After the feature is turned on, use the **Quantity**, **Unit quantity**, and **Unit** fields in the following way:

    - **Quantity** – Specify the quantity by using the default unit that is defined for the released product. However, the default unit itself isn't shown here. If a conversion is set up between the default unit and the unit that is selected in the **Unit** field, the **Quantity** field is automatically updated, based on the selections in the **Unit quantity** and **Unit** fields.
    - **Unit quantity** – Specify the quantity by using the unit that is selected in the **Unit** field.
    - **Unit** – Select the unit to apply to the value in the **Unit quantity** field.
