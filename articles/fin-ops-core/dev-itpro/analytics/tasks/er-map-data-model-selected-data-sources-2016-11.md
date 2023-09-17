---
title: ER Map data model to selected data sources
description: This article describes how to map an Electronic reporting (ER) data model to selected Microsoft Dynamics 365 Finance data sources.
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
ms.search.form: ERWorkspace, ERSolutionTable, ERDataModelDesigner, ERModelMappingTable, ERModelMappingDesigner
---
# ER Map data model to selected data sources

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can map an Electronic reporting (ER) data model to selected data sources. This model mapping will later be used as a data source in a format configuration that will be used to manage electronic payment documents. In this example, you map a data model for sample company, Litware, Inc. to data sources. To complete these steps, you must first complete the steps in the "Select data sources for model mapping" procedure.


## Open ER configurations tree
1. Go to Organization administration > Workspaces > Electronic reporting.
2. Click Configurations.

## Select created model mapping
1. In the tree, select 'Payments (simplified model)'.
    * Make sure that the model configuration "Payments (simplified model)" has been created in advance. Otherwise, stop now and return after completion of the task guide 'Create a new configuration with data model of the selected domain'.  
2. Click Model designer.
3. Click Map model to datasource.
4. Select the 'CT mapping' record.
    * CT mapping  

## Bind created data sources to data model elements
1. Click Designer.
2. In the tree, select 'Processing date & time(ProcessingDateTime)'.
3. In the tree, select 'Processing date(ProcessingDateTime)'.
4. Click Bind.
5. In the tree, select 'Payment message identification(MessageIdentification)'.
6. In the tree, expand 'Transactions'.
7. In the tree, select 'Transactions\Journal batch number(JournalNum)'.
8. Click Bind.
9. In the tree, select 'Payments'.
10. In the tree, select 'Transactions'.
11. Click Bind.
12. In the tree, expand 'Payments= Transactions'.
13. In the tree, expand 'Payments= Transactions\Creditor'.
14. In the tree, expand 'Payments= Transactions\Creditor\Account'.
15. In the tree, select 'Payments= Transactions\Creditor\Account\Currency code(Currency)'.
16. In the tree, expand 'Transactions\vendBankAccountInTransactionCompany()'.
17. In the tree, select 'Transactions\vendBankAccountInTransactionCompany()\Currency(CurrencyCode)'.
18. Click Bind.
19. In the tree, select 'Payments= Transactions\Creditor\Account\IBAN code(IBAN)'.
20. In the tree, select 'Transactions\vendBankAccountInTransactionCompany()\IBAN(BankIBAN)'.
21. Click Bind.
22. In the tree, select 'Payments= Transactions\Creditor\Account\Number'.
23. In the tree, select 'Transactions\vendBankAccountInTransactionCompany()\Bank account number(AccountNum)'.
24. Click Bind.
25. In the tree, expand 'Payments= Transactions\Creditor\Agent'.
26. In the tree, select 'Payments= Transactions\Creditor\Agent\Name'.
27. In the tree, select 'Transactions\vendBankAccountInTransactionCompany()\Name'.
28. Click Bind.
29. In the tree, select 'Payments= Transactions\Creditor\Agent\Routing number(RoutingNumber)'.
30. In the tree, select 'Transactions\vendBankAccountInTransactionCompany()\Routing number(RegistrationNum)'.
31. Click Bind.
32. In the tree, select 'Payments= Transactions\Creditor\Agent\SWIFT code(SWIFT)'.
33. In the tree, select 'Transactions\vendBankAccountInTransactionCompany()\SWIFT code(SWIFTNo)'.
34. Click Bind.
35. In the tree, select 'Payments= Transactions\Creditor\Name'.
36. In the tree, expand 'Transactions\findVendTable()'.
37. In the tree, select 'Transactions\findVendTable()\name()'.
38. Click Bind.
39. In the tree, select 'Payments= Transactions\Currency code(Currency)'.
40. In the tree, expand 'Transactions\>Relations'.
41. In the tree, expand 'Transactions\>Relations\Currency table(Currency)'.
42. In the tree, select 'Transactions\>Relations\Currency table(Currency)\Currency code(CurrencyCodeISO)'.
43. Click Bind.
44. In the tree, expand 'Payments= Transactions\Debtor'.
45. In the tree, expand 'Payments= Transactions\Debtor\Account'.
46. In the tree, select 'Payments= Transactions\Debtor\Account\Currency code(Currency)'.
47. In the tree, select 'Bank Account(BankAccount)'.
48. In the tree, expand 'Bank Account(BankAccount)'.
49. In the tree, select 'Bank Account(BankAccount)\Currency(CurrencyCode)'.
50. Click Bind.
51. In the tree, select 'Bank Account(BankAccount)\IBAN'.
52. In the tree, select 'Payments= Transactions\Debtor\Account\IBAN code(IBAN)'.
53. Click Bind.
54. In the tree, select 'Payments= Transactions\Debtor\Account\Number'.
55. In the tree, select 'Bank Account(BankAccount)\Bank account number(AccountNum)'.
56. Click Bind.
57. In the tree, expand 'Payments= Transactions\Debtor\Agent'.
58. In the tree, select 'Payments= Transactions\Debtor\Agent\Name'.
59. In the tree, select 'Bank Account(BankAccount)\Name'.
60. Click Bind.
61. In the tree, select 'Payments= Transactions\Debtor\Agent\Routing number(RoutingNumber)'.
62. In the tree, select 'Bank Account(BankAccount)\Routing number(RegistrationNum)'.
63. Click Bind.
64. In the tree, select 'Payments= Transactions\Debtor\Agent\SWIFT code(SWIFT)'.
65. In the tree, select 'Bank Account(BankAccount)\SWIFT code(SWIFTNo)'.
66. Click Bind.
67. In the tree, select 'Payments= Transactions\Debtor\Name'.
68. In the tree, select 'Company information(Company)'.
69. In the tree, expand 'Company information(Company)'.
70. In the tree, select 'Company information(Company)\Name'.
71. Click Bind.
72. In the tree, select 'Payments= Transactions\Description'.
73. In the tree, select 'Transactions\Description(Txt)'.
74. Click Bind.
75. In the tree, select 'Payments= Transactions\End to end identification code(End2EndID)'.
76. In the tree, select 'Transactions\$EndToEndID'.
77. Click Bind.
78. In the tree, select 'Payments= Transactions\Instructed amount(InstructedAmount)'.
79. In the tree, select 'Transactions\$Amount'.
80. Click Bind.
81. In the tree, select 'Payments= Transactions\Transaction date(TransactionDate)'.
82. In the tree, select 'Transactions\Date(TransDate)'.
83. Click Bind.

## Validate created mapping
1. Click Validate.
    * Validate the new mapping to ensure that all bindings are okay.  
2. Click the arrow to expand or collapse the Error List section.
3. Click Save.
4. Close the page.
5. Close the page.
6. Close the page.

## Change the status of the current version of model configuration
1. Click Change status.
    * Change the status of designed model configuration – from Draft to Completed to make it available for payment format design.  
2. Click Complete.
    * Select Complete.  
3. In the Description field, type a value.
    * For example, 'version 1'.  
4. Click OK.
5. Select the completed version of the current configuration.
    * Note that the created configuration is saved as completed version 1.  



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
