--- 
# required metadata 
 
title: Set up company bank accounts for ISO20022 direct debits
description: This article explains how to set up company-specific bank account information that's required to generate customer payment files. 
author: mrolecki
ms.date: 08/01/2023
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

TThis article explains how to set up company-specific bank account information that's required to generate customer payment files.

## Set up the IBAN and SWIFT codes
1. Go to **Cash and bank management** > **Bank accounts**.
2. Use the **Quick Filter** to filter on the **Bank account** field..
3. In the list, select a row and then select the link in the row.  
4. Select **Edit**.
5. In the **Additional identification** section, in the **IBAN** field, enter a value.
6. In the **SWIFT code** field, enter a value. For many payment formats, SWIFT\BIC isn't required, however we recommend it be registered for a bank account.  
7. Select **Save**.

## Set up a bank account for the legal entity
1. Go to **Organization administration** > **Organizations** > **Legal entities** and select **Edit**.
2. In the **Bank account information** section, in the **Bank account** field, select a value.
3. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
