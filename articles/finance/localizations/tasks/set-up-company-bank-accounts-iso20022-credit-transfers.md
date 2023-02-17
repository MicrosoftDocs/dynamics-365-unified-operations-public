--- 
# required metadata 
 
title: Set up company bank accounts for ISO20022 credit transfers
description: This procedure shows how to set up company-specific bank account information that is required for payment file generation. 
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
# Set up company bank accounts for ISO20022 credit transfers

[!include [banner](../../includes/banner.md)]

This procedure shows how to set up company-specific bank account information that is required for payment file generation. You set up information required to generate ISO 20022 credit transfer format but depending on the format there might be other information required, such as the Company ID or the Sort code. 

The demo data company used to create this procedure is DEMF.

This is the second procedure, out of five, that illustrates the vendor payment process using electronic reporting configurations. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Set up IBAN and SWIFT code
1. Go to Cash and bank management > Bank accounts.
2. Use the Quick Filter to filter on the Bank account field with a value of 'DEMF OPER'.
3. Click DEMF OPER to open bank account details.
4. Click Edit.
5. Expand the Additional identification section.
6. In the IBAN field, type 'DE89370400440532013000'.
7. In the SWIFT code field, type 'DEUTDEFF'.
    * Note that SWIFT\BIC is not required for many payment formats, however it is recommended to have it registered for a bank account.  
8. Click Save.

## Set up bank account for the legal entity
1. Go to Organization administration > Organizations > Legal entities.
2. Click Edit.
3. Expand the Bank account information section.
4. In the Bank account field, enter or select a value.
5. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]