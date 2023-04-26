---
title: Add BAS report boxes and generate the Australia Business Activity Statement BAS
description: This procedure walks you through adding BAS report boxes and generating the BAS.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Australia
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: LedgerJournalTable, LedgerJournalTransVendInvoice, DefaultDashboard, LedgerJournalTransVendPaym, VendOpenTrans, TaxGroupLookup, TaxItemGroupLookup, CustFreeInvoice, CustTableLookup, CustPostInvoiceJob, TaxReportExtraFields, SrsReportViewerForm
---
# Add BAS report boxes and generate the Australia Business Activity Statement BAS

[!include [banner](../../includes/banner.md)]

This procedure walks you through adding BAS report boxes and generating the BAS. Before you can complete this procedure, you must define the additional BAS reconciliation account,  create BAS PAYG reason codes, create BAS fringe benefit reason codes, create sales tax (reporting code) and withholding tax groups with required purchase and sales transactions.



This procedure was created using the demo data company 'USMF' with a primary legal entity address in Australia.


## Add BAS report boxes and print the Australia BAS
1. Go to Tax > Declarations > Sales tax > Additional BAS report boxes.
2. Click New.
3. In the Settlement period field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. In the From date field, enter a date.
7. In the To date field, enter a date.
8. In the Document identification number field, type a value.
    * Enter the activity statement unique document identification number  
9. Click the Cover page tab.
10. In the 7 Deferred installment field, enter a number.
11. In the 7A Deferred GST on imports field, enter a number.
12. In the 1G Credit for wholesale sales tax field, enter a number.
13. In the 5B Credit from PAYG field, enter a number.
14. In the 6B Credit fringe benefits tax field, enter a number.
15. Click the Back cover page tab.
16. In the W1 Total payroll field, enter a number.
    * Enter Total salary, wages and other payments.  
17. In the W-2 Withheld from payroll field, enter a number.
    * Enter the total amount you withheld from salaries, wages and other payments, including payments to contractors under a voluntary agreement shown in box W1.  
18. In the W3 Withheld from investment where no TFN field, enter a number.
    * W3 covers other types of withholding:  -interest, dividends, unit trust or other investment distributions provided with a TFN (includes a non-resident)  -any payments  made to foreign residents    
19. In the W4 Withheld from invoices where no ABN field, enter a number.
    * Enter the total amount you withheld from payments to suppliers who did not quote their ABN.  
20. In the T1 Installment income field, enter a number.
    * Calculate your installment income for the quarter and enter this in the T1 box.  
21. In the T2 Installment rate field, enter a number.
    * The rate entered at T2 will be either:  -The installment rate worked out by us  -The most recent varied rate, if you have varied the installment rate in a previous quarter in the same income year.    
22. In the T3 New varied installment rate field, enter a number.
    * If you want to vary your installment rate, enter your new rate in the T3 box.    
23. In the T4 Reason for variation field, click the drop-down button to open the lookup.
    * If you vary your installment rate, choose a reason from the list that best describes why and enter the appropriate code.  
24. In the list, click the link in the selected row.
25. In the F1 ATO fringe benefit field, enter a number.
    * If you pay FBT quarterly, a pre-determined installment will be shown in F1.  
26. In the F2 Estimated total fringe benefits field, enter a number.
    * The estimated total FBT liability for the year.  
27. In the F3 Varied fringe benefits tax field, enter a number.
    * The amount of varied FBT installment.  
28. In the F4 Reason for variation field, click the drop-down button to open the lookup.
    * If the FBT installment amount has been varied, choose the reason, and enter the corresponding code.  
29. In the list, click the link in the selected row.
30. In the 7C Fuel tax credit over claim field, enter a number.
    * Enter any adjustments to fuel tax credits that will decrease your entitlement.  
31. In the 7D Fuel tax credit field, enter a number.
    * The amount of fuel tax credits that can be claimed depends on your business activities. For example, business activities might include acquiring, manufacturing or importing taxable fuel into Australia or when you use the fuel you manufactured.  Enter any adjustments or corrections that increase your entitlements to fuel tax credits.  
32. On the Action Pane, click ActionPaneTab.
33. Click Print Australian BAS.
    * Validate the Australian BAS report.  

## Generate the Australian BAS
1. Go to Tax > Declarations > Sales tax > Australian BAS.
2. In the Settlement period field, click the drop-down button to open the lookup.
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. In the From date field, enter a date.
6. In the Transaction date field, enter a date.
7. Select or clear the Post and settle GST check box.
8. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
