---
# required metadata
title: Disable retail transaction consistency checker rules
description: This topic describes the feature of disabling retail transaction consistency checker rules in Microsoft Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 8/29/2019
ms.topic: index-page
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata
# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-08-29
ms.dyn365.ops.version: 

---

# Disable retail transaction consistency checker rules 

This topic describes the capability to disable individual rules for retail transaction consistency checker introduced in Microsoft Dynamics 365 for Finance and Operations version 10.0.6. 

Every retailer have specific business scenarios and processes that are unique to them and as such not all of the retail transaction consistency checker rules that are shipped in the product might be applicable to every retailer. Given this, with this feature, retailers can now choose to disable the rules that are not applicable to them.

A new tab has been introduced in the **Retail parameters** form under the path **Headquarters setup > Parameters > Retail parameters** called as **Transaction validation**  wherein the user can see the list of retail transaction consistency checker rules that are available in their environment and their status. 

By default, all the rules are set to an **Enabled** status which denotes that by default all the rules will be used to validate the retail transactions before they are pulled into the retail statements. To disable individual rules, the user will have to set the respective rule status to **Disabled**. Disabled rules are not considered in the validation run of the retail transactions during the statement calculation process. 

In addition to the status on the individual rules, an additional parameter called as **Disable consistency checker for Retail transactions** has been introduced on the same form, which when turned on will bypass the entire validation process irrespective of the rule status during the statement calculation process.

