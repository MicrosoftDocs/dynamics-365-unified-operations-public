---
title: EUR-00015 Party search using VAT ID
description: This procedure shows how to complete a party search using a registration ID.
author: AdamTrukawka
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: DirPartyTable, DirPartTaxRegistrationSearch
---
# EUR-00015 Party search using VAT ID

[!include [banner](../../includes/banner.md)]

This procedure shows how to complete a party search using a registration ID. Before you can complete this procedure, you must set up VAT IDs and enter any VAT IDs for vendors, customers, or legal entities.

This procedure applies to all European countries/regions. The procedure was created using the demo data company DEMF with a primary address in Germany. This procedure is intended for an accounts payable manager or accounts receivable manager. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

1. Go to Organization administration > Global address book > Global address book.
2. Click Registration ID search.
3. Click Add.
4. In the Registration type field, enter or select a value.
    * For example, if you wanted to find parties with a registration ID of type VAT ID, select VAT ID.  
5. In the Country/region field, enter or select a value.
    * For example, enter DEU.  
6. In the Registration number field, type a value.
7. Click Find.
    * All parties with that registration ID will be displayed.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
