---
title: DOM limitations
description: This article decribes the limitations of distributed order management (DOM) functionality in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 11/15/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-11-07
---

# DOM limitations

[!include [banner](includes/banner.md)]

This article decribes the limitations of distributed order management (DOM) functionality in Microsoft Dynamics 365 Commerce.

Here are some things to consider when you use the DOM feature:

- DOM doesn't support advanced warehouse management features without customization. Customers and partners must build customizations to make DOM compatible with the advanced warehouse management capabilities and processes that are relevant to them. For more information, see [DOM extensibility](./dom-extensibility.md).

  The following known issues must be resolved to make DOM compatible with the advanced warehouse management features:

  - **The on-hand inventory** - Advanced warehousing features enable configurable dimensions (for example, inventory status) that don't provide an accurate understanding of available inventory. DOM provides an extensible method for setting available inventory for implementations that use advanced warehousing features. Customers and partners must use this extensible method to override on-hand inventory.
  - **The warehouse reassignment** - Advanced warehousing features can create loads, works, and shipments for sales lines. When shipments exist in the load of a sales line, advanced warehousing features block DOM from reassigning warehouses. Customers and partners must either exclude this type of sales lines from DOM, or delete the shipments before fulfillment plans are applied.
- DOM profiles can differ by sales origin and delivery mode. Sales order origin can be set during order ingestion, and different optimization strategies can be used based on these values. DOM also supports the creation of custom batch jobs that can take the DOM processor task as input and enable the profile to be passed as a parameter. Then one optimization can be run after another to support different business scenarios.
- DOM is only available on the cloud version of Commerce, and isn't supported in on-premises deployments.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
