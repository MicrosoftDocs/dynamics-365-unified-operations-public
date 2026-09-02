---
title: DOM considerations and limitations
description: Learn about the considerations and limitations of the distributed order management (DOM) functionality in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 09/02/2026
ms.topic: how-to
ms.author: wenxyang
ms.reviewer: mirao
ms.search.region: Global
ms.search.validFrom: 2023-11-07
---

# DOM considerations and limitations

[!INCLUDE [banner](includes/banner.md)]

This article describes the considerations and limitations of the distributed order management (DOM) functionality in Microsoft Dynamics 365 Commerce.

## Advanced warehouse management compatibility

DOM works with advanced warehouse management, and its compatibility continues to improve.

- **Available inventory**: Starting with Commerce version 10.0.46, DOM includes the inventory status from the sales order line when it checks available inventory, so only inventory with a matching status is considered. For more information, see [Inventory lookup](dom-processing.md#inventory-lookup). For other advanced warehouse inventory dimensions, use the extensible method `DOMExtensionEvents.OnSettingAvailableInventory` to override available inventory from on-hand and reserved inventory. For more information, see [DOM extensibility](dom-extensibility.md).
- **Warehouse reassignment**: When advanced warehouse management creates loads, works, and shipments for a sales line, and shipments exist in the load, DOM doesn't reassign the warehouse for that line. In this case, DOM marks "Exception of type Generic was encountered" on the sales lines and the "Generic" exception type on the sales order. To reassign warehouses in this scenario, you can build customizations to either exclude these sales lines from DOM or delete the shipments before fulfillment plans are applied, such as with `DOMExtensionEvents.OnExecutingFulfillmentPlan`. Because DOM now considers inventory status when it calculates available inventory, fulfillment results are more accurate. So, this scenario is expected to arise in fewer instances.

## Other considerations

- DOM profiles can differ by sales origin and delivery mode. You can set sales order origin during order ingestion, and use different optimization strategies based on these values. DOM also supports creating custom batch jobs that take the DOM processor task as input and enable the profile to be passed as a parameter. You can then run one optimization after another to support different business scenarios.
- DOM is available only on the cloud version of Commerce. It isn't supported for on-premises deployments.

## More resources

- [DOM overview](dom.md)
- [Set up DOM](dom-set-up.md)
- [DOM rules](dom-rules.md)
- [DOM cost configuration](dom-costs.md)
- [DOM processing](dom-processing.md)
- [Results of DOM runs](dom-runs-results.md)
- [Clean up DOM fulfillment plans and logs](dom-clean-up.md)
- [DOM extensibility](dom-extensibility.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
