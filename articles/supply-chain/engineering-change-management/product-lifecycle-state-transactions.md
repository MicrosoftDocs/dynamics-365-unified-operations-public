---
# required metadata

title: Product lifecycle states and transactions
description: This topic explains how you can control which transactions are allowed for each lifecycle state as an engineering product goes through its lifecycle.
author: t-benebo
ms.date: 02/17/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EngChgEcoResProductLifecycleStateChange
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-09-28
ms.dyn365.ops.version: 10.0.15
---

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
| Default when released to a legal entity | For standard products, set this option to *Yes* if this lifecycle state should be applied to all products by default when they are first released. Set it to *No* if this lifecycle state will be manually applied later.<p>This setting isn't applicable to engineering products. The lifecycle state of an engineering product version after it's created in the engineering company is specified in its engineering change category. When the product is released to an operational company, the lifecycle state of the product is copied. In other words, when an engineering product is released to an operational company, it has the same lifecycle state that it had in the engineering company. The lifecycle state can be overwritten in the operational company.</p> |
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

## Lifecycle states for released products and product variants

For a product that has variants (master and variants), the product (master) will have a lifecycle state and each of the variants can also have a different lifecycle state.

For specific processes, if either the variant or the product is blocked, then the process will also be blocked. Specifically, to determine whether a process is blocked, the system will make the following checks:

- For engineering-controlled products:
  - If the current engineering version is blocked, then block the process.
  - If the current variant is blocked, then block the process.
  - If the released product is blocked, then block the process.
- For standard products:
  - If the current variant is blocked, then block the process.
  - If the released product is blocked, then block the process.

For example, suppose you only want to sell one variant (red) of a given product (t-shirt) and block sales of all other variants for now. You could implement this using the following setup:

- Assign the product a lifecycle state that allows the process. For example, assign the t-shirt product a lifecycle state of *Sellable*, which allows the *Sales order* business process.
- Assign the sellable variant a lifecycle state that allows the process. For example, also assign the red variant a lifecycle state of *Sellable*.
- All other variants be assigned another lifecycle state where the process is blocked. For example, assign the white variant (and all other variants) a lifecycle state of *Not sellable*, which blocks the *Sales order* business process.

## Default product lifecycle states

The default lifecycle state for an engineering version is specified by its engineering category. The state will be defaulted when you create a new engineering version, including the first version of a new product.

When you create a new product or engineering product, you can also set the default lifecycle state by specifying it on the template released product of the release policy assigned to the product.

In this case, it's possible for the product to have a different lifecycle state than the version when you create a new engineering product.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
