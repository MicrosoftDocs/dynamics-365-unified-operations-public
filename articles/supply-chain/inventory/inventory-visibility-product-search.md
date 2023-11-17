---
title: Set up product search for Inventory Visibility
description: This article describes how to set up product search for Inventory Visibility, which lets users search for products and on-hand inventory information based on specific attributes such as size, color, and more.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/17/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Set up product search for Inventory Visibility

The *product search* feature lets users search for products and on-hand inventory information based on specific attributes such as size, color, and more. It provides the following benefits:

- **Time savings** – Users can quickly find products that meet their exact requirements, eliminating the need for extensive browsing. This improves user experience and saves valuable time.
- **Higher confidence** – Attribute-based search ensures that users get precisely what they're looking for, leading to increased confidence.
- **Increased product visibility** – Attribute-based search can highlight products that are less-often searched for but still potentially relevant. This exposes users to a broader range of options that they might not have considered.

This feature is accessible both through the [Inventory Visibility app in Power Apps](inventory-visibility-product-search-app.md) and through the [API](inventory-visibility-api.md#product-search-query).

## Prerequisites

To use the product search service, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.36 or later.
- You must be running Inventory Visibility version 1.2.2.54 or newer.

## Install the product search service

### New Inventory Visibility installations

The product search service is included in the current version of the Inventory Visibility add-in, so you don't need to install it separately if you haven't already installed the add-in for your environment. For instructions about how to install Inventory Visibility for the first time, see [Install and set up Inventory Visibility](inventory-visibility-setup.md).

### Existing Inventory Visibility installations

If your system is running Inventory Visibility version 1.2.2.53 or older, then you must uninstall Inventory Visibility in your Microsoft Dynamics Lifecycle Services (LCS) project and then install the newest version. See also [Install and set up Inventory Visibility](inventory-visibility-setup.md).

## Configure the product search service

Follow these steps to configure product search for Inventory Visibility:

1. Enable dual-write for your LCS project if it isn't already, as described in [Dual-write setup from Lifecycle Services](../../fin-ops-core/dev-itpro/data-entities/dual-write/lcs-setup.md).
1. In Supply Chain Management, go to **System administration \> Workspaces \> Data management** and select the **Framework parameters** tile.
1. On the **Data import/export framework parameters** page, open the **Entity settings** tab and select **Refresh entity list**.
1. The *Refresh entity list* job is added to the batch queue. Wait for the job to complete.
1. Go back to **System administration \> Workspaces \> Data management** and select the **Dual-write** tile.
1. On the Action Pane, select **Apply solution**.
1. On the Apply solution dialog, select **Dynamics 365 Product Search Core** and then select **Apply**.
1. Wait for the process to complete. It might take several minutes. When it's done, the **Dual-write** page updates to show all of the table maps that were added. Select all of the table maps and then select **Run** on the Action Pane.
1. The **Initial writes and related table map(s)** dialog opens. For each table map, mark the **Initial sync** check box and set **Master for initial sync** to *Finance and Operations apps*. Then select **Run**.

## Troubleshooting

If some table maps fail to do an initial sync because of a permission issue, then check your team roles by following these steps:

1. Sign in to your Dataverse environment, go to **Settings \> Security**, and select **Teams**.
1. Open your team and select **Manage Roles**.
1. Make sure your team has the following roles assigned:
   - *Dual-write app user*
   - *Dual-write runtime user*

For more how to set up dual-write security roles, see [Set up dual-write security roles and permissions](../../fin-ops-core/dev-itpro/data-entities/dual-write/security-roles.md)

## Search for products using the API

After you have set up the product search service, you can search for products using either the Inventory Visibility app in Power Apps or the Inventory Visibility API. For details about how to search for products using the Inventory Visibility API, see [Query with product search](inventory-visibility-api.md#product-search-query).

## Search for products using the Inventory Visibility app in Power Apps

After you have set up the product search service, you can search for products using either the Inventory Visibility app in Power Apps or the Inventory Visibility API. For details about how to search for products using the Inventory Visibility app in Power Apps, see [Search for products using the Inventory Visibility app](inventory-visibility-product-search-app.md).
