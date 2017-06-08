---
# required metadata

title: Financial dimensions and main accounts in a right-to-left language
description: This topic describes some of the implementation decisions that you should consider when you use a right-to-left language in Microsoft Dynamics 365 for Operations, and you must set up financial dimensions and main accounts.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 101
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 222564
ms.assetid: 875dcebb-1bbb-4841-a8c6-9e134da07e96
ms.search.region: global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Financial dimensions and main accounts in a right-to-left language

[!include[banner](../includes/banner.md)]


This topic describes some of the implementation decisions that you should consider when you use a right-to-left language in Microsoft Dynamics 365 for Operations, and you must set up financial dimensions and main accounts.

Financial dimensions and main accounts are key components of the planning phase for an implementation. After financial dimensions and main accounts are created in the system, they are used on the **Configure account structures**, **Advanced rule structures**, and **Financial dimension configuration for integrating applications** pages. The order that is defined on those pages is used in the system for data entry and consumption. In some places in the system, the financial dimensions and main accounts appear in separate fields. However, in other places, such as journals, the financial dimensions and main accounts appear as a single string.

### Best practices for setting up financial dimensions and main accounts in a right-to-left system

-   When you select the delimiter for charts of accounts, select one of the double delimiter options: double hyphen (--), double bar (||) or double period (..), or double underscore (\_\_).
-   When you create financial dimension and main account values, use only numbers and right-to-left language characters.
-   Avoid using the selected chart of accounts delimiter in financial dimension and main account values.

By following these best practices, you help guarantee consistent representation of the user defined-order throughout the system.



