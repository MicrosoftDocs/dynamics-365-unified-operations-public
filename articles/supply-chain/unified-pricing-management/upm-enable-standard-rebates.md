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

The features described in this article are available starting in Microsoft Dynamics 365 finance and operations version 10.0.48 or later.

## First steps

Start by enabling the following features in your Microsoft Dynamics 365 finance and operations app.

Go to the Feature management workspace:

1. Enable the feature titled "Unified pricing management".
1. Enable the **Enable non-attribute based rebate management deals for Unified pricing scenario** feature.

:::image type="content" source="media/feature-management.png" alt-text="Screenshot of the feature management form with relevant pricing features." lightbox="media/feature-management.png":::

> [!NOTE]
> There's a dependency between the listed features. You can't enable the **Enable non-attribute based rebate management deals for Unified pricing scenario** feature if the **Unified pricing management** feature is disabled.
> You can't disable the **Unified pricing management** feature if the **Enable non-attribute based rebate management deals for Unified pricing scenario** feature is enabled.

## Enable non-attribute based rebate management deals

1. Go to **Modules**.
1. Select the **Rebate management** tab to see all pages related to rebate management deals.
Two new pages help you manage non-attribute based rebate deals: **Non-attribute based customer rebate deals** and **Non-attribute based customer royalty deals**.

:::image type="content" source="media/module-sidebar.png" alt-text="Rebate management module sidebar view." lightbox="media/module-sidebar.png":::

Go to the **All rebate management deals** page. On this page, you can view all rebate deals. The **Attribute-based rebate** column shows the status of each rebate deal.

:::image type="content" source="media/attribute-column.png" alt-text="Screenshot of the new column in the Rebate management form to indicate attribute-based status." lightbox="media/attribute-column.png":::

From this page, you can manage any existing rebate deals or create new rebate deals. When creating new rebate deals, use the dropdown for **Type of rebate management deal** to select attribute-based or non-attribute based rebate deal types.

:::image type="content" source="media/new-attribute-based-form.png" alt-text="Updated UI for creating new rebate management deals." lightbox="media/new-attribute-based-form.png":::

Use the **Customer rebate deals** and **Customer royalty deals** pages to view and manage attribute-based customer rebate deals or royalty deals.

:::image type="content" source="media/attribute-customer-rebate.png" alt-text="Attribute-based customer rebates." lightbox="media/attribute-customer-rebate.png":::

:::image type="content" source="media/non-attribute-customer-rebate.png" alt-text="Non-attribute based customer rebates." lightbox="media/non-attribute-customer-rebate.png":::

Use the **Non-attribute based customer rebate deals** and **Non-attribute based customer royalty deals** pages to view and manage non-attribute based customer rebate deals or royalty deals.

:::image type="content" source="media/attribute-customer-royalty.png" alt-text="Attribute-based customer royalties." lightbox="media/attribute-customer-royalty.png":::

:::image type="content" source="media/non-attribute-customer-royalty.png" alt-text="Non-attribute based customer royalties." lightbox="media/non-attribute-customer-royalty.png":::

All vendor rebate deals are non-attribute based. You can access them by using the **Vendor rebate deals** page.

:::image type="content" source="media/vendor-deals.png" alt-text="Vendor rebate deals." lightbox="media/vendor-deals.png":::

Go to **Modules**. Select **Rebate management** and expand **Periodic tasks**. You can process, post, or cancel multiple rebate management deals by using the commands in this sidebar view.

:::image type="content" source="media/periodic-tasks.png" alt-text="Periodic tasks for rebate management deals." lightbox="media/periodic-tasks.png":::

You can also view and manage all rebate management deals from the **Rebate workbench** page.

:::image type="content" source="media/rebate-workbench.png" alt-text="Rebate workbench." lightbox="media/rebate-workbench.png":::

## Troubleshooting

To get more information about errors or unexpected behavior, contact Microsoft Support and open a support ticket.
