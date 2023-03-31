--- 
# required metadata 
 
title: Create solicitation types and scoring criteria for RFQs
description: This guide shows you how to create a solicitation type and associate this with a scoring method. 
author: GalynaFedorova
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchRFQSolicitationType, PurchRFQCaseTableListPage, PurchCreateRFQCase, PurchRFQCaseTable, PurchRFQScoringRFQCaseCriteria, PurchRFQScoringCriteriaCopy   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create solicitation types and scoring criteria for RFQs

[!include [banner](../../includes/banner.md)]

This guide shows you how to create a solicitation type and associate this with a scoring method. It also shows how to use the solicitation type on a request for quotation (RFQ) which then sets the default scoring method. These tasks would typically be carried out by a purchasing manager. You can use this procedure in demo data company USMF or on your own data. You need to have a scoring method available before you start.


## Create a solicitation type
1. Go to Procurement and sourcing > Setup > Request for quotation > Solicitation type.
2. Click New.
3. In the Name field, type a value.
4. In the Description field, type a value.
5. In the Scoring method field, select the scoring method that you want to use for this solicitation type.
6. Click Save.
7. Close the page.

## Use the solicitation type
1. Go to Procurement and sourcing > Requests for quotations > All requests for quotations.
2. Click New.
3. In the Solicitation type field, select the solicitation type that you have just created. 
    *   
4. Click OK.
5. Click Scoring criteria.
    * The scoring criteria that are shown are the ones from the scoring method that you associated with the solicitation type. You can choose to add or delete criteria on this page. It's also possible to add new criteria by copying them from other scoring methods.  
6. Click Copy criteria.
7. In the Scoring method field, enter or select a value.
8. Click OK.
9. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]