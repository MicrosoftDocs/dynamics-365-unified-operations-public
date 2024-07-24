--- 
title: Set up company bank accounts for ISO20022 direct debits
description: Learn how to set up company-specific bank account information, such as IBAN and SWIFT codes, that's required to generate customer payment files. 
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/01/2023
ms.reviewer: johnmichalak   
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: BankAccountTable, OMLegalEntity, BankAccountTableLookUp
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
