---
title: Display seamless sync information on custom forms in Dynamics 365 Sales
description: Learn how to modify custom forms in Dynamics 365 Sales to display seamless sync information
author: henrikan
ms.author: Henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/30/2024
ms.custom: 
  - bap-template
---

# Display seamless sync information on custom forms in Dynamics 365 Sales

[!include [banner](../includes/banner.md)]

With [seamless sync](../../../fin-ops/data-entities/add-efficiency-in-quote-to-cash-seamless-sync.md), users who work on sales orders and sales quotations in Sales can view the results of calculations that the Supply Chain Management pricing engine does, without having to take any extra steps to get prices, discounts, and totals. As the users work in Sales, all the necessary data and calculation results are seamlessly synced between systems as required.

When you [enable seamless sync in Supply Chain Management](../../../fin-ops/data-entities/add-efficiency-in-quote-to-cash-seamless-sync.md), the system automatically makes the required customizations that make it possible to see seamless sync information on the standard Order, Quote, Order Product and Quote Products forms in Dynamics 365 Sales. However, if your company uses custom versions of these forms (which is common), then you must modify your custom forms to enable seamless sync information to display correctly on your forms. This article describes how.

## Add seamless sync information to custom Order or Quote forms

To Add seamless sync information to custom Order or Quote forms in Dynamics 365 Sales, follow these steps.

1. Open the [Power Apps Maker portal](https://make.powerapps.com).
1. Open your custom *Order* or *Quote* form.
1. Select **Form Libraries** and make sure that the library named `msdyn_d365scm` is present. If it isn't, select **Add library** and add it.

    ![](media/image1.png)

1. Open the *On Load* event for the custom form and add the handler function `D365AutoSyncController.activateAutoSync`.

    ![A screenshot of a computer program Description automatically generated](media/image2.png)

1. If the grid on your custom form is editable, open the *On Save* event for the grid and add the handler function `D365AutoSyncController.onSaveDetailsGrid`.

    ![A screenshot of a computer Description automatically generated](media/image3.png)

## Add seamless sync information to custom Order Product or Quote Product forms

To Add seamless sync information to custom Order Product or Quote Product forms in Dynamics 365 Sales, follow these steps.

1. Open the [Power Apps Maker portal](https://make.powerapps.com).
1. Open your custom *Order Product* or *Quote Product* form.
1. Select **Form Libraries** and make sure that the library named `msdyn_d365scm` is present. If it isn't, select **Add library** and add it.
1. Open the *On Load* event for the custom form and add the handler function `D365AutoSyncController.activateAutoSync`.

<!--KFM: This procedure is exactly like the other one. Why not combine them? -->