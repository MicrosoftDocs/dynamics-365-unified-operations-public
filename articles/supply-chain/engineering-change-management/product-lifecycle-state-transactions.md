---
# required metadata

title: Product lifecycle states and transactions
description: This topic explains how you can control which transactions are allowed for each lifecycle state as an engineering product goes through its lifecycle.
author: t-benebo
manager: tfehr
ms.date: 09/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: EngChgEcoResProductLifecycleStateChange
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-09-28
ms.dyn365.ops.version: Release 10.0.15
---

<!-- Beatriz: note that the topic that the reference to the product lifecycle state in the doc page refers to 
 https://docs.microsoft.com/dynamics365/supply-chain/pim/product-lifecycle. Note that the topic cannot be merged with the topic above as this topic needs to be under a Product engineering section. All the topics for the product engineering need to be under a product engineering section (as it happens with other add-ins) so it is clear that this only applies if the customer gets the add-on. -->

# Product lifecycle states and transactions

[!include [banner](../includes/banner.md)]

As an engineering product goes through its lifecycle, it's important that you be able to control which transactions are allowed for each lifecycle state. For example, products that aren't yet in a mature state should not be put on a sales order. Alternatively, if a product is reaching its end-of-life state, you might want to control the inflow of that product.

For an engineering product, changes to the lifecycle state are connected to the product's engineering versions. Therefore, the product's lifecycle state can also be connected to its engineering versions. When the product lifecycle state is connected to an engineering version, you can use the lifecycle state to control which transactions are allowed for the engineering version.

## Create and manage product lifecycle states

To work with product lifecycle states, go to **Engineering change management \> Setup \> Product lifecycle state**. Then follow one of these steps.

- To create a new lifecycle state, select **New** on the Action Pane, and then set the fields as described in the following subsections.
- To edit an existing lifecycle state, select it in the list pane, select **Edit** on the Action Pane, and then set the fields as described in the following subsections.
- To delete an existing lifecycle state, select it in the list pane, and then select **Delete** on the Action Pane.

> [!NOTE]
> Engineering products use the same product lifecycle states as standard (non-engineering) products. You can also open the **Product lifecycle state** page that is described in this topic by going to **Product information management \> Setup \> Product lifecycle state**. For more information about product lifecycle states, for both engineering products and standard products, see [Product lifecycle state overview](../pim/product-lifecycle.md).

### Header

Set the following fields on the header of a product lifecycle state.

| Field | Description |
|---|---|
| State | Enter a name for the product lifecycle state. |
| Description | Enter a description of the product lifecycle state. |

### General FastTab

Set the following fields on the **General** FastTab.

| Field | Description |
|---|---|
| Default when released to a legal entity | For standard products, set this option to *Yes* if this lifecycle state should be applied to all products by default when they are first released. Set it to *No* if this lifecycle state will be manually applied later.<p>This setting isn't applicable to engineering products. The lifecycle state of an engineering product version after it's created in the engineering legal entity that is specified in its engineering change category. When the product is released to another legal entity, the lifecycle state of the product is copied. In other words, when an engineering product is released in a legal entity, it has the same lifecycle state that it had in the engineering legal entity. The lifecycle state can be overwritten in the company.</p> |
| Is active for planning | Set this option to *Yes* to include products that are in this lifecycle state in calculations at the master planning and bill of materials (BOM) levels. Set it to *No* to exclude products that are in this lifecycle state from the calculations. |

### Enabled business processes FastTab

Use the **Enabled business processes** FastTab to control which of the available business processes can be used with products in the current lifecycle state. The processes that are listed on this FastTab are automatically found in the following way:

- The first time that you save a new lifecycle state, the page loads the business processes that are currently available.
- If you add new business processes to your system, you can update the list on the **Enabled business processes** FastTab for an existing lifecycle state by selecting **Check for updates** on the Action Pane.

The following fields are available for each process that is listed on the **Enabled business processes** FastTab.

| Field | Description |
|---|---|
| Process | This read-only field shows the name of an existing business process. |
| Process area | This read-only field shows the name of an existing process area. |
| Policy | Select one of the following values to control whether and how the current process will be permitted for products that are in this lifecycle state:<ul><li>**Enabled** – The business process is allowed.</li><li>**Blocked** – The process isn't allowed. If a user tries to use the process on a product that is in this lifecycle state, the system will block the attempt and show an error instead. For example, you might block end-of-life products from being purchased.</li><li>**Enabled with warning** – The process is allowed, but a warning will be shown. For example, you might want a prototype product to be put on a production order that is created by the Research and Development department. However, other departments should be aware that they should not produce the product yet.</li></ul> |

If you're adding more lifecycle state rules as a customization, you can view those rules in the user interface (UI) by selecting **Refresh processes** in the upper pane. The **Refresh processes** button is available only to administrators.
