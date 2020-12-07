---
# required metadata

title: Set up Landed cost parameters
description: Supply Chain Management provides two different modules for working with transportation (Transportation management (TMS) and Landed cost). This topic summarizes the functionality the two modules have in common and highlights the differences between them.
author: mkirknel
manager: tfehr
ms.date: 12/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mkirknel
ms.search.validFrom: 2020-12-07
ms.dyn365.ops.version: Release 10.0.17
---

# Landed cost parameters

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The **Landed cost parameters** page sets up general information and configuration settings used across the module for posting, status updates, number sequences, and behavior. The parameters setup is shared across legal entities and can be modified by an administrator.

## Open the Landed cost parameters

To work with the setup parameters, go to **Landed cost \> Setup \> Landed cost parameters**, and then make settings as described in the following subsections.

![The Landed cost parameters page](media/landed-cost-parameters.png "The Landed cost parameters page")

## The General tab
<!--KFM: Note that none of the fields on this page provide tooltips. We should consider reusing the text on this page as tooltips. -->

### The General FastTab

The following table describes the settings available on the **General** FastTab of the **General** tab of the **Landed cost parameters** page.

| Setting | Description |
| --- | --- |
| **Use shipping rate** | The shipping rate is a specified rate for calculating costs of goods using multi-currency. It is set for a defined period and is used to determine estimate costs. Select *Yes* to enable this option. |
| **Exchange rate type** | The default exchange rate used for multi-currency calculations on a voyage and voyage costs. <!--KFM: This doesn't look right. It's an exchange rate *type*, not a rate. What does this do? Where to these values come from? --> |
| **Update purchase order quantity** | Choose what will happen when a user changes the quantity for a purchase order line. Select one of the following values:<ul><li>**Accept** – If the quantity on a purchase order line is altered, it will automatically adjust the shipment quantity.</li><li>**Warning** – If the quantity on a purchase order line is altered, and the line is attached to a shipment, a warning will be shown but the shipment quantity will be updated.</li><li>**Error** – If the quantity on a purchase order line is altered, and the line is attached to a shipment, an error message will be shown and it won't be possible to update the purchase order. Therefore, the order line must first be removed from the shipment.</li></br></ul> |
| **Automatically&nbsp;update number of cartons** | When set to *Yes*, all cartons will be added together and shown at the shipment and container levels. <!--KFM: What happens when this is set to No? --> |

### The Costing FastTab

The following table describes the settings available on the **Costing** FastTab of the **General** tab of the **Landed cost parameters** page.

| **Setting** | **Description** |
| --- | --- |
| **Posting&nbsp;specification** | Select one of the following values to specify the value adjustment in the ledger:<ul><li>**Total** – Posts a total figure to the ledger.</li><li>**Item group** – Specifies the adjustment per item group.</li><li>**Item number** – Provides the most detail.</li></ul> |
| **Allow zero costs** | An error can be given if an expected shipment cost hasn't got a value. This is normally switched on. <!--KFM: It isn't clear what this does ("can be given"?). I think we mean that we should set to "No" to show the error. The text says "this is normally switched on", but I think "switched on" may in this case mean set to "No" (which appears to be the default). What is going on here? --> |
| **Adjustment posting date** | When you post an accounts payable shipment cost invoice, the settlements table (inventory adjustments) will also be updated. This field controls the date set by default on the **Select shipment costs** page while in the invoice journal <!-- KFM: what do we mean by "the **Select shipment costs** page while in the invoice journal"? -->. Choose one of the following values:<ul><li>**Transaction date** – Default to the date of the journal (posting date).</li><li>**Purchase order invoice date** – Default to the financial posting date of the stock (purchase order) invoice.</li><li>**Selected date** – Allow the user to specify a posting date.<!-- KFM: By "allow" do we mean "prompt" or "require? Or can the user leave it blank? --></li></br></ul> |
| **Use purchase invoice voucher** | This setting has an effect when the **Post to charge account in ledger** option is enabled on the **Invoice** tab of the **Accounts payable parameters** page. When this is set to *Yes*, cost accrual transactions will use the same voucher as that used for the purchase invoice. When this is set to *No*, the voucher setup in the ITM number sequences will be used.<!-- KFM: What do we mean by the "ITM number sequences"? How can those be used by this feature? -->|
| **Block manual posting to clearing account** | Set this to *Yes* to prevent posting to clearing accounts where the transaction has not been linked to a shipment using the **Select voyage costs** button. To allow for the shipment and clearing account to be properly settled, we recommend you set this to *Yes*. <!-- KFM: Where is the **Select voyage costs** button? Why might we set this to No? -->|
| **Use cost type charge accrual account** | This setting has an effect when the **Post to charge account in ledger** option is enabled on the **Invoice** tab of the **Accounts payable parameters** page.  When this is set to *Yes*, the account configured on the **Cost type** page will be used to accrue for costs as an expense. <!-- KFM: Where is the **Cost type** page? Do we mean the **Cost type codes** page?-->|
| **Post adjustments as variance** | This setting has an effect when the **Post to charge account in ledger** option is enabled on the **Invoice** tab of the **Accounts payable parameters** page. When this is set to *Yes*, the inventory adjustment transactions related to a variance between the estimated costs and the actual costs are posted to a variance account. <!-- KFM: What if we set this to No? --> |
| **Post adjustments as variance** <!-- KFM: This label is the same as the one as above, and there are no other settings on this FastTab. What is this row for? Should it be combined with the above? --> | This setting is used in conjunction with the moving average costing method. When this is set to *Yes*, all variances between estimate and actual shipment costs will be posted to the moving average variance account. When this is set to *No*, the variance will be applied to either inventory or moving average variance accounts. This is dependent on stock on-hand.</br></br>**Note:** We recommend that you set this to *No* in most situations.</br></br>**Note:** Once this parameter has been set and inventory postings have occurred, you shouldn't change it. <!-- KFM: Should not or must not? What if we do it anyway? --> |

### The Validation FastTab

The following table describes the settings available on the **Validation** FastTab of the **General** tab of the **Landed cost parameters** page.

| **Setting** | **Description** |
| --- | --- |
| **Multiple cost invoices** | This setting pertains to multiple invoices per miscellaneous charge. Choose whether the system should *Accept*, give a *Warning*, or show an *Error* when more than one invoice is processed against a shipment/folio/container for the same miscellaneous charge. <!-- KFM: What do those slashes mean? A unique combo of all three, or any one of those three, or something else? Also, should "container" be "shipping container"? --> |
| **Multiple vendors per folio** | Select *Accept* to allow more than one vendor's purchase orders to be added to a folio. Select *Warning* or *Error* to warn against or prevent this action. Your customs broker or local laws might mandate a specific setting for this option. |
| **Multiple mode of delivery tolerance** | Select *Accept* to allow goods from a purchase order that uses a mode of delivery different from the shipment to be added to that shipment. Select *Warning* or *Error* to warn against or prevent this action. |
| **Multiple warehouse tolerance** | This parameter controls what will happen when goods are attached to a voyage that will be delivered to a different warehouse. <!-- KFM: Different from what? The purchase order? --> Choose whether the system should *Accept* the action, give a *Warning*, or show an *Error*. |
| **Missing weight** | This setting controls what will happen if a user adds an item without a weight to a shipment. Choose whether the system should *Accept* the item, give a *Warning*, or show an *Error*. If weights are used for the calculation and apportionment of costs, we recommend showing a warning or error. <!-- KFM: This setting appears to have been removed. Has it? --> |
| **Missing volume** | This setting controls what will happen if a user adds an item without a volume to a shipment. Choose whether the system should *Accept* the item, give a *Warning*, or show an *Error*. If volumes are used for the calculation and apportionment of costs, we recommend showing a warning or error. |
| **Services provider without voyage cost** | This parameter controls what will happen when an invoice is processed for a service provider without a link to a voyage. <!-- KFM: What do we mean by "processed"? Is that something a user is doing? --> Choose whether the system should *Accept* the action, give a *Warning*, or show an *Error*. We recommend showing a warning. |

### The Defaults FastTab

The following table describes the settings available on the **Defaults** FastTab of the **General** tab of the **Landed cost parameters** page.

| **Setting** | **Description** |
| --- | --- |
| **Journal name** | Select the journal that should be used by the create arrival journal function. |
| **Voyage status** | Select the status that a voyage must have before users can set up a rental shipping container for it in the system. This is normally when the goods are in transit or at the dock. <!-- KFM: Please confirm this description --> |
| **Journey template** | Select the default journey template to use for new rental shipping containers. You will typically select a journey template that includes rental costs. |
| **Movement** | When the over/under quantity for a delivery is within the set tolerance, a movement journal will be processed automatically. Select the movement journal to use. The movement journal name should have a default account number <!-- KFM: Is this true? The demo data doesn't do this. -->. |
| **Transfer** | When an under delivery is processed, the short receipt quantity will be transferred to an under-delivery warehouse. Select the transfer journal to use for this. |
| **Disable non-voyage purchase orders** | Disable Landed cost over/under delivery functionality for purchase orders not attached to a shipment. |
| **Disable non goods in transit purchase orders** | Disable Landed cost over/under delivery functionality for purchase orders that do not use goods in transit functionality. |
| **Goods in transit over receipt grace period** | Specify the number of days following the first receipt of a shipping container that further over receipts can be completed via radio frequency. <!-- KFM: What do we mean by "radio frequency"?. -->  |

## The Status updates tab

The system uses status values to mark the status of each voyage. You can create as many voyage status values as you like but four of them must be marked as used for a special purpose, as defined on the **Status updates** tab of the **Landed cost parameters** page. The following table describes the settings available here. <!-- KFM: Maybe add link to topic about how to create these values -->

Voyage status values can be applied to voyages automatically via voyage tracking or periodic batch jobs, or manually by opening the voyage and then, on the Action Pane, opening the Manage tab and selecting a status from the **Voyage update** group.

| **Setting** | **Description** |
| --- | --- |
| **Costed** | Select the voyage status that identifies a voyage as having been finalized. |
| **In transit** | Select the voyage status that identifies a voyage as being in transit. |
| **Ready for costing** | Select the voyage status that identifies a voyage as being ready for costing. The purpose of this status is to set all those voyages that have had all stock purchase invoices and voyage cost invoices processed where the **Credit on the voyage cost** is *Vendor*. Voyages that fail the costed process will show a *Ready for costing* status.|
| **Pre-costed** | Select the voyage status that identifies a voyage as being pre-costed. The pre-costed status is used when a shipment has a new cost transaction added after it has been costed. This sometimes occurs when a second freight invoice or unexpected demurrage charge has been received. This status will be applied automatically when a new voyage cost is added to a costed voyage. |

## The Voyage creator tab

The following table describes the sections provided on the **Voyage creator** tab of the **Landed cost parameters** page.

| **Section** | **Description** |
| --- | --- |
| **Tolerances** | The **Outside volume tolerance** and **Outside weight tolerance** settings establish thresholds beyond which the system will warn that the goods are overweight or over volume when a user adds them using the **Shipment creator** page. <!-- KFM: Where is this page? Should it be "Voyage creator"? --> We recommend setting this somewhere between 5% and 10% of the volume or weight.<!-- KFM: What are these percentages of? --> |
| **Folio creation setup** | The system is able to create multiple folios during the voyage creation process. Use this section to determine when a new folio should be created. The three table options are purchase order, purchase lines and inventory dimensions. <!-- KFM: I don't understand this at all. There seems to be more than three table options here. What do the field settings do? --> |

## The Cost estimates tab

The **Cost estimates** tab of the **Landed cost parameters** page provides just one setting: **Default costing version**. This applies when the costing method is *standard costing*. Select a costing version to use by default for the *Item cost price update* periodic task. You may need to change this setting each time a new financial year occurs.

## The Inventory dimensions tab

For each of the inventory dimensions displayed on the **Inventory dimensions** tab of the **Landed cost parameters** page, select *Yes* or *No*. This selection will default the view on the **Voyage Lines** , **Goods in transit orders** , **Cost estimate** and **Auto cost** pages, but can be overwritten by changing the selection on **Voyage form \> Inventory (Action) Options \> Inventory dimension per user**. The settings here establish the default across legal entities for each designated form.

<!-- KFM: This makes no sense at all to me. What is going on here? Where is **Voyage form \> Inventory (Action) Options \> Inventory dimension per user**? -->

## The Number sequences tab

The **Number sequences** tab lists each type of reference number sequence required by Landed cost but not shared across legal entities. For each listed **Reference**, select a **Number sequence code** to use for that purpose.

> [!NOTE]
> In a multi-company configuration, different number sequences must be created for each company (legal entity).

## The Shared number sequences tab

The **Shared number sequences** tab lists each type of reference number sequence that is shared across legal entities for the Landed cost module. 

There is currently just one number sequence in this category, which sets the voyage ID. The **All voyages** page lets users view all voyages across all legal entities, but to edit and process a voyage, the user will need to be in the legal entity of the record selected.

## The Feature visibility tab

The Landed cost module adds fields and functions to several commonly used pages in Supply Chain Management, including pages related to vendor master data, released products, purchase orders, transfer orders, warehouse setup, and more. If you are using the Landed cost module, then you must make these features visible everywhere to benefit from them. If you don't use the module, then you can hide these features to keep them out of the way.

On the **Feature visibility** tab of the **Landed cost parameters** page, set **Activate** to *Yes* to make Landed cost features visible everywhere they are available. Select *No* to hide them on common pages outside of the Landed cost module (though the module itself, including the **Landed cost parameters** page, will remain available to users with the right permissions to access it). <!-- KFM: Please confirm this. -->