---
title: Sync external inventory changes through Inventory Visibility (preview)
description: This article describes how to set up the system to sync inventory changes registered in an external system to Dynamics 365 Supply Chain Management and Inventory Visibility through the Inventory Visibility service business layer.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Sync external inventory changes through Inventory Visibility (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!--KFM: Preview until 10.0.41 GA -->

This article describes how to set up the system to sync inventory changes registered in an external system to Dynamics 365 Supply Chain Management and Inventory Visibility through the Inventory Visibility service business layer.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

This feature lets organizations that have multiple sources or channels of inventory operations working outside of Supply Chain Management use Inventory Visibility to store their omnichannel inventory transactions. Based on these transactions, Inventory Visibility can create and post inventory journals to Supply Chain Management. These capabilities provide the following key business benefits:

- **Manage all omnichannel inventory changes all in one place** – You can post inventory changes across all channels and data sources to Inventory Visibility, which takes care of the aggregation and posting to Supply Chain Management

- **Track inventory flow from end to end** – You can track inventory flows from source transactions/documents all the way to Supply Chain Management inventory and financial records. The system stores source document types and reference numbers when posting inventory changes to Inventory Visibility. Inventory Visibility also links Supply Chain Management journal numbers back to their original inventory transaction.

:::image type="content" source="media/sync-omnichannel-inventory-concept.svg" alt-text="Concept diagram." lightbox="media/sync-omnichannel-inventory-concept.svg":::

## Architecture and data flow

Inventory Visibility introduces a new concept called the *business layer*, which sits on top of the Inventory Visibility service. The Inventory Visibility service processes and updates data in the cache, but doesn't directly write data back to Supply Chain Management. The business layer adds the following elements and capabilities:

- An inventory adjustment API (`/api/environment/{environmentId}/transaction/adjustment/bulk`), which has columns for integrating with Supply Chain Management journals and tracking source transactions/documents.
- An entity that stores omnichannel inventory transactions details that are posted to the Inventory Visibility business layer using the new API.
- A configurable mechanism that auto-updates the Inventory Visibility service (in-memory cache service) at a regular interval.
- A configurable mechanism that aggregates the detailed transactions and synchronizes to Supply Chain Management at a regular interval and according to defined rules.
- A new user interface page for the Inventory Visibility app in Power Apps that lets you manually post inventory adjustments to the Inventory Visibility business layer, just as though you had used the API. The user interface also lets you view transactions in a detailed or aggregated format.

:::image type="content" source="media/sync-omnichannel-inventory-architecture.svg" alt-text="Architecture and data flow diagram." lightbox="media/sync-omnichannel-inventory-architecture.svg":::

<!--KFM: Should the top-right arrow point down instead? -->

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.
- The feature that is named *Inventory Visibility integration with inventory adjustment posting* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- You must be running Inventory Visibility Service version 1.2.3.88 or higher. For information about how to install Inventory Visibility, check its version number, and update it if needed, see [Install and set up Inventory Visibility](inventory-visibility-setup.md).

## Configure inventory transaction synchronization

To set up the feature, follow these steps:

1. Sign in to Power Apps, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Settings** \> **Feature management**.
1. On the **Inventory transactions** tile, select **Manage**.
1. Make the following sections in the top section of the **Transaction** page:
    - **Enable feature** – Set to *True* to enable the feature. Set to *False* to disable. It's turned on by default
    - **Is feature initialized** – <!--KFM: Description needed. -->
    - **Fno adjustment integration activity Id** – <!--KFM: Description needed. -->
    - **Fno environment URL** – <!--KFM: Description needed. -->
    - **Fno sync max line count in adjustment journal** – <!--KFM: Description needed. -->
    - **Periodically synchronize transaction to IV** - Set to *True* to set the system to synchronize inventory updates from the Inventory Visibility business layer to the Inventory Visibility service at regular intervals. Set to *False* to disable this functionality.
    - **Periodically synchronize transaction to Fno** - Set to *True* to set the system to aggregate and synchronize inventory updates from the Inventory Visibility business layer to Supply Chain Management at regular intervals. When this is set to *False*, omnichannel transactions are still stored in the Inventory Visibility business layer, but they won't be synced to Supply Chain Management.
    - **Inventory Visibility synchronization frequency** – Enter an integer to control how often (in minutes) the system should synchronize inventory updates from the Inventory Visibility business layer to Supply Chain Management (provided you've enabled this functionality). The default value is 1.
    - **Fno synchronization frequency** – Enter an integer to control how often (in minutes) the system should synchronize inventory updates from the Inventory Visibility business layer to the Inventory visibility service (provided you've enabled this functionality). The default value is 2.

1. Use the **Fno integration mappings** section to control how data is mapped from the Inventory Visibility business layer to Supply Chain Management <!--KFM: This might be wrong. Please review/clarify. -->. Use buttons in the toolbar to add, edit, or delete mappings as needed. Make the following settings for each mapping:
    - **Physical measure name** – <!--KFM: Description needed. -->
    - **Target Fno transaction type** – <!--KFM: Description needed. (default to Inventory adjustment journal) -->
    - **Target FnO Transaction Status** – <!--KFM: General description of this setting is needed. --> Set to one of the following values:
        - *None* – <!--KFM: Description needed. -->
        - *Created* – The system won't automatically post transactions to Supply Chain Management. <!--KFM: This could be clearer. -->
        - *Posted* – The journal will be posted financially when synced to Supply Chain Management.

1. If **Periodically synchronize transaction to Fno** is set to *True*, then you must configure your system to offset inventory adjustments to prevent inventory quantities from being updated twice. For details, see [Inventory Visibility adjustment offset](inventory-visibility-adjustment-offset.md).

## Create inventory changes and sync to Supply Chain Management

### Step 1: Create inventory changes in Inventory Visibility business layer

1. Log onto Inventory Visibility power app, on the left panel menu, go to **Inquiries and reports** > Inventory transactions. On the page, you can view either the detailed historical transactions, or aggregated transactions. Here we create a new transaction. On the upper left, click **Create transaction** > Select the transaction type from dropdown. For example **Inventory adjustment**
1. Enter the required product and dimension information you want to make inventory adjustment on. You can add additional dimension values by clicking **Edit dimensions**.For example, product D0001, Org id usmf, site 1, LocationID(warehouse) 13, colour red, size S, Style women
1. Select datasource, physical measure and enter the inventory adjustment quantity. For example, Data source @iv, physical measure is adjustment, quantity is 5. You also has the option to post the adjustment immediately to Inventory Visibiloty service by setting **Instant update to IV service** to true, this will bypass the parameter you set previously for **Periodically synchronize transaction to IV**
1.Optionally you can enter additional information. For External reference category, you can specify the source transaction type for this inventory adjustment, i.e. sales order/inventory counting delta/POS transaction, etc. Enter the source document ID in the **External reference ID** field. You can also specify Supply Chain Management journal name for the inventory adjustment journal to use in Supply Chain Management. If journal name value is left blank. Default journal name set in Supply Chain Management will be used.
1. You can also specify the item cost price to be created in Supply Chain Management, if left blank, journal created in Supply Chain Management will take defalt cost calculation method set in Supply Chain Management to calculate cost price
1. Trans date is the transaction date on journal line once created in Supply Chain Management
1. Click **Post**. Once success, click **check record** to view the transaction detail generated from your posting.

### Step 1 (alternative option): Create inventory changes via API post

Use the API `/api/environment/{environmentId}/transaction/adjustment/bulk` to post inventory changes to Inventory Visibility business layer. You can post either single or bulk entries.

For sample API body, you can follow step 1 above on the UI, and click **Developer reference** to generate the samples

### Step 2 (optional): View detailed and aggregated inventory transactions

Access the detailed and aggregated transactions from **Inventory transactions** page. You can track the line status.

For detailed transaction statuses:

- Created - means transaction detail is created in IV business layer
- IVPosted - indicate the inventory adjustment for this detailed line has been updated to IV cache successfully
- Aggregated - meaning detailed lines are aggregated successfully based on same dimension values

For aggregated transaction line statuses

- Created - means aggregation completed and record created
- DoNotSync - means this line will not be synced to Supply Chain Management. This can due to the aggregated line inventory change quantity is 0 (no inventory quantity change therefore no need to sync)
- Supply Chain ManagementSent - sync request is sent to Supply Chain Management
- FnOCreateError - error occurred during Supply Chain Management transaction creation
- FnOCreated - Created successfully
- FnOPostError - transaction posting failed
- FnOPosted - post success

You can also navigate from a detailed line to the linked aggregated line. Once the aggregated lines are successfully created/posted in Supply Chain Management, the returned Supply Chain Management journal ID and journal line ID will also be attached to the aggregated line.

If you wish to export the transactions, you can also access them from the dataverse entity. The entities names are **Adjustment Line** and **Aggregated Adjustment Line**

Note some information such as **External reference category/ID** or **External dimensions** are not standard fields in Supply Chain Management and only exist in IV or IV business layer. For these IV-specific information, they will not be aggregated and synced to Supply Chain Management. You access them only in Inventory Visibility.

### Step 3 (optional): Check inventory journal created/posted in Supply Chain Management

Once the aggregated line is shown as **FnOCreated** or **FnOPosted**, you can view them in your Finance and Operations system.
