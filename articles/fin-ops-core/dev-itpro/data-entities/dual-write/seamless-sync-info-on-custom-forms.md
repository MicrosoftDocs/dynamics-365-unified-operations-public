---
title: Display seamless sync information on custom forms in Dynamics 365 Sales (preview)
description: Learn how to modify custom forms in Dynamics 365 Sales to display seamless sync information
author: adpattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/01/2024
ms.custom: 
  - bap-template
---

# Display seamless sync information on custom forms in Dynamics 365 Sales (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.42 GA -->

With [seamless sync](../../../fin-ops/data-entities/add-efficiency-in-quote-to-cash-seamless-sync.md), users who work on sales orders and sales quotations in Dynamics 365 Sales can view the results of calculations that the Supply Chain Management pricing engine does, without having to take any extra steps to get prices, discounts, and totals. As users work in Sales, all the necessary data and calculation results are seamlessly synced between systems as required.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

When you install the supply chain solution for Dynamics 365 Sales, it makes several modifications to the standard forms in Sales, including modifications that add seamless sync information to the standard Order, Quote, Order Product, and Quote Products forms in Sales. However, if your company uses custom forms for one or more of these entities (which is common), then you must modify your custom forms to enable seamless sync information to display correctly on them. This article describes how.

## Add seamless sync information to custom Order or Quote forms

To add seamless sync information to custom Order or Quote forms in Sales, follow these steps.

1. Open the [Power Apps Maker portal](https://make.powerapps.com).
1. Open your custom *Order* or *Quote* form.
1. Select **Form libraries** and make sure that the library named `msdyn_d365scm` is present. If it isn't, select **Add library** and add it.

    :::image type="content" source="../media/custom-form-libraries.png" alt-text="The Form libraries dialog" lightbox="../media/custom-form-libraries.png":::

1. Open the *On Load* event for the custom form and add the handler function `D365AutoSyncController.activateAutoSync`.

    :::image type="content" source="../media/custom-form-event-function.png" alt-text="The Configure event dialog" lightbox="../media/custom-form-event-function.png":::

1. If the grid on your custom form is editable, open the *On Save* event for the grid and add the handler function `D365AutoSyncController.onSaveDetailsGrid`.

You can learn more about how to work with libraries and events for custom forms in [Configure model-driven app form event handlers](/power-apps/maker/model-driven-apps/configure-event-handlers-legacy).

## Add seamless sync information to custom Order Product or Quote Product forms

To add seamless sync information to custom Order Product or Quote Product forms in Sales, follow these steps.

1. Open the [Power Apps Maker portal](https://make.powerapps.com).
1. Open your custom *Order Product* or *Quote Product* form.
1. Select **Form libraries** and make sure that the library named `msdyn_d365scm` is present. If it isn't, select **Add library** and add it.
1. Open the *On Load* event for the custom form and add the handler function `D365AutoSyncController.activateAutoSync`.
