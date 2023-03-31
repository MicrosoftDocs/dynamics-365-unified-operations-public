---
title: ER Generate electronic documents for payments using a format configuration
description: This article describes how to use a new Electronic reporting (ER) format configuration to generate electronic documents for processing payments.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: VendPaymMode, LedgerJournalTable, LedgerJournalTransVendPaym, BankAccountTableLookUp
---
# ER Generate electronic documents for payments using a format configuration

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can use a new Electronic reporting (ER) format configuration to generate electronic documents for processing payments. These steps can be performed in the GBSI sample company.

To complete these steps, you must first complete the steps in the "Create a configuration with format of payment document" procedure.


## Change the configuration of the electronic payment method
1. Go to Accounts payable > Payment setup > Methods of payment.
2. Toggle the File format section to expand it, if needed.
3. Use the Quick Filter to find records. For example, filter on the Method of payment field with a value of 'Electronic'.
4. Click Edit.
5. Set the General electronic reporting field to Yes.
    * Select Yes to use the General electronic reporting pattern for payment files generation.  
6. In the Name field, click the drop-down button to open the lookup.
7. Select BACS (UK fictitious) format configuration.
8. Click Save.
9. Close the page.

## Test the format of generated payment files
1. Go to Accounts payable > Payments > Payment journal.
2. Click New.
3. In the list, mark the selected row.
4. In the Name field, click the drop-down button to open the lookup.
5. In the list, click the link in the selected row.
    * Select VendPay.  
6. Click Save.
7. Click Lines.
8. In the Company field, type 'DEMF'.
    * DEMF  
9. In the Account field, specify the values 'DE-01001'.
    * DE-01001  
10. In the Description field, type 'Payment'.
    * Payment  
11. In the Debit field, enter a number.
    * 1000  
12. Click the Payment tab.
13. In the Method of payment field, click the drop-down button to open the lookup.
14. In the list, find and select the desired record.
    * Select the Electronic value.  
15. In the list, click the link in the selected row.
16. Click Save.
17. Click Generate payments.
18. In the Method of payment field, click the drop-down button to open the lookup.
19. In the list, find and select the desired record.
    * Select the Electronic value.  
20. In the list, click the link in the selected row.
    * Select the Electronic value.  
21. In the File name field, type a value.
    * For example, type 'payments'.  
22. In the Bank account field, click the drop-down button to open the lookup.
23. In the list, click the link in the selected row.
    * Select the value GBSI OPER.  
24. Click OK.
25. Click OK.
    * Analyze the created payment file in XML format. Compare it with the designed document layout and defined payment transaction attributes.  



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
