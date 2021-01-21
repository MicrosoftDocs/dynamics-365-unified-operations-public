---
# required metadata

title: Costing parameter values setup
description: When you set up the Landed cost module, you are able to establish several sets of common values that will be available when you select certain types of costing parameter values elsewhere in the application. This topic describes how to set up each of these sets of values.
author: RichardLuan
manager: tfehr
ms.date: 12/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: riluan
ms.search.validFrom: 2020-12-07
ms.dyn365.ops.version: Release 10.0.17
---

# Costing parameter values setup

When you set up the Landed cost module, you are able to establish several sets of common values (and related settings per value) that will be available when you select certain types of costing parameter values elsewhere in the application. This topic describes how to set up each of these sets of values.

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

## Set up cost type codes

Cost type codes determine the type of cost that is incurred when landing the goods into the warehouse, or the landed costs of the voyage. They normally increase the value of the goods, but they can be used to accrue amounts into the ledger. Ledger adjustments are used when a cost is accrued over a period of time or during a series of voyages and offset in a single transaction.

> [!NOTE]
> If the cost type table is shared across legal entities, the chart of accounts must also be shared across entities for the posting transactions to function correctly.

To set up your cost type codes, go to **Landed cost \> Costing setup \> Cost Type Codes**. Use the buttons on Action Pane to create a new cost type code, edit existing codes, or delete a selected cost type. The following table describes the settings available for each cost type code.

| Setting | Description |
| --- | --- |
| **Cost type code** | Enter a name for the cost type code. |
| **Description** | Enter a description of the cost type code. |
| **Use shipping rate** | Set to *Yes* if the voyage exchange rate (sometimes referred to as a management rate) must be used to calculate the value of these costs. This means that instead of the standard default or spot exchange rate, the shipping rate will be used to exchange foreign-currency invoices. |
| **Reporting category** | Establishes a reporting category for the cost type. Reports can be printed either by reporting categories or by cost type. |
| **Debit Type** | Select whether this cost type will debit the *Item*, *Ledger account* or *Vendor*. |
| **Debit Posting** | When **Debit type** is set to *ledger account*, select the posting description. |
| **Debit Account** | When **Debit type** is set to *ledger account*, select the ledger account to use. |
| **Credit Type** | Select whether this cost type will credit the *Item*, *Ledger account* or *Vendor*. |
| **Credit Posting** | When **Credit type** is set to *ledger account*, select the posting description. |
| **Credit Account** | When **Credit type** is set to *ledger account*, select the ledger account to use. |
| **Clearing account** | Select the clearing account for this cost type. We recommend specifying a separate clearing account per cost type to assist with reconciliation. |
| **Standard cost Posting type** | If you are using standard costing, select the posting description. |
| **Standard cost variance account** | If you are using standard costing, the account specified here will be used to post any variance. It uses the landed cost breakdown on the **Item prices** page. This is created using the periodic routine to update prices. Consider the following example:<p>Item standard cost = $15.00</p><p>FOB = $13.00</p><p>Freight = $2.00</p><p>When the invoice is received for the stock, the item is received in at $15.00, but there is a standard price variance of $2.00 for the item because the actual FOB is $13.00. This is posted to the standard price variance account set up in the item posting profile. The estimated freight is $2.00, so at the time of posting the stock invoice there is no variance. However, when the invoice for freight is received, it is $2.50 per unit, so a $0.50 variance is therefore posted to the specified cost. |
| **Moving average variance account** | If you are using moving average costing, the account specified here will be used to post any variance. Consider the following example:<p>The estimated Freight is $2.00, however when the invoice for freight is received, it is $2.50 per unit, so a $0.50 variance therefore must be posted.</p><p>When **Post adjustments as variance** is set to *Yes* on the **Landed cost parameters** page, all variances between estimated and actual shipment costs will be posted to the moving average variance account specified here. When **Post adjustments as variance** is set to *No*, standard functionality will be used, and the variance will be applied either to inventory or to the moving average variance accounts specified here. This is dependent on stock on-hand. |
| **Charge accrual account** | Select the account used to accrue for cost estimates when posting the purchase invoice. This is only used when **Use cost type charge accrual account** is set to *Yes* on the **Landed cost parameters** page (**General** tab, **Costing** FastTab). |
| **Charge account** | Select the account used to capture the inbound transportation costs that have been invoiced by a supplier. The amount is posted as a debit. The offset account is the stock variation account. This posting will only be used when **Post to charge account in ledger** is set to *Yes* on the **Accounts payable parameters** page. |
| **Variance account** | This field is the account which will be used to offset the charge accruals when posting the purchase invoice. This is only used when **Use cost type charge accrual account** is set to *Yes* on the **Landed cost parameters** page (**General** tab, **Costing** FastTab). |

## Vendor cost type groups

Vendor cost type groups help determine how *auto cost* charges are found and applied to a voyage. Vendors with similar import costs are linked together. For example, all vendors from emerging markets pay the same percentage duty for the same type of product purchased from an established market.

You can maintain vendor cost type groups by going to **Landed cost \> Costing setup \> Vendor Cost type groups**. This page provides a grid that lists existing vendor cost type groups. Its Action Pane provides commands for adding, removing, and editing rows in the grid. The following table describes the settings available for each row.

| Setting | Description |
| --- | --- |
| **Vendor cost type groups** | Enter a unique name for the vendor cost type group (such as *Emerging markets*). |
| **Description** | Enter a description of the vendor cost type group. This description can provide details as to the level or type of charge associated to the vendor group. |

## Item cost type groups

Item cost type groups help determine how *auto cost* charges are found and applied to a voyage. Similar items are linked together. For example, all items with a duty rate of 5% will belong to a certain cost type group.

You can maintain item cost type groups by going to **Landed cost \> Costing setup \> Item cost type groups**. This page provides a grid that lists existing item cost type groups and its Action Pane provides commands for adding, removing, and editing rows in the grid. The following table describes the settings available for each row.

| Setting | Description |
| --- | --- |
| **item cost type groups** | Enter a unique name for the item cost type group (such as *Duty 5%*). |
| **Description** | Enter a description of the item cost type group. This description can provide details as to the level or type of charge associated to the item group. |

> [!NOTE]
> Item cost type is linked to the item through its **Released product** page (**Purchase** FastTab, **Cost type group** field).

## Transfer order cost type groups

Transfer order cost type groups help determine how *auto cost* charges are found. Similar items are linked together. For example, all items with a duty rate of 7% may belong to a certain cost type group.

You can maintain transfer order cost type groups by going to **Landed cost \> Costing setup \> Transfer order cost type groups**. This page provides a grid that lists existing transfer order cost type groups. Its Action Pane provides commands for adding, removing, and editing rows in the grid. The following table describes the settings available for each row.

| Setting | Description |
| --- | --- |
| **Transfer order cost type groups** | Enter a unique name for the transfer order cost type group (such as *Duty 7%*). |
| **Description** | Enter a description of the transfer order cost type group. This description can provide details as to the level or type of charge associated to the transfer order cost type group. |

> [!NOTE]
> Item cost type is linked to the item through its **Released product** page (**Purchase** FastTab, **Transfer order cost group** field).

## Cost templates

Use cost templates to set default values for settings that the user getting the estimate cost may not necessarily know. Cost templates can be a method of reducing complexity in the estimating process by minimizing the selections that users need to specify to get an accurate estimate.

To work with cost templates, go to **Landed cost \> Costing setup \> Cost templates**. This page provides a list pane that shows each existing cost template. Its Action Pane provides commands for adding, removing, and editing templates in the list. The following table describes the settings available for each template.

| **Field** | **Description** |
| --- | --- |
| **Cost template** | Enter a unique name for the cost template. It typically describes the factor or cost multiplier for the cost template. |
| **Description** | Enter a description of the cost template. |
| **Shipping company** | Select the vendor account of the shipping company to associate with the cost template. |
| **Mode of delivery** | Select the mode of delivery used by this cost template when calculating the estimated cost of an item. This will assist in determining the auto costs associated to the goods on the cost estimate. |
| **Shipping container type** | Select the shipping container type to associate with the cost template. This will assist in determining which auto costs are associated to the goods during a cost estimate. |
| **Customs broker** | Select the customs broker (vendor) to associate with the cost template. This will assist in determining which auto costs are associated to the cost estimate. |
| **Factor** | Enter a factor to apply to the final cost estimate of goods. For example, if you would like to add 10% to the calculated cost estimate, enter *1.10* in this field. |

## Volumetric divisors

Volumetric divisors are used to calculate the volumetric weight. Each shipping/freight company formulates its own volumetric divisors. In addition, they normally use a different divisor depending on the mode of delivery (for example, air and sea are often quite different). These same companies can also further complicate their rules depending on where they are shipping from.

For example, consider a package sent by air with a volume of 3 cubic meters. The company charges by volumetric weight, and apply a volumetric divisor is 6, which is multiplied by the volume to find the volumetric weight. Therefore their calculation is 3 x 6 = 18 kg (volumetric weight).

To set up volumetric divisors, go to **Landed cost \> Costing setup \> Volumetric divisors**. This page provides a grid that lists existing volumetric divisors. Its Action Pane provides commands for adding, removing, and editing rows in the grid. The following table describes the settings available for each row.

| Setting | Description |
| --- | --- |
| **Shipping company** | Select the vendor account of the shipping company associated with this volumetric divisor. |
| **Cost type code** | Select the cost type code associated with this volumetric divisor. Use this setting to place cost types into reporting buckets. Reports can either be printed by reporting categories or by cost type. |
| **From port** | Select the from port for which this volumetric divisor applies. |
| **Volumetric divisor** | Enter the volumetric divisor value that applies for this row. The value entered here will *multiplied* by the volume of each package to find that package's volumetric weight. |
