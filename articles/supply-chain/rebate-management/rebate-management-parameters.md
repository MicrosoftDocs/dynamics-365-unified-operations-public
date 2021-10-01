---
# required metadata

title: Rebate management parameters
description: This topic describes the Rebate management parameters page. This page contains settings that affect posting, status updates, number sequences, and other behavior.
author: sherry-zheng
ms.date: 02/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: TAMRebateParameters
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2021-02-19
ms.dyn365.ops.version: 10.0.18
---

# Rebate management parameters

[!include [banner](../includes/banner.md)]

The **Rebate management parameters** page is used to define settings that apply across the **Rebate management** module. These settings affect posting, status updates, number sequences, and other behavior. The setup on this page is shared across legal entities and can be modified by users who have the appropriate security permissions.

To open the **Rebate management parameters** page, go to **Rebate management \> Setup \> Rebate management parameters**. Then set the fields as described in the following subsections.

## Rebate management tab

The following table describes the fields that are available on the **Rebate management** tab of the **Rebate management parameters** page.

| Field | Description |
|---|---|
| Default status | Select the default status for all new deals. To define the set of status values that is available for selection, use the [**Rebate statuses** page](rebate-statuses.md). |
| Process by dimension | Select whether provision, rebate, and write-off transactions should be processed by financial dimension. When this option is turned on, the system uses financial dimensions from the source transactions in the target transactions. |
| Check if previously posted | <p>Select the system behavior if unposted rebate transactions are processed more than once for the same period:</p><ul><li>**Warning** – The system allows users to override the original transactions lines, but a warning is shown.</li><li>**Error** – The system prevents users from overriding the original transactions lines, and an error message is shown. |
| Automatically post journals | Select whether the system should automatically post proposed journals. Those journals include daily journals that are used for provisions and customer deductions, and also vendor tax invoice journals. |
| Automatically post free text invoices | Select whether the system should automatically post free text invoices. This option applies only to free text invoices where the payment type is set to *Tax invoice customer deductions*. |
| Rebate item order reference | Select the rebate reference to use on sales orders and purchase orders that are generated from the rebate process (*None*, *Rebate management deal*, *Rebate management number*, *Rebate transaction number*, or *Document notes*). |
| Use claim process | <p>Set this option to *Yes* to use a claims process. In this way, you can mark transactions that Rebate management creates as either claimed or unclaimed, and then post only the claimed transactions.</p><p>For example, you calculate rebates for a month's worth of transactions, but the customer has left two days unclaimed. In this case, the unclaimed transactions will be re-created the next time that you run the *Process* function for the next period.</p><p>If you set this option to *No*, all claim transactions are posted.</p> |
| Include order type journal | For deals or deal lines where the transaction type is set to *Order*, this option controls whether a sales order of the *Journal* type should be included. It provides flexibility if those types of orders are used in scenarios where a rebate should not yet apply. |

## Number sequences tab

Use the **Number sequences** tab on the **Rebate management parameters** page to assign number sequence codes to the different number sequences that Rebate management uses. The following table describes the purpose of each of those number sequences. For more information about number sequences, see [Number sequences overview](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md) and its related topics.

| Reference | Description |
|---|---|
| Rebate management deal | The number sequence assigns a unique key value to each rebate deal. This key is used when deals are created. |
| Rebate management number | The number sequence assigns a unique key value to each rebate. This key is used to identify rebate relationships. |
| Rebate transaction number | The number sequence assigns a unique key value to each rebate transaction. This key is used to identify rebate transactions. |
| Tax Invoice | The number sequence assigns a unique key value to each rebate invoice. This key is used when rebate journals are automatically posted. |

## Feature visibility tab

Rebate management adds features (fields and functions) to several frequently used pages in Microsoft Dynamics 365 Supply Chain Management. Those pages include pages that are related to sales orders and sales deals. If you're using Rebate management, you must make those features visible everywhere before you can benefit from them. If you aren't using Rebate management, you can hide the features to keep them out of the way.

On the **Feature visibility** tab of the **Rebate management parameters** page, set the **Activate** option to *Yes* to make Rebate management features visible wherever they are available. Set it to *No* to hide the features on common pages outside the **Rebate management** module. However, even when the option is set to *No*, the module itself, including the **Rebate management parameters** page, will remain available to users who have the appropriate permissions to access it.
