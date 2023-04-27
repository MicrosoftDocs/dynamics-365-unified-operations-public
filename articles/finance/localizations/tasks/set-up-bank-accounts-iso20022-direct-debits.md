--- 
# required metadata 
 
title: Set up customers and customer bank accounts for ISO20022 direct debits
description: This task walks you through setting up a customer bank account and a customer direct debit mandate which are required to generate the customer payment file like ISO20022 direct debit. 
author: mrolecki
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustTable, CustBankAccounts, CustDirectDebitMandate, BankAccountTableLookUp,  LogisticsAddressCityLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up customers and customer bank accounts for ISO20022 direct debits

[!include [banner](../../includes/banner.md)]

This task walks you through setting up a customer bank account and a customer direct debit mandate which are required to generate the customer payment file like ISO20022 direct debit. Depending on the customer payment formats tha are set up, additional information, not covered in this procedure, might be required for a customer or a customer bank account. 

This task was created using the demo data company DEMF with a legal entity primary address in Germany.



This is the fourth of five procedures that demonstrate the customer payment process using electronic reporting configurations.


## Set up a customer bank account
1. Go to Accounts receivable > Customers > All customers.
2. Use the Quick Filter to find records. For example, filter on the Account field with a value of 'DE-010 '.
3. In the list, click the link in the selected row.
4. On the Action Pane, click Customer.
5. Click Bank accounts.
6. Click New.
7. In the Bank account field, type a value.
8. In the Name field, type a value.
    * For example, enter 'EUR bank'.  
9. In the Bank groups field, enter or select a value.
10. In the IBAN field, type a value.
    * For example, enter 'DE36200400000628808808'.  
11. In the SWIFT code field, type a value.
    * For example: Enter 'COBADEFFXXX'.  Please note that SWIFT \ BIC is not mandatory for many payment formats however it is recommended to have it registered for a bank account.  
12. Click Save.
13. Close the page.
14. Click Edit.
15. Expand the Payment defaults section.
16. In the Bank account field, enter or select a value.

## Add a direct debit mandate
1. Expand the Direct debit mandates section.
2. Click Add.
3. In the Creditor bank account field, enter or select a value.
    * For example, select DEMF OPER.  
4. In the Signature date field, enter a date.
5. Click Yes to confirm the date update.
6. In the Signature location field, enter or select a value.
7. In the Expected number of payments field, enter a number.
8. Click OK.
9. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]