--- 
# required metadata 
 
title: Create a scoring method for RFQs
description: This procedure shows you how to create a scoring method. 
author: GalynaFedorova
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchRFQScoringMethod   
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
# Create a scoring method for RFQs

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a scoring method. A scoring method is a set of criteria that can be used to compare bids that are sent in reply to a request for quotation (RFQ). For example, you might want to rate a vendor on past performance, or rate whether the company is environmentally friendly or a good collaborator, or you might want to compare bids based on price. The scoring method can be associated with a solicitation type as the default scoring method for RFQs of that type. These tasks would typically be carried out by a purchasing manager. You can use this procedure in demo data company USMF or on your own data.

1. Go to Procurement and sourcing > Setup > Request for quotation > Scoring method.
2. Click New.
3. In the Name field, type a value.
4. In the Description field, type a value.
5. Click Save.
6. Click New.
7. In the Name field, type a value.
8. In the Description field, type a value.
    * This description is shown along with the scoring method name when a scoring method is selected for an RFQ.  
9. In the Range from field, enter a number.
    * The range limits what the procurement professional can enter as a score. When there are multiple scoring criteria on an RFQ, the scores that have been entered are added to each other and the sum is made available to allow the bids to be compared.  
10. In the Range to field, enter a number.
11. Click New.
12. In the Name field, type a value.
13. In the Description field, type a value.
14. In the Range from field, enter a number.
15. In the Range to field, enter a number.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]