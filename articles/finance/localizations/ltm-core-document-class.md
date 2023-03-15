---
title: Document class for Latin America 
description: This topic provides information about the document class configuration for Latin America. 
author: Fhernandez0088
ms.date: 03/15/2022
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---
# Document classes for Latin America
You will be able to create the different documents with which the company register their transactions with third parties (invoices, credit notes, debit notes, etc.).
These documents can also represent payment methods (checks, wire transfers, etc.) and treasury documents (receipts, payment orders, etc.).
## Prerequisites
The following prerequisites must be met before setting up document classes:
- The prefix lengths must be set in **LATAM Parameters**.
- Sales point must be created.
- At least a bank must be created and configured to be used in a document class.
- Journals must be created to be assigned in document classes.
- **Document class letters** must be previously created.
- **Document class types** must be previously created.

## Set up a Document class
1. Go to **Organization administration > Setup > LATAM > Document class**
2. Select **New** from the action pane.
3. In the **General** section complete the following:

| Field                         | Description                                                                                                                                                                                                                  |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Document class Id             | This field must be completed with a code to identify the document class created, it must be unique.                                                                                                                          |
| Description                   | Must add a brief description.                                                                                                                                                                                                |
| Legal Description             | Complete this field with a text to be printed in a legal document.                                                                                                                                                           |
| Document class type Id.       | Select a document class type from the list.                                                                                                                                                                                  |
| Document class letter Id      | Select a document class letter from the list.                                                                                                                                                                                |
| Prefix                        | Enter a prefix to be used in the complete document number.                                                                                                                                                                   |
| Inactive                      | Activate this slider to make the document class invisible when postin transactions.                                                                                                                                          |
| Apply withholding calculation | Activate this slider to enable the withholding calculation on the document class.                                                                                                                                            |
| Original exchange rate        | Activate this slider to not generate currency exchange rate differences in payments.                                                                                                                                         |
| Document number separator     | Enter a character to be used as the document number separator prefixes-salespoint.                                                                                                                                           |
| Copy document number in       | Select an option form this field to copy the document number generated to the native fields 'Invoice' and/or 'Document number'.                                                                                              |
| Require AC number             | Activate this slider to make the AC number mandatory when posting a transaction.                                                                                                                                             |
| Concept labels 1, 2, 3        | Complete the labels if necessary for the fields in LATAM information when posting a transaction.                                                                                                                             |
| Require control code          | Activate the control code if necessary.                                                                                                                                                                                      |
| Type of control code          | Choose between automatic and manual.                                                                                                                                                                                         |
| Report/Service Id.            | Select an option if necessary for docucment printing.                                                                                                                                                                        |
| Bank transaction type         | Choose a transaction type when creating a payment method that has an impact on bank accounts.                                                                                                                                |
| Notes 1, 2, 3                 | Enter a text to include in the document printing if necessary.                                                                                                                                                               |
| Details Taxpayer              | Enable this option to make the tax related information mandatory when posting a transaction.                                                                                                                                 |
| Document with tax             | When enabled no more than one line of the vendor/client type with this document class assigned can be created in a journal. When enabled there can't be two or more lines with foreign currency and different exchange rate. |
4. If the **Document class type** is not a payment method proceed to **step 6**.
If the **Document class type** is a payment method complete the following from the **Payment method type** section:

| Field                    | Description                                                                                           |
|--------------------------|-------------------------------------------------------------------------------------------------------|
| Payment method type      | Select an option from the list that represents the document created.                                  |
| Entry action             | Enable this to allow the 'Entry' action in the payment journal (i.e., third-party check reception).   |
| Exit action              | Enable this to allow the 'Exit' action in the payment journal (i.e., third-party check deposit).      |
| Re-entry action          | Enable this to allow the 'Re-entry' action in the payment journal (i.e., third-party check rejected). |
| Emission action          | Enable this to allow the 'Emission' action in the payment journal (i.e., own check emission).         |
| Accrual action           | Enable this to allow the 'Accrual' action in the payment journal (i.e., deferred checks accrual).     |
| Cancellation action      | Enable this to allow the 'Accrual' action in the payment journal (i.e., deferred checks accrual).     |
| Posting profile          | Select the posting profile to be used when posting a transaction with the document class.             |
| Enable currency exchange | Enables changing default currency when posting a transaction.                                         |
| Currency                 | Select the default currency for the payment method.                                                   |
| Require deferred date    | Requires the due date to be higher than the emission date.                                            |
5. When configuring a payment method, you must add at least one bank to the **Bank accounts** grid to be used.
6. Add at least one journal name to the grid **Journal names** to be used when posting a transaction with the document class.
7. In the **Additional data** section enable, make mandatory or disable the required fields to be shown in the **LATAM** information section when posting a transaction.
8. In the **Document mask** section enable the sales point required and configure the format mask for them.
9. In the **Dimensions** section select the predetermined dimensions desired that will be applied to the voucher lines when posting a transaction.

## Add the fiscal codification provided by the fiscal authorities

You can use **Tax application** option to add this codification.

1.	Go to **Navigation pane > Organization administration > Setup > LATAM > Document class**.
2.	Select the **Tax application** button on the action pane.
3.	Select **New** to add a line to the grid.
4.	In the **Tax application Id.** field select a value from the list.
5.	In the **Tax application code field** type the code with which the fiscal authority identifies the document class type.
6.	Select **Save**.

