---
# required metadata

title: Sync omnichannel Inventory changes to FnO via Inventory Visibility
description: This article describes how to enable the omnichannel inventory transaction management in Inventory Visibility, and how to set up the out-of-box transaction aggregation and sync to Dynamics 365 Supply Chain Management via Inventory Visibility
author: yufeihuang
ms.date: 07/12/2024
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: yufeihuang
ms.search.validFrom: 2024-07-20
ms.dyn365.ops.version: 10.0.41
---

# Sync omnichannel Inventory changes to FnO through Inventory Visibility
This article describes how to enable the omnichannel inventory transaction management in Inventory Visibility business layer, and how to set up the out-of-box transaction aggregation and sync to Dynamics 365 Supply Chain Management via Inventory Visibility
## Business scenario fit and benefits
For organizations that have multi-source or channel of inventory operations outside of Dynamics 365 SCM, in the past you usually need to customize different ways to post external inventory changes into Dynamics 365 SCM. With this new capability you can now leverage Inventory Visibility to store your omnichannel inventory transactions. Based on these transaction Inventory Visibility can also create and post inventory journals to Dynamics 365 SCM as an out-of-box integration.

There are two key business benefits:
* Allow you to manage your omnichannel inventory changes all in one place - 

    All inventory changes across your channels or datasources can be posted to Inventory Visibility. IVS will take care of the rest aggregation and posting to FnO
* Enable the end-to-end tracking of inventory flow from source document/transaction to FnO inventory and financial records

    You can store source document type and reference number when posting inventory changes to IV. IV will also link FnO journal number back to inventory transactions


![Sync omnichannel inventory changes to FnO via Inventory Visibility](media/Sync-omnichannel-inventory-changes-to-FnO-via-Inventory-Visibility.png "Sync omnichannel inventory changes to FnO via Inventory Visibility")

## Architechture and dataflow
Inventory Visibility service introduces a new concept called **Business Layer**, which is a layer on top of current Inventory Visibility service. The existing Inventory Visibility service mainly processes and updates data in cache and does not directly wirtes data back to Dynamics 365 Finance and Operations(FnO). While this new Inventory Visibility Business Layer offers:
* A new inventory adjustment API **/api/environment/{environmentId}/transaction/adjustment/bulk** with additional columns for FnO journal integration and for source transaction/document tracking
* Entity that stores omnichannel inventory transactions details that are posted to Inventory Visibility business layer using the new API
* Configurable mechanism that auto-updates the current Inventory Visibility service (in-memory cache service) by certain interval
* Configurable mechanism that aggregates the detailed transactions and synchronize to FnO by certain interval and rules
* A new UI page that allows you to post the inventory adjustment to IV business layer the same as using the API, plus viewing the transactions in detail or aggregated format

![Architecture and dataflow](media/Architecture-and-data-flow.png "Architecture and dataflow")

## Version requirement and supported journal type ##
Required FnO version is **10.0.41** or higher, the supposted journal type for FnO integration under this release is **Inventory adjustment journal**

Required Inventory Visibility Service version is **1.2.3.88** or higher

## Settings
1. Log onto your Dynamics 365 Supply Chain Management/Finance and Operations system > Go to **Feature management**, search for feature **Inventory Visibility integration with inventory adjustment posting** and click **Enable now**
1. Go to **Inventory Management** workspace > Inventory Visibility integration parameters > Transaction > Set **Enabe adjustment journal sync** to **Yes** > Click **Generate configurations**. This will automatically enable mandatory settings in Inventory Visibility service
1. Log onto Inventory Visibiity power app > Settings > Feature Management > Inventory Transactions. You will see the feature is enabled already. > Click **Manage** to check and update configuration if needed. Below are some key settings explained:
    * **Periodically synchronize transaction to IV** - Enable this toggle means the inventory updates to IV business layer will be grouped by batch and posted to IV service. 
    * Correspondingly you can find **Inventory Visibility synchronization frequency** is set to 1 (minute) by default. This means the batch job syncs from IV business layer to IV service runs every minute
    * **Periodically synchronize transaction to FnO** - Enable this toggle means the inventory transactions stored in IV business layer will be aggregated and synced to FnO. Disabling the feature will still allow storage of omnichannel transactions in IV business layer. But there will be no sync to FnO. 
    * Correspondingly you can find **FnO synchronization frequency** is set to 2 (minutes) by default
    * **FnO integration mappings** - you can view the default datasource and physical measure for inventory adjustment update to IV, the **Target Fno Transaction** is default to Inventory adjustment journal. And the **Target FnO Transaction Status** is **Posted** by default, meaning the journal will be posted financially when synced to FnO. If you do not want automatic posting, change the status to **Created**
1. Make sure you also complete settings indicated in [Inventory Visibility adjustment offset](https://learn.microsoft.com/en-us/dynamics365/supply-chain/inventory/inventory-visibility-adjustment-offset) if you enabled sync to FnO

## Create inventory changes and sync to FnO
### Step 1: Create inventory changes in Inventory Visibility business layer
1. Log onto Inventory Visibility power app, on the left panel menu, go to **Inquiries and reports** > Inventory transactions. On the page, you can view either the detailed historical transactions, or aggregated transactions. Here we create a new transaction. On the upper left, click ** Create transaction** > Select the transaction type from dropdown. For example **Inventory adjustment**
1. Enter the required product and dimension information you want to make inventory adjustment on. You can add additional dimension values by clicking **Edit dimensions**.For example, product D0001, Org id usmf, site 1, LocationID(warehouse) 13, colour red, size S, Style women
1. Select datasource, physical measure and enter the inventory adjustment quantity. For example, Data source @iv, physical measure is adjustment, quantity is 5. You also has the option to post the adjustment immediately to Inventory Visibiloty service by setting **Instant update to IV service** to true, this will bypass the parameter you set previously for **Periodically synchronize transaction to IV**
1.Optionally you can enter additional information. For External reference category, you can specify the source transaction type for this inventory adjustment, i.e. sales order/inventory counting delta/POS transaction, etc. Enter the source document ID in the **External reference ID** field. You can also specify FnO journal name for the inventory adjustment journal to use in FnO. If journal name value is left blank. Default journal name set in FnO will be used.
1. You can also specify the item cost price to be created in FnO, if left blank, journal created in FnO will take defalt cost calculation method set in FnO to calculate cost price
1. Trans date is the transaction date on journal line once created in FnO
1. Click **Post**. Once success, click **check record** to view the transaction detail generated from your posting.

### Step 1 (alternative option): Create inventory changes via API post
Use the API **/api/environment/{environmentId}/transaction/adjustment/bulk** to post inventory changes to Inventory Visibility business layer. You can post either single or bulk entries.
For sample API body, you can follow step 1 above on the UI, and click **Developer reference** to generate the samples
### Step 2 (optional): View detaied and aggregated inventory transactions
Access the detailed and aggregated transactions from **Inventory transactions** page. You can track the line status.

For detailed transaction statuses:
*   Created - means transaction detail is created in IV business layer
*   IVPosted - indicate the inventory adjustment for this detailed line has been updated to IV cache successfully
*   Aggregated - meaning detailed lines are aggregated successfully based on same dimension values

For aggregated transaction line statuses
*   Created - means aggregation completed and record created
*   DoNotSync - means this line will not be synced to FnO. This can due to the aggregated line inventory change quantity is 0 (no inventory quantity change therefore no need to sync)
*   FnOSent - sync request is sent to FnO
*   FnOCreateError - error occured during FnO transaction creation
*   FnOCreated - Created successfully
*   FnOPostError - transaction posting failed
*   FnOPosted - post success

You can also navigate from a detailed line to the linked aggregated line. Once the aggregated lines are successfully created/posted in FnO, the returned FnO journal ID and journal line ID will also be attached to the aggregated line. 

If you wish to export the transactions, you can also access them from the dataverse entity. The entities names are **Adjustment Line** and **Agregated Adjustment Line**

Note some information such as **External reference category/ID** or **External dimensions** are not standard fields in FnO and only exist in IV or IV business layer. For these IV-specific information, they will not be aggregated and synced to FnO. You access them only in Inventory Visibility.
### Step 3 (optional): Check inventory journal created/posted in FnO
Once the aggregated line is shown as **FnOCreated** or **FnOPosted**, you can view them in your Finance and Operations system.
