---
# required metadata

title: Rebate management parameters
description: 
author: sherry-zheng
manager: tfehr
ms.date: 02/19/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  TAMRebateParameters
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2021-02-19
ms.dyn365.ops.version: Release 10.0.18
---

# Rebate management parameters

[!include [banner](../includes/banner.md)]

The **Rebate management parameters** page contains settings that apply across the Rebate management module. These settings affect posting, status updates, number sequences, and other behavior. The parameters setup is shared across legal entities and can be modified with the appropriate security.

To work with the setup parameters, go to **Rebates and deductions \> Setup \> Rebate management parameters** and then make settings as described in the following subsections.

## The Rebate management tab

The following table describes the settings available on the **Rebate management** tab of the **Rebate management parameters** page

| Setting | Description |
| --- | --- |
| **Default status** | Select the default status to be used for all new agreements. Use the [**Rebate statuses** page](rebate-statuses.md) to establish the collection of status values available. <!-- KFM: Are "agreements", "contracts" and "deals" always the same thing? If so, we should use "deals" everywhere to match the UI. -->  |
| **Process by dimension** | Choose whether or not provision, rebate, and write-off transactions should be processed by financial dimension. When enabled, the system uses financial dimensions for the source transactions. |
| **Check if previously posted** | Choose how the system should handle unposted rebate transactions has have processed for the same period more than once. Select one of the following values:<ul><li>**Warning** - The system will allow users to override the original transactions lines, but will display a warning.</li><li>**Error** - The system will prevent users from overriding the original transactions lines, and will display an error. |
| **Automatically post journals** | Choose whether the system should post proposed journals automatically. This includes daily journals used for provisions and customer deductions as well as vendor tax invoice journals. |
| **Automatically post free text invoices** | Choose whether the system should post free text invoices automatically. This applies where the payment type is *Tax invoice customer deductions*. <!-- KFM: What does the second sentence refer to? --> |
| **Rebate item order reference** | Select the rebate reference to use on sales and purchase orders generated from the rebate process (*None*, *Rebate and deductions deal*, *Rebate and deductions number*, *Rebate transaction number*, or *Document notes*). |
| **Use claim process** | Set this to *Yes* if you'd like to use a claims process. When you use a claims process, you are able to mark transactions created by Rebate management as claimed or unclaimed, and subsequently only post the claimed transactions. For example, if you calculates rebates for a month's worth of transactions but the customer has left 2 days unclaimed, the unclaimed transactions will be recreated the next time you run the process function for the same period. <!-- KFM: Please review this. Also, what happens when we set this to no? --> |
| **Include order type journal** | When the agreement's transaction type is set to order, should sales order type Journal be included. This provides flexibility where these types of orders are used for scenarios where a rebate shouldn't apply as yet. <!-- KFM: This isn't clear. Revision needed. --> |

## The Number sequences tab

Use the **Number sequences** tab of the **Rebate management parameters** page to assign number sequence codes for each of the number sequences used by Rebate management. The following table describes the purpose of each sequence used by Rebate management. For more information about number sequences, see [Number sequences overview](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md) and its related topics.

| **Reference** | **Description** |
| --- | --- |
| **Rebate and deductions deal** | Assigns a unique key value for each rebate deal. This key is used when creating deals. |
| **Rebate and deductions number** | Assigns a unique key value for each rebate. This key is used to identify rebate relationships. |
| **Rebate transaction number** | Assigns a unique key value for each rebate transaction. This key is used to identify rebate transactions. |
| **Tax Invoice** | Assigns a unique key value for each rebate invoice. This key is used when automatically posting rebate journals. |

## The Feature visibility tab

Rebate management adds features (fields and functions) to several frequently used pages in Supply Chain Management. <!-- KFM: Maybe mention common pages where these settings are available (eg, sales orders, purchase orders, etc.) Eg: "These pages include pages that are related to vendor master data, released products, purchase orders, transfer orders, and warehouse setup." --> If you're using Rebate management, you must make those features visible everywhere before you can benefit from them. If you aren't using Rebate management, you can hide the features to keep them out of the way.

On the **Feature visibility** tab of the **Rebate management parameters** page, set the **Activate** option to *Yes* to make Rebate management features visible wherever they are available. Set it to *No* to hide the features on common pages outside Rebate management. However, even when the option is set to *No*, the module itself, including the **Rebate management parameters** page, will remain available to users who have the correct permissions to access it.

<!-- KFM: I adapted this section from the Landed cost docs. Please confirm the situation is the same. -->