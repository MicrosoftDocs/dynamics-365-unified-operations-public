--- 
# required metadata 
 
title: Reconcile freight manually
description: This procedure shows how to reconcile freight manually. 
author: BibiSp
manager: AnnBe 
ms.date: 10/13/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: bis
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: bis
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Reconcile freight manually

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to reconcile freight manually. This is typically done by a transportation coordinator. You can use this procedure in the USMF demo data company.


## Select a load to reconcile
1. Go to Transportation management > Planning > Load planning workbench.
2. Clear the Hide shipped and received check box. 
3. In the list, select the load that has load ID 00006.

## Create a carrier invoice
    * If you reconcile freight manually and don’t receive carrier invoices automatically, you can create an invoice based on the freight bill.  
1. Click Related information.
2. Click Freight bill details.
3. Click Generate freight bill invoice.
4. In the Invoice field, type a value.
5. Click OK.

## Reconcile the invoice
    * When you reconcile a carrier invoice and a freight bill, this is done line by line.  
1. Click Match freight bills and invoices.
2. Expand the Invoice details section.
3. Expand the Unmatched freight bill details section.
4. In the list, mark the selected row.
5. Click Match.
6. Expand the Matched freight bill details section.

## Submit the invoice for approval
1. Click Submit for approval.
2. Close the page.
3. Clear the Hide approved check box. 
4. Click Vendor invoice journals.
5. Click to follow the link in the Reference journal number field.
6. Click Lines.

