--- 
# required metadata 
 
title: Set up company bank accounts for ISO20022 direct debits
description: This task walks you through setting up the company specific bank account information that is required for generating customer payment files. 
author: mrolecki
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: BankAccountTable, OMLegalEntity, BankAccountTableLookUp   
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
# Set up company bank accounts for ISO20022 direct debits

[!include [banner](../../includes/banner.md)]

This task walks you through setting up the company specific bank account information that is required for generating customer payment files. This procedure uses the ISO 20022 direct debit format as an example. Other formats might require additional setup information like the Company ID or the Sort code.



This task was created using the demo data company DEMF.



This is the second of five procedures that demonstrate the customer payment process using electronic reporting configurations.


## Set up the IBAN and SWIFT codes
1. Go to Cash and bank management > Bank accounts.
2. Use the Quick Filter to filter on the Bank account field with a value of 'DEMF OPER'.
3. In the list, click the link in the selected row.
    * For example, click 'DEMF OPER' to open the bank account details.  
4. Click Edit.
5. Expand or collapse the Additional identification section.
6. In the IBAN field, type a value.
    * For example, enter 'DE89370400440532013000'.  
7. In the SWIFT code field, type a value.
    * For example, enter 'DEUTDEFF'.    Please note that SWIFT \ BIC is not mandatory for many payment formats however it is recommended to have it registered for a bank account.  
8. Click Save.

## Set up a bank account for the legal entity
1. Go to Organization administration > Organizations > Legal entities.
2. Click Edit.
3. Expand or collapse the Bank account information section.
4. In the Bank account field, click the drop-down button to open the lookup.
5. In the list, click the link in the selected row.
    * For example, select the "DEMF OPER" bank account.  
6. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]