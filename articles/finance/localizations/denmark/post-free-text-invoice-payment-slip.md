--- 
# required metadata 
 
title: Post a free text invoice with a payment slip
description: This article explains how to post a free text invoice with a payment slip attachment in a specified format. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustFreeInvoice, CustTableLookup, CustPostInvoiceJob, SRSPrintDestinationSettingsForm   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Denmark
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Post a free text invoice with a payment slip

[!include [banner](../../includes/banner.md)]

You can post a free text invoice with a payment slip attachment in a specified format. The payment slip is printed with the creditor identification number and invoice number to identify the payment.



This procedure walks you through posting a free text invoice with a payment slip.



Before you can complete this procedure, you must set up a payment slip formats and setup payment slip for customer invoices. 

This procedure was created using the demo data company DEMF. 

This functionality is available for legal entities whose primary address is in Denmark. 



1. Go to Accounts receivable > Invoices > All free text invoices.
2. Click New.
3. In the Customer account field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. In the Currency field, click the drop-down button to open the lookup.
7. In the list, find and select the desired record.
    * The payment slip can be printed only for free text invoice with currency Danish kroner (DKK).  
8. In the list, click the link in the selected row.
9. In the list, mark the selected row.
10. In the Description field, type a value.
11. In the Main account field, specify the desired values.
12. In the Unit price field, enter a number.
13. Click Save.
14. Click Post.
15. Click OK.
16. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
