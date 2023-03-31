---
title: ER Design domain specific data model
description: This article describes how to create a new Electronic reporting (ER) configuration that contains a data model for electronic payment documents.
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
ms.search.form: ERWorkspace, ERSolutionTable, ERSolutionCreateDropDialog, ERDataModelDesigner, ERDataModelContentsItemCreationDialog, ERDataContainerDescriptorReferenceSwitchDialog
---
# ER Design domain specific data model

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can create a new Electronic reporting (ER) configuration that contains a data model for electronic payment documents. This data model will later be used as a data source when you create the format of the payment documents.

In this example, you will create a configuration for sample company, Litware, Inc. These steps can be performed in any company as ER configurations are shared among companies. To complete these steps, you must first complete the steps in the "Create a configuration provider and mark it as active" procedure.

1. Go to Organization administration > Workspaces > Electronic reporting.

    Select the configuration provider for sample company, 'Litware, Inc.' If you don't see this configuration provider, you must first complete the steps in the "Create a configuration provider and mark it as active" procedure.  
    
2. Click Reporting configurations.

    You will create a configuration that contains a data model for electronic payment documents. This data model will be used later as a data source when you create the format for the payment documents.  

## Create a new data model configuration
1. Click Create configuration to open the drop dialog.
2. In the Name field, type 'Payments (simplified model)'.
3. In the Description field, type 'Payment model configuration'.

    The active configuration provider is automatically entered here. This provider will be able to maintain this configuration. Other providers can use this configuration, but will not be able to maintain it.  

4. Click 'Create configuration' button to complete the configuration creation task

## Create a data model
You're creating a new data model for the selected configuration. This configuration version will have a status of Draft.  
1. Click Designer.

## Define the structure of a party participating in a payment process
1. Click New to open the drop dialog.
2. In the Name field, type 'Party'.
3. Click Add.
4. Click New to open the drop dialog.
5. In the Name field, type 'Name'.
6. In the Item type field, select 'String'.
7. Click Add.
8. In the Find field, type 'Party'.
9. Click Find previous.

## Define the bank structure for this model
1. Click New to open the drop dialog.
2. In the Name field, type 'Agent'.
3. In the Item type field, select 'Record'.
4. Click Add.
5. In the Description field, enter 'Financial institution (for instance, a bank) servicing an account for the party (debtor/creditor).'.

    Financial institution (for instance, a bank) servicing an account for the party (debtor/creditor).  

6. Click New to open the drop dialog.
7. In the Name field, type 'Name'. 
8. In the Item type field, select 'String'.
9. Click Add.
10. Click New to open the drop dialog.
11. In the Name field, type 'SWIFT'.
12. Click Add.
13. In the Description field, enter 'Bank identification code'. 
14. Click New to open the drop dialog.
15. In the Name field, type 'RoutingNumber'.
16. Click Add.
17. In the Description field, enter 'Routing number'.
18. Click Find previous.

## Define the bank account structure for this model
1. Click New to open the drop dialog.
2. In the Name field, type 'Account'. 
3. In the Item type field, select 'Record'.
4. Click Add.
5. In the Description field, enter 'Identification of an account of a party in a financial institution (for instance, a bank).'.

    Identification of an account of a party in a financial institution (for instance, a bank).  

6. Click New to open the drop dialog.
7. In the Name field, type 'Currency'. 
8. In the Item type field, select 'String'.
9. Click Add.
10. In the Description field, enter 'Currency code'.
11. Click New to open the drop dialog.
12. In the Name field, type 'Number'. 
13. Click Add.
14. Click New to open the drop dialog.
15. In the Name field, type 'IBAN'. 
16. Click Add.
17. In the Description field, enter 'International bank account number'.

## Define the payment message structure for credit transfer payment type
1. Click New to open the drop dialog.
2. In the New node as a field, enter 'Model root'.
3. In the Name field, type 'CustomerCreditTransferInitiation'.
4. Click Add.
5. In the Find field, type 'CustomerCreditTransferInitiation'. 
6. Click Find previous.
7. Click New to open the drop dialog.
8. In the Name field, type 'MessageIdentification'. 
9. Click Add.
10. In the Description field, enter 'The point-to-point reference assigned by the instructing party (and sent to the next party) to identify a message.'.

    The point-to-point reference assigned by the instructing party (and sent to the next party) to identify a message.  

11. Click New to open the drop dialog.
12. In the Name field, type 'ProcessingDateTime'.
13. In the Item type field, select 'DateTime'.
14. Click Add.
15. In the Description field, enter 'Date and time at which the payment message was created.'. 
16. Click New to open the drop dialog.

    Define the payment transaction structure for this model.  

17. In the Name field, type 'Payments'.
18. In the Item type field, select 'Record list'.
19. Click Add.
20. In the Description field, enter 'Payment lines of the current message'.
21. Click New to open the drop dialog.
22. In the Name field, type 'Creditor'. 
23. In the Item type field, select 'Record'.
24. Click Add.
25. In the Description field, enter 'Party to which an amount of money is due.'. 
26. Click Switch item reference.
27. In the Find field, type 'Party'.
28. Click Find next.
29. Click OK.
30. In the Find field, type 'Payments'.
31. Click Find next.
32. Click New to open the drop dialog.
33. In the Name field, type 'Debtor'. 
34. Click Add.
35. In the Description field, enter 'Party that owes an amount of money to the (ultimate) creditor.'.
36. Click Switch item reference.
37. In the Find field, type 'Party'.
38. Click Find next.
39. Click OK.
40. Click Find next.
41. Click New to open the drop dialog.
42. In the Name field, type 'Description'.
43. In the Item type field, select 'String'.
44. Click Add.
45. Click New to open the drop dialog.
46. In the Name field, type 'Currency'.
47. Click Add.
48. In the Description field, enter 'Currency code'.
49. Click New to open the drop dialog.
50. In the Name field, type 'TransactionDate'. 
51. In the Item type field, select 'Date'.
52. Click Add.
53. In the Description field, enter 'Transaction date'. 
54. Click New to open the drop dialog.
55. In the Name field, type 'InstructedAmount'.  
56. In the Item type field, select 'Real'.
57. Click Add.
58. In the Description field, enter 'The amount of money to be moved between the debtor and creditor, before deduction of charges. The amount should be expressed in the currency as ordered by the initiating party.'.

    The amount of money to be moved between the debtor and creditor, before deduction of charges. The amount should be expressed in the currency as ordered by the initiating party.  

59. Click New to open the drop dialog.
60. In the Name field, type 'End2EndID'. 
61. In the Item type field, select 'String'.
62. Click Add.
63. In the Description field, enter 'The unique identification assigned by the initiating party. This identification is passed on, unchanged, throughout the entire end-to-end chain.'. 
64. In the Name field, type 'PaymentModel'.

    The PaymentModel name aligns with predefined interfaces of payment forms.  

65. Click Save.
66. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
