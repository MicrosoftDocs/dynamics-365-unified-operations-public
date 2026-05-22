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

Starting in Microsoft Dynamics 365 Supply Chain version 10.0.48, the **Non-attribute based rebate management deals** feature can be included in Unified pricing management scenarios. When you enable this feature, the pricing evaluation process considers existing rebate agreements without requiring changes to their configuration.

This capability allows organizations to continue using existing rebate management deals while adopting Unified pricing. Customers can also create new non-attribute based rebate deals, facilitating the migration to Unified pricing for those customers who rely on the legacy behavior.

## Prerequisites

To enable the features, follow these steps:

1. Go to the Feature management workspace.
1. Enable the **Unified pricing management** and **Enable non-attribute based rebate management deals for Unified pricing scenario** features.

> [!NOTE]
> There's a dependency between the listed features. You can't enable the **Enable non-attribute based rebate management deals for Unified pricing scenario** feature if the **Unified pricing management** feature is disabled.
> You can't disable the **Unified pricing management** feature if the **Enable non-attribute based rebate management deals for Unified pricing scenario** feature is enabled.

## Enable non-attribute based rebate management deals

1. Go to **Rebate management** to see all pages related to rebate management deals.
Two new pages manage non-attribute based rebate deals:
    - **Non-attribute based customer rebate deals**
    - **Non-attribute based customer royalty deals**

1. Go to the **All rebate management deals** page. On this page, you can view all rebate deals. The **Attribute-based rebate** column shows the status of each rebate deal.
From this page, you can manage any existing rebate deals or create new rebate deals.
1. To create new rebate deals, in the **Type of rebate management deal** field, select attribute or non-attribute rebate deal types.

To view and manage attribute-based customer rebate deals or royalty deals, see the following pages:

- **Customer rebate deals**
- **Customer royalty deals**

 To view and manage non-attribute based customer rebate deals or royalty deals, see the following pages:

- **Non-attribute based customer rebate deals**
- **Non-attribute based customer royalty deals**

All vendor rebate deals are non-attribute based and be accessed using the **Vendor rebate deals** page.

To process, post, or cancel multiple rebate management deals, follow these steps:

1. Go to **Rebate management**.
1. Expand **Periodic tasks**. You can process, post, or cancel multiple rebate management deals by using the commands.

To view and manage all rebate management deals, see the **Rebate workbench** page.

:::image type="content" source="media/rebate-workbench.png" alt-text="Screenshot of the rebate workbench." lightbox="media/rebate-workbench.png":::

## Troubleshooting

To get more information about errors or unexpected behavior, contact Microsoft Support and open a support ticket.
