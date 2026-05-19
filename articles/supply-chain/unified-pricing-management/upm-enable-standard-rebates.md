---
title: Enable non-attribute based rebate management deals in Unified pricing management
description: Allow non-attribute based rebate management deals to be considered in Unified pricing management.
author: chelsiemb
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 05/01/2026
ms.custom:
- bap-template
---

# Enable non-attribute based rebate management deals in Unified pricing management

[!include [banner](../includes/banner.md)]

Use the Rebate management module to create contracts, deals, or agreements between a business and its customers or vendors, so that you can calculate rebates, deductions, and royalties. When you enable Unified pricing, you can determine rebates based on pricing attributes.

The feature described in this article enables **non-attribute based rebate management deals** to be included in Unified pricing management scenarios. When you enable this feature, the pricing evaluation process considers existing rebate agreements without requiring changes to their configuration.

This capability allows organizations to continue using existing rebate management deals while adopting Unified pricing. Customers can also create new non-attribute based rebate deals, facilitating the migration to Unified pricing for those customers who rely on the legacy behavior.

## Prerequisites

The features described in this article are available starting in Microsoft Dynamics 365 Supply Chain version 10.0.48 or later.

To enable the features, follow these steps:
1. Go to the Feature management workspace.
2. Enable the **Unified pricing management** and **Enable non-attribute based rebate management deals for Unified pricing scenario** features.

> [!NOTE]
> There's a dependency between the listed features. You can't enable the **Enable non-attribute based rebate management deals for Unified pricing scenario** feature if the **Unified pricing management** feature is disabled.
> You can't disable the **Unified pricing management** feature if the **Enable non-attribute based rebate management deals for Unified pricing scenario** feature is enabled.

## Enable non-attribute based rebate management deals

To enable non-attribute based rebate management deals, follow these steps:
1. Go to **Modules** > select **Rebate management** to see all pages related to rebate management deals.
Two new pages help you manage non-attribute based rebate deals:
    - **Non-attribute based customer rebate deals**
    - **Non-attribute based customer royalty deals**

2. Go to the **All rebate management deals** page. On this page, you can view all rebate deals. The **Attribute-based rebate** column shows the status of each rebate deal.
From this page, you can manage any existing rebate deals or create new rebate deals. When creating new rebate deals, use the dropdown for **Type of rebate management deal** to select attribute-based or non-attribute based rebate deal types.

The **Customer rebate deals** and **Customer royalty deals** pages allow you to view and manage attribute-based customer rebate deals or royalty deals.
The **Non-attribute based customer rebate deals** and **Non-attribute based customer royalty deals** pages allow you to view and manage non-attribute based customer rebate deals or royalty deals.

All vendor rebate deals are non-attribute based. You can access them by using the **Vendor rebate deals** page.

To process, post, or cancel multiple rebate management deals, follow these steps:
1. Go to **Modules** > **Rebate management**.
2. Expand **Periodic tasks**. You can process, post, or cancel multiple rebate management deals by using the commands in this sidebar view.

You can also view and manage all rebate management deals from the **Rebate workbench** page.

:::image type="content" source="media/rebate-workbench.png" alt-text="Rebate workbench." lightbox="media/rebate-workbench.png":::

## Troubleshooting

To get more information about errors or unexpected behavior, contact Microsoft Support and open a support ticket.
