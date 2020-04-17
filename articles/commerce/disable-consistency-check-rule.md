---
# required metadata
title: Disable rules in the retail transaction consistency checker
description: This topic describes the functionality for disabling transaction consistency checker rules in Microsoft Dynamics 365 Commerce.
author: josaw1
manager: AnnBe
ms.date: 10/15/2019
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

# Disable rules in the retail transaction consistency checker 

[!include [banner](../includes/banner.md)]

Retailers can have business scenarios and processes that are unique to them. Therefore, not all the rules that are included by default in the commerce transaction consistency checker are applicable to all retailers. To accommodate differences, Microsoft Dynamics 365 Commerce provides functionality that can be used to disable the rules that aren't applicable.

To view the list of rules that are available in the transaction consistency checker in your environment, and to see the status of each rule, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**, and select the **Transaction validation** tab.

By default, the status of every rule is set to **Enabled**. Therefore, all the rules are used to validate transactions before they are pulled into the commerce statements. To disable a rule, change its status to **Disabled**. Disabled rules aren't considered when transactions are validated during the statement calculation process.

To bypass the whole validation process, regardless of the rules that are enabled, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**, and then, on the **Transaction validation** tab, set the **Disable consistency checker for Commerce transactions** option to **Yes**. After this option is set to **No**, it can't be set back to **Yes** from the user interface (UI).
