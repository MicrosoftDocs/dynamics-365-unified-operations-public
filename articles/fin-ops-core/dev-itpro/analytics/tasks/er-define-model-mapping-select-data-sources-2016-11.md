---
title: Define ER model mappings and select data sources for them
description: This article describes how a System Administrator or an Electronic Reporting Developer can select data sources for an Electronic reporting data model.
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
ms.search.form: ERWorkspace, ERSolutionTable, ERDataModelDesigner, ERModelMappingTable, ERModelMappingDesigner, ERExpressionDesignerFormula
---
# Define ER model mappings and select data sources for them

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can select data sources for an Electronic reporting (ER) data model. The data sources will be bound to individual components of the selected data model at design time and populate business data to that data model at run-time. In this example, you will select data sources for an existing data model that has been created for sample company, Litware, Inc. To complete these steps, you must first complete the steps in the "Create a new data model" procedure.


## Open the Electronic Reporting configurations tree
1. Go to Organization administration > Workspaces > Electronic reporting.
2. Click Reporting configurations.

## Insert a new model mapping
1. In the tree, select 'Payments (simplified model)'.
2. Click Designer.
3. Click Map model to datasource.
4. Click New.
    * This will create a new record that will map the data model to data sources. In this example, you will map the data model to data sources for the desired payment type: credit transfer.     It is possible to design more than one mapping for a particular data model. For example, you could create a mapping for the different types of payments, such as for direct debit or for credit transfers. In this example, you will create a mapping for credit transfers.  
5. In the Name field, type 'CT mapping'.
    * CT mapping  
6. In the Description field, type 'Payment model mapping CT'.
    * Payment model mapping CT  
7. In the Definition field, type 'CustomerCreditTransferInitiation'.
    * CustomerCreditTransferInitiation  
8. ResolveChanges the Definition.
9. Click Save.

## Define required data sources for the current model mapping
1. Click Designer.
2. In the tree, select 'Dynamics 365 for Operations\Table records'.
3. Click Add root.
    * Enter this data source to access payment transactions.  
4. In the Name field, type 'Transactions'.
    * Transactions  
5. In the Label field, enter 'Transactions'.
    * Transactions  
6. In the Help field, enter 'Ledger journal lines'.
    * Ledger journal lines  
7. Select Yes in the Ask for query field.
    * Select Yes.  
8. In the Table field, type 'LedgerJournalTrans'.
    * LedgerJournalTrans  
9. Click OK.
    * Select the LedgerJournalTrans table as a data source for the current data model.  
10. In the tree, select 'Functions\Calculated field'.
11. Click Add.
    * Click Add to add a new calculated field.  
12. In the Name field, type '$EndToEndID'.
    * $EndToEndID  
13. Click Edit formula.
14. In the tree, select 'String\CONCATENATE'.
15. Click Add function.
16. In the tree, expand 'Transactions'.
17. In the tree, select 'Transactions\Voucher'.
18. Click Add data source.
19. In the Formula field, enter 'CONCATENATE(Transactions.Voucher, "-", '.
    * Type [ , "-", ] at the end of the formula.  
20. In the tree, select 'String\TEXT'.
21. Click Add function.
22. In the tree, select 'Transactions\Record-ID(RecId)'.
23. Click Add data source.
24. In the Formula field, enter 'CONCATENATE(Transactions.Voucher, "-", TEXT(Transactions.RecId))'.
    * Type [))] at the end of the formula.  
25. Click Save.
    * Make sure that no errors have been discovered for the created formula. See the ERRORS tab below the formula editor control.  
26. Close the page.
27. Click OK.
    * Add the calculated field to this data source.  
28. Click Add.
    * Click Add to add a new calculated field.  
29. In the Name field, type '$Amount'.
    * $Amount  
30. Click Edit formula.
31. In the tree, expand 'Transactions'.
32. In the tree, select 'Transactions\Debit(AmountCurDebit)'.
33. Click Add data source.
34. In the Formula field, enter 'Transactions.AmountCurDebit - '.
    * Type [ - ] at the end of the formula.  
35. In the tree, select 'Transactions\Credit(AmountCurCredit)'.
36. Click Add data source.
37. Click Save.
38. Close the page.
39. Click OK.
    * This will add the $Amount calculated field to the selected data source for the current data model.  
40. In the tree, select 'Transactions\$Amount'.
41. In the tree, expand 'Transactions'.
42. In the tree, expand or collapse 'Transactions\$Amount'.
43. In the tree, expand or collapse 'Transactions'.
44. In the tree, select 'Dynamics 365 for Operations\Table records'.
45. Click Add root.
    * Enter this data source to access the company's bank account details.  
46. In the Name field, type 'BankAccount'.
    * BankAccount  
47. In the Label field, enter 'Bank Account'.
    * Bank Account  
48. In the Help field, enter 'Bank Account'.
    * Bank Account  
49. Select Yes in the Ask for query field.
    * Select Yes.  
50. In the Table field, type 'BankAccountTable'.
    * BankAccountTable  
51. Click OK.
    * Select the BankAccountTable table as a data source for the current data model.  
52. Click Add root.
    * Enter this data source to access the company's requisites.  
53. In the Name field, type 'Company'.
    * Company  
54. In the Label field, type a value.
    * Company information  
55. In the Help field, enter 'Company information'.
    * Company information  
56. Select Yes in the Ask for query field.
    * Select Yes.  
57. In the Table field, type 'CompanyInfo'.
    * CompanyInfo  
58. Click OK.
    * Select the CompanyInfo table as a data source for the current data model.  
59. In the tree, select 'Functions\Calculated field'.
60. Click Add root.
    * Insert a calculated field as a new data source.  
61. In the Name field, type 'ProcessingDateTime'.
    * ProcessingDateTime  
62. In the Label field, enter 'Processing date & time'.
    * Processing date & time  
63. Click Edit formula.
64. In the tree, select 'Date/time\SESSIONNOW'.
65. Click Add function.
66. Click Save.
67. Close the page.
68. Click OK.
    * Add the ProcessingDateTime calculated field as a data source for the current data model.  
69. Click Save.
70. Close the page.
71. Close the page.
72. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
