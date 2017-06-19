---
# required metadata

title: Purchase duties | Microsoft Docs
description: A purchase duty is a tax on incoming sales tax and is calculated as a percentage of the paid sales tax. This topic is related to a specific functionality extension that applies to legal entities in Austria.
author: neserovleo
manager: AnnBe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Austria
# ms.search.industry: 
ms.author: v-lenest
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Enterprise edition, July 2017 update

---

# Purchase duties for Austria

A purchase duty is a tax on incoming sales tax and is calculated as a percentage of the paid sales tax. This topic includes information about purchase duties for legal entities that have their primary address in Austria. For more information about the global sales tax functionality, see [Sales tax overview](../general-ledger/indirect-taxes-overview.md).

The calculation of purchase duties is based on sales tax codes. To include a sales tax code in the purchase duty calculation, select the **Purchase duty** check box on the **Saxes tax codes** page. 

You can specify purchase duty settings on the **Tax setup** menu on the **Purchase duty** page. You can set the duty identifier (for example, **KU**), description, tax authority, and accounts that will be used for posting. Duty account is a balance account where the liability for the purchase duty is registered. Cost account is a profit and loss account that the costs are posted to and a settle account.

To specify the value of the purchase duty, click **Purchase duty value** to open the **Purchase duty value** page. You can specify the purchase duty percentage (for example **0,30**) for the required period.

Purchase duties are generated when you settle and post sales taxes. You can generate the **Purchase duty** report from the **Purchase duty reporting** menu.
