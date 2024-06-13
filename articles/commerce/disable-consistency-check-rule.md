---
# required metadata
title: Disable rules used in the transaction validation process
description: This article describes the functionality for disabling transaction validation rules in Microsoft Dynamics 365 Commerce.
author: analpert
ms.date: 12/11/2021
ms.topic: conceptual
# optional metadata
# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 

---

# Disable rules used in the transaction validation process

[!include [banner](../includes/banner.md)]

Retailers can have business scenarios and processes that are unique to them. Therefore, not all rules that are included in the commerce transaction validation process are applicable to all retailers. To accommodate differences, Microsoft Dynamics 365 Commerce provides functionality that can be used to disable rules that aren't applicable.

To view the list of rules that are available in the transaction validation process in your environment, and to see the status of each rule, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters** and select the **Transaction validation** tab. All enabled rules are used to validate transactions during the **Validate store transactions** process and must pass for transactions to be collected and posted on a transactional statement.

By default, the status of every rule is set to **Enabled**. Therefore, all the rules are used to validate transactions before they can be pulled into the commerce transactional statements. To disable a rule, change its status to **Disabled**. Disabled rules aren't considered when transactions are validated during **Validate store transactions** process.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
