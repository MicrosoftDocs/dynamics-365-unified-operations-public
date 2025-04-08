---
title: Sync external inventory adjustments through Inventory Visibility
description: This article explains how to set up the system to sync inventory adjustments registered in an external system to Microsoft Dynamics 365 Supply Chain Management and Inventory Visibility through the Inventory Visibility service business layer.
author: yufei-huang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 08/26/2024
ms.custom: 
  - bap-template
---

# Sync external inventory adjustments through Inventory Visibility

[!include [banner](../includes/banner.md)]

This article explains how to set up the system to sync inventory adjustment transactions that are registered in an external system to Microsoft Dynamics 365 Supply Chain Management and Inventory Visibility through the Inventory Visibility service business layer.

Some organizations have multiple sources or channels of inventory operations that work outside Supply Chain Management. This feature enables those organizations to use Inventory Visibility to store their omnichannel inventory transactions. Based on these transactions, Inventory Visibility can create and post inventory adjustment journals to Supply Chain Management. These capabilities provide the following key business benefits:

- **Manage all omnichannel inventory adjustments in one place.** You can post inventory adjustments across all channels and data sources to Inventory Visibility. Inventory Visibility then handles the aggregation and posting to Supply Chain Management.
- **Track inventory flow from end to end.** You can track inventory flows from source transactions/documents all the way to Supply Chain Management inventory and financial records. The system stores source document types and reference numbers when it posts inventory adjustments to Inventory Visibility. Inventory Visibility also links Supply Chain Management journal numbers to their original inventory transaction.

:::image type="content" source="media/sync-omnichannel-inventory-concept.svg" alt-text="Concept diagram." lightbox="media/sync-omnichannel-inventory-concept.svg":::

## Architecture and data flow

Inventory Visibility introduces the concept of the *business layer*, which sits on top of the Inventory Visibility service. The Inventory Visibility service processes and updates data in the cache, but it doesn't directly write data back to Supply Chain Management. The business layer feature adds the following elements and capabilities:

- An inventory adjustment API (`/api/environment/{environmentId}/transaction/adjustment/bulk`) that is designed to create inventory adjustment transactions in the Inventory Visibility business layer. The business layer has columns that are used to integrate with Supply Chain Management journals and track source transactions/documents.
- An entity that stores omnichannel inventory transactions details that are posted to the Inventory Visibility business layer by using the new API.
- A configurable mechanism that automatically updates posted inventory adjustment transactions to the Inventory Visibility service (in-memory cache service) at a regular interval.
- A configurable mechanism that aggregates the detailed inventory adjustment transactions and syncs to Supply Chain Management at a regular interval and according to defined rules.
- A new user interface (UI) page for the Inventory Visibility app in Power Apps. This page lets you manually post inventory adjustment transactions to the Inventory Visibility business layer. It's an alternative to using the API. The UI also lets you view transactions in a detailed or aggregated format.

:::image type="content" source="media/sync-omnichannel-inventory-architecture.svg" alt-text="Architecture and data flow diagram." lightbox="media/sync-omnichannel-inventory-architecture.svg":::

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Dynamics 365 Supply Chain Management version 10.0.41 or later.
- You must be running Inventory Visibility service version 1.2.3.88 or later. Learn how to install Inventory Visibility, check its version number, and update it as required in [Install and set up Inventory Visibility](inventory-visibility-setup.md).
- The following features must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):

    - *Inventory Visibility integration with inventory adjustment offset* (This feature is a prerequisite.)
    - *Inventory Visibility integration* (prerequisite)
    - *Inventory Visibility transaction integration* (This feature adds the features that are described in this article.)

## Configure inventory transaction synchronization

### Set up the feature for the first time

To set up the feature for the first time, follow these steps.

1. Sign in to Supply Chain Management.
1. Go to **Inventory Management** \> **Setup** \> **Inventory Visibility** \> **Inventory Visibility integration parameters**.
1. On the **Transaction** tab, set the **Enable adjustment journal sync** option to *Yes*.
1. Select **Generate configurations** to run an automatic deployment script that initializes the configuration in Supply Chain Management and the Inventory Visibility service.
1. Select **Enable posting job** to open the **Inventory Visibility posting job** dialog box.
1. Each time the *Inventory Visibility posting job* runs, it automatically posts the inventory adjustment journals submitted from the Inventory Visibility business layer. You should schedule this job to run as often as is appropriate for your business. Depending on the volume of incoming data, this job can be resource intensive, so we recommend scheduling it to run during off-peak hours. Select the **Recurrence** link to open the **Define recurrence** dialog, use it to set up your schedule, and then select **OK** to save your settings.
1. Select **OK** to close the dialog box.

### Manage the feature configuration

To manage the feature configuration, follow these steps.

1. Sign in to Power Apps, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Settings** \> **Feature management**.
1. On the **Inventory transactions** tile, select **Manage**.
1. On the **Transaction** page, in the upper section, set the following fields:
    - **Enable feature** – Set this option to *True* to enable the feature. Set it to *False* to disable the feature. The feature is automatically turned on when you initialize the configuration as described in the previous section.
    - **Periodically synchronize transaction to IV** – Set this option to *True* if you want the system to automatically sync inventory updates from the Inventory Visibility business layer to the Inventory Visibility service at regular intervals. Set it to *False* to disable this functionality.
    - **Inventory Visibility synchronization frequency** – Enter an integer to specify how often (in minutes) the system syncs inventory updates from the Inventory Visibility business layer to Supply Chain Management (if you enabled this functionality). The default value is *5*.

1. In the **Fno Synchronization Settings** section, set the following fields:
    - **Enable Sync Job** – Set this option to *True* if you want the system to automatically aggregate and sync inventory updates from the Inventory Visibility business layer to Supply Chain Management at regular intervals. When this option is set to *False*, omnichannel transactions are still stored in the Inventory Visibility business layer. However, they aren't synced to Supply Chain Management.
    - **Job settings** – Select the setting value to open the detailed settings page, where you can specify the start and end time, recurrence interval, and unit for synchronizing inventory updates from the Inventory Visibility business layer to the Inventory Visibility service (if this functionality is enabled). The job is automatically scheduled with default settings when you install Inventory Visibility.
    - **Fno sync max line count in adjustment journal** – Enter an integer to specify the maximum number of inventory adjustment lines that are allowed per adjustment journal during synchronization back to Supply Chain Management. The default value is *10,000*.
    - **Fno sync max journal count in package** – Enter an integer to specify the maximum number of inventory adjustment journals that are allowed per data package during synchronization back to Supply Chain Management. The default value is *1*.

1. Use the **Fno integration mappings** section to control how data is mapped from the Inventory Visibility business layer to Supply Chain Management. Use the buttons on the toolbar to add, edit, or delete mappings as required. For each mapping, set the following fields:

    - **Physical measure name** – Select the physical measure that provides the quantity of the inventory.
    - **Target FnO Transaction type** – Specify the type of inventory journal that is created in Supply Chain Management. The default value is *Inventory adjustment journal*.
    - **Target FnO Transaction Status** – Select one of the following values to specify the status of the inventory journal that is created in Supply Chain Management:

        - *None* – The system doesn't create transactions in Supply Chain Management.
        - *Created* – The system creates transactions but doesn't automatically post them in Supply Chain Management.
        - *Posted* – The system creates transactions and financially posts the journal in Supply Chain Management.

1. If you set the **Periodically synchronize transaction to Fno** option to *True*, you must ensure that your system in configured to offset inventory adjustments to prevent inventory quantities from being updated twice. Learn more in [Inventory Visibility adjustment offset](inventory-visibility-adjustment-offset.md).

## Manually enter inventory adjustments in the Inventory Visibility app

You can use the Inventory Visibility app in Power Apps to manually enter inventory adjustments directly in the Inventory Visibility business layer.

1. Sign in to Power Apps, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Inquiries and reports** \> **Inventory transactions**.
1. On the toolbar, select **Create transaction** \> **Inventory adjustment**.
1. On the **Create inventory adjustment** page, on the **Product and dimension information** FastTab, specify the product that you want to adjust inventory for. If some of the product dimensions that you need (such as color or style) aren't shown, select **Edit dimensions** to add them.
1. On the **Adjustment quantity** FastTab, select the data source, physical measure, and quantity of the inventory adjustment. To immediately update inventory adjustments to the Inventory Visibility service cache from the staging area, select the **Instant update to IV service** checkbox.
1. On the **Additional information** FastTab, you can set the following optional fields:

    - **External reference category** – Specify the source transaction type for the inventory adjustment, such as sales order, inventory counting delta, or POS transaction.
    - **External reference ID** – Enter the source document ID from the external system.
    - **Supply Chain Management journal name** – Specify the inventory adjustment journal to use in Supply Chain Management. If you leave this field blank, the default journal name that is set in Supply Chain Management is used.
    - **Item cost price** – Specify the item cost price to create in Supply Chain Management. If you leave this field blank, the journal that is created in Supply Chain Management uses the default cost calculation method that is set in Supply Chain Management to calculate the cost price.
    - **Trans date** – The transaction date to set on the journal line when it's created in Supply Chain Management.

1. To preview what your inventory adjustment will look like when they are posted to the Inventory Visibility business layer through the API, select **Developer reference**. This action shows the JavaScript Object Notation (JSON) body that will be sent to the Inventory Visibility business layer when you post the transaction.
1. On the toolbar, select **Post**.

## Submit inventory adjustments to the Inventory Visibility API

External systems typically submit inventory adjustments to the Inventory Visibility business layer through the Inventory adjustment API. The following example shows the API and body content details.

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
Query(Url Parameters):
    createWithIVSync # bool, optional
Body:
[
    {
        "id": string
        "organizationId": string,
        "productId": string,
        "quantityDataSource": string,
        "physicalMeasure": string,
        "dimensions": {
            "siteId": string,
            "locationId": string,
            [key:string]: string, # optional
        },
        "quantity": number,
        "externalReferenceCategory": string, # optional
        "externalReferenceId": string, # optional
        "fnoJournalNameId": string, # optional
        "costPrice": number, # optional
        "transDate": date, # optional
    },
]
```

Learn more about how to work with the Inventory Visibility API, including how to authenticate and get an access token, in [Inventory Visibility public APIs](inventory-visibility-api.md).

## View inventory transactions in the Inventory Visibility app

The Inventory Visibility app in Power Apps provides a UI where you can view detailed and aggregated inventory transactions.

- Detailed inventory transactions include all individual transactions together with all the original details.
- Aggregated inventory transactions combine lines that have matching dimension values (such as site, warehouse, and color). Some information might be omitted. Instead of showing every individual transaction, the UI shows totals or averages over the specified dimensions. Only the aggregated transactions are synced with Supply Chain Management.

Detailed and aggregated transactions differ in the following ways:

- Granularity:

    - Detailed transactions show individual original inventory adjustment transactions and provide fine-grained data.
    - Aggregated transactions show summarized data and provide a higher-level overview.

- Data volume:

    - Detailed transaction data sets are typically larger because they include every transaction.
    - Aggregated transaction data sets are typically smaller because they condense multiple similar transactions into single records.

### View detailed inventory transactions

To view detailed inventory transactions, follow these steps.

1. Sign in to Power Apps, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Inquiries and reports** \> **Inventory transactions**.
1. In the row where the **Type** field is set to *Detail*, in the **Action** column, select **View**.

   On the **Transaction details** page, a grid lists details for each successful transaction. Most of the columns are self-explanatory, but here are some important columns to note:

    - **Line record ID** – The globally unique identifier (GUID) that is automatically generated for each original inventory adjustment transaction. Select the link to view more details about the transaction.
    - **Source line status** – The current status of the transaction. The following values are used:

        - *Created* – The adjustment was created in the Inventory Visibility business layer and is waiting to be posted. This status is the initial status for the inventory adjustment records.
        - *IVPosted* – The adjustment was successfully updated in the Inventory Visibility cache from the staging area. This status is the prerequisite status for aggregation.
        - *Aggregated* – Detailed lines were successfully aggregated based on matching dimension values. This status is the prerequisite status for synchronization to Supply Chain Management.

    - **Aggregated line ID** – Select the link to view details about the linked aggregated line. After the aggregated lines are successfully created and/or posted in Supply Chain Management, the journal ID and journal line ID that Supply Chain Management returns are added to the aggregated transaction details.

### View aggregated inventory transactions

To view aggregated inventory transactions, follow these steps.

1. Sign in to Power Apps, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Inquiries and reports** \> **Inventory transactions**.
1. In the row where the **Type** field is set to *Aggregated*, in the **Action** column, select **View**.

    On the **Transaction aggregated** page, a grid lists details for each successful aggregated transaction. Most of the columns are self-explanatory, but here are some important columns to note:

    - **Line record ID** – The GUID that is automatically generated for each aggregated inventory adjustment transaction. Select the link to view more details about the aggregated transaction. After the aggregated lines are successfully created and/or posted in Supply Chain Management, the journal ID and journal line ID that Supply Chain Management returns are included in the aggregated transaction details.
    - **Aggregated line status** – The current status of the aggregated transaction. The following values are used:

        - *Created* – The aggregated transaction record was successfully created. This status is the initial status for the aggregated transaction record.
        - *DoNotSync* – The line won't be synced to Supply Chain Management. This status typically occurs because the inventory change quantity of the aggregated line is 0 (zero). (Because the inventory quantity wasn't changed, there is no need to sync it.)
        - *FnOSyncEnqueued* – Inventory Visibility sent a request to sync the line with Supply Chain Management. This status indicates that the record was synced in Supply Chain Management and is awaiting further processing.
        - *FnOTransCreated* – Supply Chain Management successfully processed the synchronization request and created the inventory journal.
        - *FnOTransCreateError* – An error occurred during the attempt to create the inventory journal in Supply Chain Management. You can use the message ID to check the error. Go to **Supply Chain Management** \> **System administration workspace** \> **Data Management IT** \> **Recurring data jobs**.
        - *FnOTransPosted* – The inventory journal was successfully posted.
        - *FnOTransPostError* – Inventory journal posting failed.

## Export transaction details

To export transaction details, you must access them from the Dataverse entity and export them from there. The entity names are *Adjustment Line* and *Aggregated Adjustment Line*.

## Check inventory journals posted to Supply Chain Management

To view the aggregated lines that were successfully posted or created in Supply Chain Management, follow these steps.

1. Sign in to Supply Chain Management.
1. Go to **Inventory Management** \> **Journal entries** \> **Items** \> **Inventory adjustment**.
1. Change the filter for the **Posted** column as required to view posted journals, unposted journals, or all journals.

> [!NOTE]
> Some of the optional fields that you can submit to the Inventory Visibility business layer don't exist as standard fields in Supply Chain Management. These fields include **External reference category**, **External reference ID**, and any other external dimensions. These fields aren't synced to Supply Chain Management. However, they are stored in the business layer and can be read by using the Inventory Visibility app, as described earlier in this article.
