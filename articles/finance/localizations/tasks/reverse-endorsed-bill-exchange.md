--- 
# required metadata 
 
title: Reverse an endorsed bill of exchange
description: This task walks you through reversing an endorsed bill of exchange. 
author: ShylaThompson
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustBillOfExchangeEndorseListPage, CustBillOfExchangeEndorseReverse, LedgerTransVoucher   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Reverse an endorsed bill of exchange

[!include [banner](../../includes/banner.md)]

This task walks you through reversing an endorsed bill of exchange.



Before you can complete this task, you must have at least one endorsed bill of exchange. 

This task was created using the demo data company JPMF.

1. Go to Accounts payable > Payments > Endorse bills of exchange.
2. In the list, find and select the desired record.
    * Select a bill of exchange that has a status of "Endorsed".  Note that you cannot reserve a bill of exchange if the vendor transaction is already settled. You must undo the settlement before reserving the endorsement.  
3. Click Reverse endorsement to open the drop dialog.
4. Click Reverse endorsement.
    * You can change the reverse date if necessary.  
5. Click Inquiry.
6. Click Voucher.
    * Verify that that an accounting voucher was generated for the reversal.  

