--- 
# required metadata 
 
title: FR-00004 French bills of exchange and promissory notes
description: The French bill of exchange remittance report displays details about remitted bills of exchange. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustPaymMode, CustVendPaymFormat   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: France
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# FR-00004 French bills of exchange and promissory notes

[!include [banner](../../includes/banner.md)]

The French bill of exchange remittance report displays details about remitted bills of exchange. The report includes information about your bank account, legal entity, and remittance type. It also provides a list of customer transactions that are affected by the bill of exchange. This report is used by accounts receivable clerks and accounts payable clerks to maintain customer payments. 



This procedure walks you through creating the bill of exchange remittance journal and generating the bill of exchange remittance report.

Before you can complete this procedure, you must create, approve, and post draw the bill of exchange journal.

This procedure was created using the demo data company FRSI.

1. Go to Accounts receivable > Payments > Bill of exchange > Remittance journal.
2. Click New.
3. In the Name field, enter or select a value.
4. In the list, click the link in the selected row.
    * For example, enter 'RemiseBque'.  
5. Click the Bill of exchange tab.
6. In the Bank account field, enter or select a value.
7. In the list, find and select the desired record.
    * For example, select 'FRN'.  
8. In the list, click the link in the selected row.
9. Click the Setup tab.
10. In the Account type field, select 'Bank'.
11. In the Offset account field, specify the desired values.
    * For example, select 'FRSI OPER'.  
12. Click Lines.
13. In the Account field, specify the desired values.
    * For example, select 'FR_SI_0020'.  
14. Click Settle transactions.
    * Select the lines to include.  
15. Click OK.
16. Click Generate remittance.
17. In the Method of payment field, enter or select a value.
18. In the list, find and select the desired record.
    * For example, select 'BOEPDF'.  
19. In the File name field, type a value.
20. Click OK.
    * You might be asked to enter a processing date.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]