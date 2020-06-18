---
# required metadata

title: Product lifecycle state and transactions
description: When an engineering product traverses through its lifecycle, it's important that you can control which transactions are allowed per lifecycle state. As an example, when products aren't yet in a mature state, they shouldn't be put on a sales order and on the other end, if a product is reaching its end-of-life state, you want to ensure that the inflow of this product can be controlled.
author: XXXX
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
 https://docs.microsoft.com/en-us/dynamics365/supply-chain/pim/product-lifecycle. Note that the topic cannot be merged with the topic above as this topic needs to be under a Product engineering section. All the topics for the product engineering need to be under a product engineering section (as it happens with other add-ins) so it is clear that this only applies if the customer gets the add-on. -->

# Product lifecycle state and transactions

When an engineering product traverses through its lifecycle, it's important that you can control which transactions are allowed per lifecycle state. As an example, when products aren't yet in a mature state, they shouldn't be put on a sales order and on the other end, if a product is reaching its end-of-life state, you want to ensure that the inflow of this product can be controlled.

For an engineering product, changing the lifecycle state goes hand-in-hand with its engineering versions and therefor the product lifecycle state can also be connected to its engineering versions. When the product lifecycle state is connected to an engineering version, you can control what transactions are allowed for this engineering version via its product lifecycle state. For more information, see [Product lifecycle state overview](../pim/product-lifecycle.md).

<!-- KFM: Where are we? I think we need a nav path. -->

Next to the **Is active for planning** check box, the following transactions can be controlled by the product lifecycle state:

<!-- KFM: Are the bolded terms below literal UI text? If not, maybe set in italic, and also spell out all abbreviations. -->

- Entering the product on a **sales quotation**
- Entering the product on a **sales order**
- Generating a **sales picking list** for the product
- Creating **WBS estimates for items** for the product
- Entering **item forecast** for the product
- Creating a **production order** for the product
- Reporting the product **BOM report as Finished**
- Adding the product to the **production BOM**
- Generating **production picking list** for the product
- Entering the product on an **inventory transfer**
- Entering the product on **inventory journals**
- Entering the product on an **inventory movement** journal
- Entering the product on an **inventory adjustment** journal
- Entering the product on a **purchase order**
- Entering the product on **request for quote**

You can extend these rules by creating extensions. To make them appear in the user interface, use the button **Check for updates**.

There are three options for each transaction:

- **Enabled** - This is the default value where the transaction is allowed. As an example, you can use a matured operational product on all transactions.
- **Blocked** - The transaction is not allowed and will be blocked, you will get an error. As an example, you want to block an end-of-life product from being purchased
- **Enabled with warning** - The transaction is allowed, but you will receive a warning. As an example, you want a prototype product to be put on a production order by the research and development department, but other departments should be aware that they should not produce the product yet.