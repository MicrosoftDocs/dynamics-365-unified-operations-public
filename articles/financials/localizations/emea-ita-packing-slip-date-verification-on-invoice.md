---
# required metadata

title: Packing slip date verification on invoices for Italy
description: For Italy, the invoice date is verified on packing slips and invoice proposals. This topic provides additional information about the verification that occurs. 
author: ShylaThompson
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 263824
ms.search.region: Italy
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Packing slip date verification on invoices for Italy

[!include[banner](../includes/banner.md)]


For Italy, the invoice date is verified on packing slips and invoice proposals. This topic provides additional information about the verification that occurs. 

For legal entities with primary addresses in Italy there is a packing slip date verification step for users who generate sales invoices or project invoices.

-   Packing slips that are dated later than the invoice are not be included in the suggested update quantity.
-   For project management and accounting, when you create an invoice proposal, only the customer packing slips that are dated earlier than the invoice proposal are included in the proposal. **Note**: If the user input date for the invoice proposal is empty, the system date is used.




