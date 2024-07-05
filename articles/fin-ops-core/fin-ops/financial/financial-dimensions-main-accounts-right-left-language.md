---
title: Financial dimensions and main accounts in right-to-left languages
description: Learn about decisions that you need to make when you use a right-to-left language, and you must set up financial dimensions and main accounts.
author: RyanCCarlson2
ms.author: rcarlson
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/19/2024
ms.reviewer: johnmichalak
ms.search.region: global
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.assetid: 875dcebb-1bbb-4841-a8c6-9e134da07e96
---

# Financial dimensions and main accounts in right-to-left languages

[!include [banner](../../../finance/includes/banner.md)]

This article describes some of the implementation decisions that you should consider when you use a right-to-left language, and you must set up financial dimensions and main accounts.

Financial dimensions and main accounts are key components of the planning phase for an implementation. After financial dimensions and main accounts are created in the system, they are used on the **Configure account structures**, **Advanced rule structures**, and **Financial dimension configuration for integrating applications** pages. The order that is defined on those pages is used in the system for data entry and consumption. In some places in the system, the financial dimensions and main accounts appear in separate fields. In other places, such as journals, the financial dimensions and main accounts appear as a single string.

## Best practices for setting up financial dimensions and main accounts in a right-to-left system

- When you select the delimiter for charts of accounts, select one of the double delimiter options: double hyphen (`--`), double bar (`||`), double period (`..`), or double underscore (`\\`).
- When you create financial dimension and main account values, use only numbers and right-to-left language characters.
- Avoid using the selected chart of accounts delimiter in financial dimension and main account values.

By following these best practices, you help guarantee consistent representation of the user defined-order throughout the system.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
