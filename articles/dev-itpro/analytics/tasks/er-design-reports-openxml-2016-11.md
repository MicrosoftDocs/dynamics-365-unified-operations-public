--- 
# required metadata 
 
title: Design a configuration for generating reports in OpenXML format for electronic reporting (ER)
description: The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can create a new Electronic reporting (ER) configuration that contains a template for generating electronic documents in OPENXML format. 
author: NickSelin
manager: AnnBe 
ms.date: 01/16/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Design a configuration for generating reports in OpenXML format for electronic reporting (ER)

[!include[task guide banner](../../includes/task-guide-banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can create a new Electronic reporting (ER) configuration that contains a template for generating electronic documents in OPENXML format. This configuration will be used for processing vendor payments.



In this example, you will create a configuration for sample company, Litware, Inc. These steps can be performed in GBSI company.



To complete these steps, you must first complete the steps in the “Create a configuration provider and mark it as active” procedure. You must also download and save the Microsoft Excel file, [Template of Payment Report](https://go.microsoft.com/fwlink/?linkid=862266). 

## Upload the Payments data model configuration
1. Go to Organization administration > Workspaces > Electronic reporting.
2. In the list, mark the selected row.
    * Select the configuration provider for sample company, Litware, Inc. If you don’t see this configuration provider, you must first complete the steps in the “Create a configuration provider and mark it as active” procedure.  
3. Click Set active.
4. Click Repositories.
    * Select a repository for the Operations Resources type, if available. If its available, skip the following steps about creating a new repository.  
5. Click Add to open the drop dialog.
6. In the Configuration repository type field, enter 'Operations resources'.
7. Click Create repository.
8. Click OK.
9. Click Open.
10. In the tree, select 'Payment model'.
11. Click Import.
    * Import this data model. It will be used as a data source in a new format configuration. Skip this step if this configuration has been already imported.  
12. Click Yes.
13. Close the page.
14. Close the page.

## Create a new format configuration
1. Click Reporting configurations.
2. In the tree, select 'Payment model'.
3. Click Create configuration to open the drop dialog.
4. In the New field, enter 'Format based on data model PaymentModel'.
    * Create a format that is based on the PaymentModel data model.  
5. In the Name field, type 'Sample worksheet report'.
    * Sample worksheet report  
6. In the Description field, type 'Sample worksheet report for vendors’ payments'.
    * Sample worksheet report for vendors’ payments.  
7. In the Data model definition field, enter or select a value.
    * Select the 'CustomerCreditTransferInitiation' definition.  
8. Click Create configuration.

## Design a new document in OPENXML worksheet format
1. In the tree, select 'Payment model\Sample worksheet report'.
2. Click Designer.
3. On the Action Pane, click Import.
4. Click Import from Excel.
5. Click Attachments.
    * Attach the existing Excel document as a template.  
6. Click New.
7. Click File.
    * Point to the existing Excel file.  
8. Close the page.
9. In the Template field, enter or select a value.
    * Select the attached Excel file to be used as a template.  
10. Click OK.
    * Note that ER format components have been created in the designing format based on the structure of the referring MS Excel document (named ranges).  

## Create a new data source to calculate totals by currency codes
1. Click the Mapping tab.
2. Click Add root to open the drop dialog.
3. In the tree, select 'Functions\Group by'.
4. In the Name field, type 'PaymentByCurrency'.
    * PaymentByCurrency  
5. Click Edit group by.
6. In the tree, expand 'model'.
7. In the tree, select 'model\Payments'.
8. Click Add field to.
9. Click What to group.
10. In the tree, expand 'model\Payments'.
11. In the tree, select 'model\Payments\Currency'.
12. Click Add field to.
13. Click Grouped fields.
14. In the tree, select 'model\Payments\Instructed Amount(InstructedAmount)'.
15. Click Add field to.
16. Click Aggregation fields.
17. In the Method field, select an option.
    * Select the SUM aggregation function.  
18. In the Name field, type 'TotalInstructuredAmount'.
    * TotalInstructuredAmount  
19. Click Save.
20. Close the page.
21. Click OK.

## Map format components to data sources
1. In the tree, expand 'model'.
2. In the tree, expand 'model\Payments'.
3. In the tree, expand 'model\Payments\Initiating Party(InitiatingParty)'.
4. In the tree, select 'model\Payments\Initiating Party(InitiatingParty)\Name'.
5. In the tree, expand 'Excel\ReportHeader'.
6. In the tree, select 'Excel\ReportHeader\CompanyName'.
7. Click Bind.
8. In the tree, expand 'model\Payments\Creditor'.
9. In the tree, expand 'model\Payments\Creditor\Identification'.
10. In the tree, select 'model\Payments\Creditor\Identification\Source ID(SourceID)'.
11. In the tree, expand 'Excel\PaymLines'.
12. In the tree, select 'Excel\PaymLines\VendAccountName'.
13. Click Bind.
14. In the tree, select 'model\Payments\Creditor\Name'.
15. In the tree, select 'Excel\PaymLines\VendName'.
16. Click Bind.
17. In the tree, expand 'model\Payments\Creditor Agent(CreditorAgent)'.
18. In the tree, select 'model\Payments\Creditor Agent(CreditorAgent)\Name'.
19. In the tree, select 'Excel\PaymLines\Bank'.
20. Click Bind.
21. In the tree, select 'model\Payments\Creditor Agent(CreditorAgent)\Routing Number(RoutingNumber)'.
22. In the tree, select 'Excel\PaymLines\RoutingNumber'.
23. Click Bind.
24. In the tree, expand 'model\Payments\Creditor Account(CreditorAccount)'.
25. In the tree, expand 'model\Payments\Creditor Account(CreditorAccount)\Identification'.
26. In the tree, select 'model\Payments\Creditor Account(CreditorAccount)\Identification\Number'.
27. In the tree, select 'Excel\PaymLines\AccountNumber'.
28. Click Bind.
29. In the tree, select 'model\Payments\Instructed Amount(InstructedAmount)'.
30. In the tree, select 'Excel\PaymLines\Debit'.
31. Click Bind.
32. In the tree, expand 'model\Payments\Creditor'.
33. In the tree, expand 'model\Payments\Creditor Account(CreditorAccount)'.
34. In the tree, expand 'model\Payments\Creditor Agent(CreditorAgent)'.
35. In the tree, select 'model\Payments\Currency'.
36. In the tree, select 'Excel\PaymLines\Currency'.
37. Click Bind.
38. In the tree, expand 'PaymentByCurrency'.
39. In the tree, expand 'PaymentByCurrency\grouped'.
40. In the tree, select 'PaymentByCurrency\grouped\Currency'.
41. In the tree, expand 'Excel\SummaryLines'.
42. In the tree, select 'Excel\SummaryLines\SummaryCurrency'.
43. Click Bind.
44. In the tree, expand 'PaymentByCurrency\aggregated'.
45. In the tree, select 'PaymentByCurrency\aggregated\TotalInstructuredAmount'.
46. In the tree, select 'Excel\SummaryLines\SummaryAmount'.
47. Click Bind.
48. In the tree, select 'PaymentByCurrency'.
49. In the tree, select 'Excel\SummaryLines'.
50. Click Bind.
51. In the tree, select 'model\Payments'.
52. In the tree, select 'Excel\PaymLines'.
53. Click Bind.
54. Click Save.
55. Close the page.

## Use the created configuration for payments processing
1. Click Change status.
2. Click Complete.
3. Click OK.
4. Close the page.
5. Close the page.
6. Go to Accounts payable > Payment setup > Methods of payment.
7. Use the Quick Filter to filter on the Method of payment field with a value of 'Electronic'.
    * Electronic  
8. Click Edit.
9. Expand the File formats section.
10. Select Yes in the Generic electronic reporting field.
11. In the Export format configuration field, enter or select a value.
    * Select the ‘Sample worksheet report’ configuration.  
12. Click Save.
13. Close the page.

## Use the created configuration for testing of payment journals processing
1. Go to Accounts payable > Payments > Payment journal.
2. Click New.
    * Create a new payment journal.  
3. In the Name field, type 'VendPay'.
    * VendPay  
4. Click Lines.
5. In the Account field, specify the values 'GB_SI_000001'.
    * GB_SI_000001  
6. Set Debit to '1000'.
7. Click New.
8. In the Account field, specify the values 'GB_SI_000005'.
    * GB_SI_000005  
9. Set Debit to '2000'.
10. In the Currency field, type 'EUR'.
    * EUR  
11. In the Offset account field, specify the values 'GBSI OPER'.
    * GBSI OPER  
12. In the Method of payment field, type 'Electronic'.
    * Electronic  
13. Click Save.
14. Click Generate payments.
15. In the Method of payment field, type 'Electronic'.
    * Electronic  
16. In the File name field, type 'Payments'.
    * For example, type Payments.  
17. In the Bank account field, type 'GBSI OPER'.
    * GBSI OPER  
18. Click OK.
19. Click OK.
    * Review the created worksheet, including details of payment lines as well as totals for each currency code used in this payment message.  

