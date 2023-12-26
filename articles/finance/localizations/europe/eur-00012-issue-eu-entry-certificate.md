--- 
# required metadata 
 
title: EUR-00012 Issue an EU entry certificate
description: This procedure walks you through enabling an EU entry certificate, configuring a customer account to use entry certificates and issue a certificate. 
author: mrolecki
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustParameters, CustTable, SalesTableListPage, SalesCreateOrder, SalesTable, SalesEditLines,  CustInvoiceJournal, CustEntryCertificateJour_W, SrsReportViewerForm   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# EUR-00012 Issue an EU entry certificate

[!include [banner](../../includes/banner.md)]
This procedure walks you through enabling an EU entry certificate, configuring a customer account to use entry certificates and issue a certificate. This procedure was created using the demo data company DEMF.


## Enable entry certificate management
1. Go to Accounts receivable > Setup > Accounts receivable parameters.
2. Click the Shipments tab.
3. Expand the Entry certificate section.
4. Select Yes in the Enable entry certificate management field.
5. Select Yes in the Enable entry certificate issuing field.
6. Click the Number sequences tab.
7. In the list, find and select Entry certificate row.
8. In the Number sequence code field, enter or select a value.

## Set up a customer
1. Go to Accounts receivable > Customers > All customers.
2. Use the Quick Filter to find records. For example, filter on the Account field with a value of 'DE-015'.
3. Open customer account details.
4. Click Edit.
5. Expand the Invoice and delivery section.
6. Select Yes in the Entry certificate required field.
7. Select Yes in the Issue entry certificate field.
8. Click Save.

## Create an EU entry certificate automatically
1. Go to Accounts receivable > Orders > All sales orders.
2. Click New.
3. In the Customer account field, enter or select a value.
4. Click OK.
5. In the Item number field, enter or select a value.
6. Click Save.
7. On the Action Pane, click Pick and pack.
8. Click Post packing slip.
9. Expand the Parameters section.
10. In the Quantity field, select 'All'.
11. Clear the Issue entry certificate check box.
    * An entry certificate can be issued during packing slip posting or during order invoicing. Leave the Issue entry certificate checkbox unchecked to issue it later.  
12. Click OK.
13. Click OK.
14. On the Action Pane, click Invoice.
15. Click Invoice.
    * Verify that the Entry certificate required and Issue entry certificate checkboxes in the Overview section are marked.  You can also select the Print entry certificate check box to allow printing of the certificate.  
16. Click OK.
17. Click OK.
18. On the Action Pane, click Invoice.
19. Click Invoice.
20. On the Action Pane, click Invoice.
21. Click View issued entry certificates.
22. Click Print.
23. Close the page.
24. Click Change status.
25. In the New status field, select an option.
26. Click OK.
27. Close the page.

## Create an EU entry certificate manually
1. On the Action Pane, click Invoice.
2. Click Create entry certificate.
3. Click OK.
4. On the Action Pane, click Invoice.
5. Click View issued entry certificates.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]