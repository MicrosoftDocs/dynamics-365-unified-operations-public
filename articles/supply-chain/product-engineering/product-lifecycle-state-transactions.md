---
# required metadata

title: Product lifecycle state and transactions
description: When an engineering product traverses through its lifecycle, it's important that you can control which transactions are allowed per lifecycle state. As an example, when products aren't yet in a mature state, they shouldn't be put on a sales order and on the other end, if a product is reaching its end-of-life state, you want to ensure that the inflow of this product can be controlled.
author: t-benebo
manager: tfehr
ms.date: 07/31/2020
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
ms.author: benebotg
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Release 10.0.13
---

<!-- Beatriz: note that the topic that the reference to the product lifecycle state in the doc page refers to 
 https://docs.microsoft.com/dynamics365/supply-chain/pim/product-lifecycle. Note that the topic cannot be merged with the topic above as this topic needs to be under a Product engineering section. All the topics for the product engineering need to be under a product engineering section (as it happens with other add-ins) so it is clear that this only applies if the customer gets the add-on. -->

# Product lifecycle state and transactions

[!include [banner](../includes/banner.md)]

As an engineering product traverses through its lifecycle, it's important that you can control which transactions are allowed per lifecycle state. For example, when products aren't yet in a mature state, they shouldn't be put on a sales order and on the other end, when a product is reaching its end-of-life state, you want to control the inflow of this product.

For an engineering product, changing the lifecycle state goes hand-in-hand with its engineering versions and therefor the product lifecycle state can also be connected to its engineering versions. When the product lifecycle state is connected to an engineering version, you can control what transactions are allowed for this engineering version via its product lifecycle state.

## Create and manage product lifecycle states

To work with product lifecycle states, go to **Project Oaktree \> Setup \> Product lifecycle state**. Then do one of the following:

- To create a new lifecycle state, select **New** from the Action Pane and then make settings as described in the following sections.
- To edit an existing lifecycle state, select it from the list pane, select **Edit** on the Action Pane, and then make settings as described in the following sections.
- To delete an existing lifecycle state, select it from the list pane and then select **Delete** on the Action Pane.

> [!NOTE]
> Engineering products use the same product lifecycle states as standard products. You can also open the **Product lifecycle state** page described in this topic by going to **Product information management \> Setup \> Product lifecycle state**. For more information about product lifecycle states, both for engineering and non-engineering products, see [Product lifecycle state overview](../pim/product-lifecycle.md).

## Settings in the header

Make the following settings in the header of a product lifecycle state:

| Setting | Description |
| --- | --- |
| **State** | Enter a name for the product lifecycle state. |
| **Description** | Enter a description of the product lifecycle state. |

## The General FastTab

Make the following settings on **General** FastTab:

| Setting | Description |
| --- | --- |
| **Default when released to a legal entity** | This setting is not applicable for engineering products. The lifecycle state of an engineering product version after creation in the engineering legal entity is the specified in its engineering change category. When the product is released to another legal entity, the lifecycle state for the product copied. In other words, when the engineering product is released in a legal entity it will have the same lifecycle state as it had in the engineering legal entity. It can be overwritten at the company. For standard products: Set to *Yes* if this state should be applied by default for all products when they are first released. Set to *No* for states that will be manually applied later. |
| **Is active for planning** | Set this to *Yes* to include products in this state in master planning and BOM-level calculations. Set to *No* to exclude products in this state from those calculations. |

## The Enabled business processes FastTab

Use **Enabled business processes** FastTab to control which of the available business processes can be used with products in the current lifecycle sate. The processes listed here are found automatically as follows:

- The first time you save a new lifecycle state, the page loads the business processes that are currently available at that time.
- If you add new business processes to your system, you can refresh the list on the **Enabled business processes** FastTab for an existing lifecycle state by selecting **Check for updates** on the Action Pane.

For each process listed here, make the following settings:

| Setting | Description |
| --- | --- |
| **Process** | This read-only value shows the name of an existing business process. |
| **Process&nbsp;area** | This read-only value shows the name of an existing process area. |
| **Policy** | Set this to one of the following to control whether and how the current process will be permitted for products in the current lifecycle state:<ul><li>**Enabled** - Allow this business process.</li><li>**Blocked** - The process is not allowed. If a user attempts to use this process on a product in this lifecycle state, the system will block it and show an error instead. For example, you might block end-of-life products from being purchased.</li><li>**Enabled with warning** - The process is allowed, but a warning will be shown. For example, you might want a prototype product to be put on a production order created by the research and development department, but other departments should be aware that they should not produce the product yet.</li></ul> |

If you are customizing by adding more lifecycle state rules, you will be able to view those rules in the UI using the button **Refresh processes** in the top pane. You need to be an administrator to have access to the Refresh processes button.
