---
title: Set up product search for Inventory Visibility
description: Learn how to set up product search for Inventory Visibility, which lets users search for products and on-hand inventory information based on specific attributes.
author: Weijiesa
ms.author: weijiesa
ms.topic: how-to
ms.date: 11/20/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Set up product search for Inventory Visibility

[!include [banner](../includes/banner.md)]

The *product search* feature lets users search for products and on-hand inventory information based on specific attributes, such as size and color. It provides the following benefits:

- **Time savings** – Users can quickly find products that meet their exact requirements without having to do extensive browsing. Therefore, the feature helps improve the user experience and save valuable time.
- **Higher confidence** – Attribute-based search ensures that users get exactly what they're looking for. Therefore, user confidence increases.
- **Increased product visibility** – Attribute-based search can highlight products that are less often searched for but still potentially relevant. Therefore, users are exposed to a broader range of options that they might not have considered.

This feature is accessible both through the [Inventory Visibility app in Microsoft Power Apps](inventory-visibility-product-search-app.md) and through the [API](inventory-visibility-api.md#product-search-query).

## Prerequisites

Before you can use the product search service, your system must meet the following requirements:

- You must be running Dynamics 365 Supply Chain Management 10.0.36 or later.
- Inventory Visibility version 1.2.2.54 or later must be installed and set up as described in [Install and set up Inventory Visibility](inventory-visibility-setup.md).

## Install the product search service

### New Inventory Visibility installations

The product search service is included in the current version of the Inventory Visibility Add-in. Therefore, you don't have to install it separately if you haven't already installed the add-in for your environment. For information about how to install Inventory Visibility for the first time, see [Install and set up Inventory Visibility](inventory-visibility-setup.md).

### Existing Inventory Visibility installations

If your system is running Inventory Visibility version 1.2.2.53 or earlier, you must update Inventory Visibility in your Microsoft Dynamics Lifecycle Services project and then install the newest version. Learn more in [Install and set up Inventory Visibility](inventory-visibility-setup.md).

## Configure the product search service

Follow these steps to configure product search for Inventory Visibility.

1. If dual-write isn't already enabled for your Lifecycle Services project, enable it as described in [Dual-write setup from Lifecycle Services](../../fin-ops-core/dev-itpro/data-entities/dual-write/lcs-setup.md).
1. In Supply Chain Management, go to **System administration** \> **Workspaces** \> **Data management**, and select the **Framework parameters** tile.
1. On the **Data import/export framework parameters** page, on the **Entity settings** tab, select **Refresh entity list**.
1. The *Refresh entity list* job is added to the batch queue. Wait for the job to be completed.
1. Go back to **System administration** \> **Workspaces** \> **Data management**, and select the **Dual-write** tile.
1. On the Action Pane, select **Apply solution**.
1. In the **Apply solution** dialog box, select **Dynamics 365 Product Search Core**, and then select **Apply**.
1. Wait for the process to be completed. It might take several minutes. When it's completed, the **Dual-write** page is updated and shows all the table maps that were added. Select all the table maps, and then select **Run** on the Action Pane.
1. The **Initial writes and related table map(s)** dialog box appears. For each table map, select the **Initial sync** checkbox, and set the **Master for initial sync** field to *Finance and Operations apps*. Then select **Run**.

## Troubleshooting

If some table maps fail to do an initial synchronization because of a permission issue, follow these steps to check your team roles.

1. Sign in to your Dataverse environment, go to **Settings** \> **Security**, and select **Teams**.
1. Open your team, and select **Manage Roles**.
1. Make sure that the following role is assigned to your team:
    
    - *System Administrator*

For more information about how to set up dual-write security roles, see [Set up dual-write security roles and permissions](../../fin-ops-core/dev-itpro/data-entities/dual-write/security-roles.md).

## Search for products using the API

After you set up the product search service, you can search for products either by using the Inventory Visibility app in Power Apps or by using the Inventory Visibility API. For details about how to search for products by using the Inventory Visibility API, see [Query with product search](inventory-visibility-api.md#product-search-query).

## Search for products using the Inventory Visibility app in Power Apps

After you set up the product search service, you can search for products either by using the Inventory Visibility app in Power Apps or by using the Inventory Visibility API. For details about how to search for products by using the Inventory Visibility app in Power Apps, see [Search for products using the Inventory Visibility app](inventory-visibility-product-search-app.md).
