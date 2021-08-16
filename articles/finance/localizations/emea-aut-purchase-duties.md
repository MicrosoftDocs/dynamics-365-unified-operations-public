---
# required metadata

title: Purchase duties
description: This topic provides information about purchase duties in Austria.
author: ShylaThompson
ms.date: 07/21/2021
ms.topic: article
ms.prod: 
ms.technology: 


# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Austria
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Purchase duties

A purchase duty is a tax on incoming sales tax. It's calculated as a percentage of the paid sales tax. Purchase duties are calculated for legal entities that have a primary address in Austria.

The calculation of purchase duties is based on sales tax codes. To include a sales tax code in the purchase duty calculation, select the **Purchase duty** checkbox on the **Sales tax codes** page.

You can specify a purchase duty by selecting **Tax setup** on the **Purchase duty** page. You can set the duty identifier (for example, **KU**), description, tax authority, and posting accounts. The duty account is a balance account where the liability for the purchase duty is registered. The cost account is a profit and loss account that the costs are posted to. A settle account is an account where the settlement transactions are generated.

To specify the value of the purchase duty, select **Purchase duty value** to open the **Purchase duty value** page. You can specify the purchase duty percentage for the required period.

Purchase duties are generated when you settle and post sales taxes. You can generate the **Purchase duty** report from the **Purchase duty reporting** menu.

For more information about global sales tax functionality, see [Sales tax overview](../general-ledger/indirect-taxes-overview.md).
