--- 
# required metadata 
 
title: Create and export vendor payments using ISO20022 payment format
description: This procedure shows how to create payment lines in the vendor payment journal and generate a vendor payment file using ISO2022 Credit transfer example. 
author: mrolecki
manager: AnnBe 
ms.date: 10/24/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create and export vendor payments using ISO20022 payment format

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to create payment lines in the vendor payment journal and generate a vendor payment file using ISO2022 Credit transfer example. 

The demo data company used to create this procedure is DEMF.

This is the fifth procedure, out of five, that illustrates the vendor payment process using electronic reporting configurations. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Create payment lines
1. Go to Accounts payable > Payments > Payment journal.
2. Click New.
3. In the list, mark the selected row.
4. In the Name field, enter or select a value.
5. Click Lines.
6. Click Payment proposal.
7. Click Create payment proposal.
8. Expand the Records to include section.
9. Click Filter.
10. In the list, select the row for Vendors table and Vendor account field.
11. In the Criteria field, enter or select a value.
    * You can apply any criteria for selecting vendor transactions to pay, for this example use DE-001 as a vendor account.  
12. Click OK.
13. Click OK.
14. Click Create payments.

## Generate an ISO20022 payment file

