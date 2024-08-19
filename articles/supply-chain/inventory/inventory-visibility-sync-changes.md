---
title: Sync external inventory adjustments through Inventory Visibility (preview)
description: This article describes how to set up the system to sync inventory adjustments registered in an external system to Dynamics 365 Supply Chain Management and Inventory Visibility through the Inventory Visibility service business layer.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Sync external inventory adjustments through Inventory Visibility (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!--KFM: Preview until 10.0.41 GA -->

<!--KFM: There is some confusion in this article related to "transaction" vs "adjustment" vs "change". Are these always the same thing? -->
<!--Roger: "Transaction" represent all type of business activities managed in the IVS, which include ("Adjustment / Counting / Transfer / etc..") , those transactions will lead to inventory "Change" in the backend FnO system. -->

This article describes how to set up the system to sync inventory adjustment transactions registered in an external system to Dynamics 365 Supply Chain Management and Inventory Visibility through the Inventory Visibility service business layer.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

This feature lets organizations that have multiple sources or channels of inventory operations working outside of Supply Chain Management use Inventory Visibility to store their omnichannel inventory transactions. Based on these transactions, Inventory Visibility can create and post inventory adjustment journals to Supply Chain Management. These capabilities provide the following key business benefits:

- **Manage all omnichannel inventory adjustments all in one place** – You can post inventory adjustments across all channels and data sources to Inventory Visibility, which takes care of the aggregation and posting to Supply Chain Management

- **Track inventory flow from end to end** – You can track inventory flows from source transactions/documents all the way to Supply Chain Management inventory and financial records. The system stores source document types and reference numbers when posting inventory adjustments to Inventory Visibility. Inventory Visibility also links Supply Chain Management journal numbers back to their original inventory transaction.

:::image type="content" source="media/sync-omnichannel-inventory-concept.svg" alt-text="Concept diagram." lightbox="media/sync-omnichannel-inventory-concept.svg":::

## Architecture and data flow

Inventory Visibility introduces a new concept called the *business layer*, which sits on top of the Inventory Visibility service. The Inventory Visibility service processes and updates data in the cache, but doesn't directly write data back to Supply Chain Management. The business layer feature adds the following elements and capabilities:

- An inventory adjustment API (`/api/environment/{environmentId}/transaction/adjustment/bulk`) is designed to create inventory adjustment transactions in the Inventory Visibility business layer, which has columns for integrating with Supply Chain Management journals and tracking source transactions/documents.
- An entity that stores omnichannel inventory transactions details that are posted to the Inventory Visibility business layer using the new API.
- A configurable mechanism that auto-updates posted Inventory Adjustment transactions to the Inventory Visibility service (in-memory cache service) at a regular interval.
- A configurable mechanism that aggregates the detailed Inventory Adjustment transactions and synchronizes to Supply Chain Management at a regular interval and according to defined rules.
- A new user interface page for the Inventory Visibility app in Power Apps that lets you manually post inventory adjustment transactions to the Inventory Visibility business layer, just as though you had used the API. The user interface also lets you view transactions in a detailed or aggregated format.

:::image type="content" source="media/sync-omnichannel-inventory-architecture.svg" alt-text="Architecture and data flow diagram." lightbox="media/sync-omnichannel-inventory-architecture.svg":::

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.
- You must be running Inventory Visibility Service version 1.2.3.88 or higher. For information about how to install Inventory Visibility, check its version number, and update it if needed, see [Install and set up Inventory Visibility](inventory-visibility-setup.md).
- The feature that is named *Inventory Visibility integration with inventory adjustment posting* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
> [!NOTE]
> Two dependent features: *Inventory Visibility integration with inventory adjustment offset* and *Inventory Visibility transaction integration* must be turned on in feature management.

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

## Manually enter inventory adjustments in the Inventory Visibility app

You can manually enter inventory adjustments directly into the Inventor Visibility business layer using the Inventory Visibility app in Power Apps. Here's how to do it:

1. Sign in to Power Apps, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Inquiries and reports** \> **Inventory transactions**.
1. From the toolbar, select **Create transaction** \> **Inventory adjustment**. <!--KFM: Will we have other options here? -->
1. The **Create inventory adjustment** page opens. On the **Product and dimension information** FastTab, specify the product you want to adjust inventory for. If you don't see all of the product dimensions you need (such as color or style), then select **Edit dimensions** to add them.
1. On the **Adjustment quantity** FastTab, select the **Data source**, **Physical measure**, and **Quantity** of the inventory adjustment.
1. On the Additional information FastTab, you can specify the following optional information:
    - **External reference category** – Specify the source transaction type for this inventory adjustment, such as sales order, inventory counting delta, or POS transaction.
    - **External reference ID** – Enter the source document ID from the external system.
    - **Supply Chain Management journal name** – Specify the inventory adjustment journal to use in Supply Chain Management. If you leave this field blank, the default journal name set in Supply Chain Management will be used.
    - **Item cost price** – Specify the item cost price to be created in Supply Chain Management. If you leave this field blank, the journal created in Supply Chain Management will use the default cost calculation method set in Supply Chain Management to calculate the cost price.
    - **Trans date** – The transaction date to set on the journal line when it's created in Supply Chain Management.

1. If you'd like to see how your inventory adjustment will look when posted to the Inventory Visibility business layer through the API, select **Developer reference**. This will show you the JSON body that will be sent to the Inventory Visibility business layer when you post the transaction.
1. From the toolbar, select **Post**.

## Submit inventory adjustments to the Inventory Visibility API

External systems typically submit inventory adjustments to the Inventory Visibility business layer through the transaction adjustment API. Here are the API and body content details:

<!--KFM: IMPORTANT!!  I added this specification based on what we have in the existing API documentation. I guessed the data types and many other details, including the method (POST). PLEASE REVIEW THIS CAREFULLY! Other details may be missing (for example, how to submit bulk updates). -->

```txt
Path:
    /api/environment/{environmentId}/transaction/adjustment/bulk
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    {
        productId: string,
        organizationId: string,
        dimensions: {
            siteId: string,
            locationId: string,
            [key:string]: string, # optional
        },
        quantityDataSource: string,
        physicalMeasure: string,
        quantity: number,
        externalReferenceCategory: string, # optional
        externalReferenceId: string, # optional
        fnoJournalNameId: string, # optional
        costPrice: number, # optional
        transDate: datetime, # optional
    }
```

For more information about how to work with the Inventory Visibility API, including how to authenticate and get an access token, see [Inventory Visibility public APIs](inventory-visibility-api.md).

## View inventory transactions in the Inventory Visibility app

The Inventory Visibility app in Power Apps provides a user interface for viewing detailed and aggregated inventory transactions.

<!--KFM: Briefly describe why we might do this and how detailed transactions differ from aggregated transactions. Define what aggregated transactions are and why we do that. -->

### View detailed inventory transactions

To view detailed inventory transactions, follow these steps:

1. Sign in to Power Apps, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Inquiries and reports** \> **Inventory transactions**.
1. Select the **View** button in the **Action** column for the row where **Type** is *Detail*.
1. The **Transaction details** page opens, showing a grid that lists details for each successful transaction. Most columns are self-explanatory, but here are some key columns to note:
    - **Line record ID** – <!--KFM: briefly describe what this is -->. Select this link to view more details about the transaction.
    - **Source line status** – Shows the current status of the transaction using one of the following values:
        - *Created* - The adjustment was created in Inventory Visibility business layer. <!--KFM: and is waiting to be posted? -->
        - *IVPosted* - The adjustment was successfully updated in Inventory Visibility cache. <!--KFM: and is waiting/ready to be aggregated? -->
        - *Aggregated* - Detailed lines were successfully aggregated based on matching dimension values. <!--KFM: and is ready to be(has been?)  posted to SCM? Has also been posted to IV? -->
    - **Aggregated line ID** –  <!--KFM: briefly describe what this is -->. Select this link to open details about the linked aggregated line. Once the aggregated lines are successfully created/posted in Supply Chain Management, the returned Supply Chain Management journal ID and journal line ID will be included in the aggregated transaction details.

### View aggregated inventory transactions

To view aggregated inventory transactions, follow these steps:

1. Sign in to Power Apps, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Inquiries and reports** \> **Inventory transactions**.
1. Select the **View** button in the **Action** column for the row where **Type** is *Aggregated*.
1. The **Transaction aggregated** page opens, showing a grid that lists details for each successful aggregated transaction. Most columns are self-explanatory, but here are some key columns to note:
    - **Line record ID** – <!--KFM: briefly describe what this is -->. Select this link to view more details about the aggregated transaction. Once the aggregated lines are successfully created/posted in Supply Chain Management, the returned Supply Chain Management journal ID and journal line ID will be included in the aggregated transaction details.
    - **Aggregated line status** – Shows the current status of the aggregated transaction using one of the following values:
        - *Created* - The aggregated transaction record was created successfully. <!--KFM: And is waiting to sync? -->
        - *DoNotSync* - The line won't be synced to Supply Chain Management. This is typically because the aggregated line inventory change quantity is 0 (inventory quantity wasn't changed, so there is no need to sync it). <!--KFM: Might this also happen due to configuration setting? -->
        - *Supply Chain ManagementSent* - Inventory Visibility sent a request to synchronize the line with Supply Chain Management
        - *FnOCreateError* - An error occurred when trying to create the transaction in Supply Chain Management. <!--KFM: What now? -->
        - *FnOCreated* - Supply Chain Management successfully processed the sync request and created the transaction.
        - *FnOPostError* - The post failed. <!--KFM: What now? How is this different from the create error? -->
        - *FnOPosted* - The post succeeded. <!--KFM: How is this different from *FnOCreated*? -->

        <!--KFM: In my test system, I don't see any of the above status values. Instead I see *FnoTransPosted* and *FNOTransPostError*. Please update the above list to include these and double-check the other values. -->

## Export transaction details

To export transaction details, you must access them from the Dataverse entity and export them from there. The entity names are **Adjustment Line** and **Aggregated Adjustment Line**

## Check inventory journals posted to Supply Chain Management

<!--KFM: We should either explain how to do this here, or provide a link, or remove this section. -->

Aggregated lines that were successfully posted or created in Supply Chain Management can be seen in Supply Chain Management.

> [!NOTE]
> Some of the optional fields that you're able to submit to the Inventory Visibility business layer doesn't exist as standard fields in Supply Chain Management (including **External reference category**, **External reference ID**, and external dimensions <!--KFM: Can we really have external dimensions? -->). These fields aren't synced to Supply Chain Management, but they are stored in the business layer and can be read using the Inventory Visibility app, as described previously in this article.
