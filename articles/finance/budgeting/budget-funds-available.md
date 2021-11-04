---
# required metadata

title: Budget funds available feature
description: This topic introduces the budget funds available feature and provides information to help you configure budget control to optimize management of your organization's financial resources.
author: rcarlson
ms.date: 11/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BudgetControlConfiguration
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: ["60493", "intro-internal"]
ms.assetid: be964167-43bc-431d-9adb-48bff32d68d5
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2021-11-28
ms.dyn365.ops.version: AX 10.0.24

---

# Budget Funds Available 

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

#### Enhanced calculation feature for budget funds available.

The **Only track amounts in the budget funds available calculation** feature lets you tracki the underlying budget control tables for document types and states according to the settings marked in budget control for the budget funds available. 

Seome budget control configuration settings that must be set to specific values for this feature to work properly. The required settings are listed in the following table.

| If this setting is enabled        | This also needs to be enabled     |
| :---------------------------------- | :---------------------------------- |
| Budget reservations for pre-encumbrances | Budget reservations for encumbrances **and** Actual expenditures |
| Budget reservations for encumbrances | Actual expenditures |
| When using PR-type General budget reservation documents and Budget reservations for encumbrances | Budget reservations for pre-encumbrances |

//todo add more content about the difference they will see with this feature on vs. off. 
