---
# required metadata

title: Packing slip date verification on invoices for Italy | Microsoft Docs
description: For Italy, the invoice date is verified on packing slips and invoice proposals. This topic provides additional information about the verification that occurs. 
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-14 22:43:22
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 81
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 263824
ms.assetid: 51d7f47c-62ec-4c6c-b1bd-4d0db1b35f2e
ms.region: Italy
# ms.industry: 
ms.author: v-elgolu

---

# Packing slip date verification on invoices for Italy

For Italy, the invoice date is verified on packing slips and invoice proposals. This topic provides additional information about the verification that occurs. 

For legal entities with primary addresses in Italy there is a packing slip date verification step for users who generate sales invoices or project invoices.

-   Packing slips that are dated later than the invoice are not be included in the suggested update quantity.
-   For project management and accounting, when you create an invoice proposal, only the customer packing slips that are dated earlier than the invoice proposal are included in the proposal. **Note**: If the user input date for the invoice proposal is empty, the system date is used.


