---
# required metadata

title: Purchase duties | Microsoft Docs
description: A purchase duty is a tax on incoming sales tax and is calculated as a percentage of the paid sales tax. This article is related to a specific functionality extension applicable for legal entities in Austria.
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

A purchase duty is a tax on incoming sales tax and it is calculated as a percentage of the paid sales tax.
This topic includes information about purchase duties for legal entities with a primary address in Austria. For more details about global sales tax functionality, see [Sales tax overview](../general-ledger/indirect-taxes-overview.md).

Purchase duty calculation is based on the sales tax codes. To include a sales tax code in the purchase duty calculation, select the **Purchase duty** checkbox on the **Saxes tax codes** page. 

You can specify purchase duty settings on the **Purchase duty** page in the **Tax Setup** menu. You can set the duty identification (i.e. KU), description, Tax authority and accounts which will be used for posting: Duty account is a balance account in which the liability for the purchase duty is registered, Cost account is a Profit and Loss account to which the costs are posted and a Settle account.

To specify the purchase duty value, click the **Purchase duty value** button to open the **Purchase duty value** page. You can specify the purchase duty percent (i.e. 0,30) for the required period.

Purchase duties will be generated when you settle and post sales taxes. You can generate the**Purchase duty** report from the **Purchase duty reporting** menu.


