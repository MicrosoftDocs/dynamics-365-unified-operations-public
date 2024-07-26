---
title: Sync omnichannel Inventory changes to Supply Chain Management via Inventory Visibility
description: This article describes how to enable omnichannel inventory transaction management in the Inventory Visibility business layer, and how to set up the out-of-box transaction aggregation and sync to Dynamics 365 Supply Chain Management through Inventory Visibility
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Sync omnichannel Inventory changes to Supply Chain Management through Inventory Visibility

This article describes how to enable omnichannel inventory transaction management in the Inventory Visibility business layer. It also describes how to set up transaction aggregation and synchronization to Dynamics 365 Supply Chain Management through Inventory Visibility.

This feature lets organizations that have multiple sources or channels of inventory operations outside of Supply Chain Management use Inventory Visibility to store their omnichannel inventory transactions. Based on these transactions, Inventory Visibility can also create and post inventory journals to Supply Chain Management. These capabilities provide teh following key business benefits:

- **Manage all omnichannel inventory changes all in one place** – You can post inventory changes across all channels and data sources to Inventory Visibility, which takes care of the aggregation and posting to Supply Chain Management

- **Track inventory flow from end to end the end-to-end** – You can track inventory flows from source transactions/documents all the way to Supply Chain Management inventory and financial records. The system stores source document types and reference numbers when posting inventory changes to Inventory Visibility. Inventory Visibility also links each Supply Chain Management journal number back to the original inventory transaction.

:::image type="content" source="media/sync-omnichannel-inventory-concept.svg" alt-text="Concept diagram." lightbox="media/sync-omnichannel-inventory-concept.svg":::

## Architecture and data flow

Inventory Visibility introduces a new concept called the *business layer*, which lies on top of the Inventory Visibility service. The Inventory Visibility service processes and updates data in the cache, but doesn't directly write data back to Supply Chain Management. The business layer builds on this by adding the following elements and capabilities:

- An inventory adjustment API (`/api/environment/{environmentId}/transaction/adjustment/bulk`), which has columns for integrating with Supply Chain Management journals and tracking source transactions/documents.
- An entity that stores omnichannel inventory transactions details that are posted to the Inventory Visibility business layer using the new API.
- A configurable mechanism that auto-updates the Inventory Visibility service (in-memory cache service) at a regular interval.
- A configurable mechanism that aggregates the detailed transactions and synchronizes to Supply Chain Management at a regular interval and according to defined rules.
- A new user interface page that lets you post inventory adjustments to the Inventory Visibility business layer, just as though you used the API. The user interface also lets you view transactions in a detailed or aggregated format.

:::image type="content" source="media/sync-omnichannel-inventory-architecture.svg" alt-text="Architecture and data flow diagram." lightbox="media/sync-omnichannel-inventory-architecture.svg":::

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.
- You must be running Inventory Visibility Service version 1.2.3.88 or higher. For information about how to install Inventory Visibility, check its version number, and update it if needed, see [Install and set up Inventory Visibility](inventory-visibility-setup.md).

## Settings

1. Log onto your Dynamics 365 Supply Chain Management/Finance and Operations system > Go to **Feature management**, search for feature **Inventory Visibility integration with inventory adjustment posting** and click **Enable now**
1. Go to **Inventory Management** workspace > Inventory Visibility integration parameters > Transaction > Set **Enabe adjustment journal sync** to **Yes** > Click **Generate configurations**. This will automatically enable mandatory settings in Inventory Visibility service
1. Log onto Inventory Visibiity power app > Settings > Feature Management > Inventory Transactions. You will see the feature is enabled already. > Click **Manage** to check and update configuration if needed. Below are some key settings explained:

    - **Periodically synchronize transaction to IV** - Enable this toggle means the inventory updates to IV business layer will be grouped by batch and posted to IV service.
    - Correspondingly you can find **Inventory Visibility synchronization frequency** is set to 1 (minute) by default. This means the batch job syncs from IV business layer to IV service runs every minute
    - **Periodically synchronize transaction to Supply Chain Management** - Enable this toggle means the inventory transactions stored in IV business layer will be aggregated and synced to Supply Chain Management. Disabling the feature will still allow storage of omnichannel transactions in IV business layer. But there will be no sync to Supply Chain Management.
    - Correspondingly you can find **FnO synchronization frequency** is set to 2 (minutes) by default
    - **FnO integration mappings** - you can view the default datasource and physical measure for inventory adjustment update to IV, the **Target Fno Transaction** is default to Inventory adjustment journal. And the **Target FnO Transaction Status** is **Posted** by default, meaning the journal will be posted financially when synced to Supply Chain Management. If you do not want automatic posting, change the status to **Created**

1. Make sure you also complete settings indicated in [Inventory Visibility adjustment offset](inventory-visibility-adjustment-offset.md) if you enabled sync to Supply Chain Management.

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

Use the API **/api/environment/{environmentId}/transaction/adjustment/bulk** to post inventory changes to Inventory Visibility business layer. You can post either single or bulk entries.

For sample API body, you can follow step 1 above on the UI, and click **Developer reference** to generate the samples

### Step 2 (optional): View detaied and aggregated inventory transactions

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
