---
title: Packing slip date verification on invoices for Italy
description: For Italy, the invoice date is verified on packing slips and invoice proposals. This article provides additional information about the verification that occurs.
author: AdamTrukawka
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Italy
ms.author: atrukawk
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 263824
ms.search.form: CustPackingSlipJournal
---

# Packing slip date verification on invoices for Italy

[!include [banner](../../includes/banner.md)]

For Italy, the invoice date is verified on packing slips and invoice proposals. This article provides additional information about the verification that occurs. 

For legal entities with primary addresses in Italy there is a packing slip date verification step for users who generate sales invoices or project invoices.

-   Packing slips that are dated later than the invoice are not be included in the suggested update quantity.
-   For project management and accounting, when you create an invoice proposal, only the customer packing slips that are dated earlier than the invoice proposal are included in the proposal. **Note**: If the user input date for the invoice proposal is empty, the system date is used.






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
