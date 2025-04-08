---
title: EUR-00015 Party search using VAT ID
description: Learn how to perform a party search using a registration ID with Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2025
ms.reviewer: johnmichalak
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.search.validFrom: 2016-06-30
ms.search.form: DirPartyTable, DirPartTaxRegistrationSearch
---

# EUR-00015 Party search using VAT ID

[!include [banner](../../includes/banner.md)]

This article explains how to perform a party search using a registration ID with Microsoft Dynamics 365 Finance.

The following procedure shows how to perform a party search using a registration ID. Before you can complete this procedure, you must set up VAT IDs and enter any VAT IDs for vendors, customers, or legal entities.

The procedure applies to all European countries/regions, and was created using the demo data company DEMF with a primary address in Germany. The procedure is intended for an accounts payable manager or accounts receivable manager.

To perform a party search using a registration ID, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration > Global address book > Global address book**.
1. Select **Registration ID search**.
1. Select **Add**.
1. In the **Registration type** field, enter or select a value. For example, if you wanted to find parties with a registration ID of type VAT ID, select **VAT ID**.  
1. In the **Country/region** field, enter or select a value. For example, enter "DEU".  
1. In the **Registration number** field, enter a value.
1. Select **Find**. All parties with that registration ID are displayed.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
