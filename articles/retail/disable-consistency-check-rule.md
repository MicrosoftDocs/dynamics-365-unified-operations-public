---
# required metadata
title: Disable rules in retail transaction consistency checker
description: This topic describes the functionality for disabling retail transaction consistency checker rules in Microsoft Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 09/13/2019
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
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 

---

# Disable rules in retail transaction consistency checker 

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

Because most retailers have specific business scenarios and processes that are unique to them, not all of the retail transaction consistency checker rules that are shipped in the product are applicable. Because of this, we've introduced functionality that retailers can use to disable the rules that are not applicable to them.

On the **Retail > Headquarters setup > Parameters > Retail parameters** page, the **Transaction validation** tab can be used to see the list of retail transaction consistency checker rules that are available in their environment and the status of the rules. 

By default, all the rules are set to **Enabled**, so all the rules will be used to validate retail transactions before they are pulled into the retail statements. To disable individual rules, set the status for the rule to **Disabled**. Disabled rules are not considered in the validation run of the retail transactions during the statement calculation process. 

To bypass the entire validation process regardless of which rules are enabled, go to **Retail > Headquarters setup > Parameters > Retail parameters** page and set the **Disable consistency checker for Retail transactions** parameter to **On**. Once this parameter is turned off, it will not be possible to turn it on again from the UI. <!--- this last sentence is confusing. need to check with Anil. --->

