--- 
title: Set up company bank accounts for ISO20022 credit transfers
description: Learn how to set up company-specific bank account information that's required to generate file payments, including a process for setting up IBAN and SWIFT codes. 
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

# Set up company bank accounts for ISO20022 credit transfers

[!include [banner](../../includes/banner.md)]

This article explains how to set up company-specific bank account information that's required to generate payment files. You set up information required to generate ISO 20022 credit transfer format but depending on the format, there might be other information required. This could include the **Company ID** or the **Sort code**. 

## Set up IBAN and SWIFT code
1. Go to **Cash and bank management** > **Bank accounts**.
2. Use the **Quick Filter** to filter on the **Bank account** field.
3. Select and double-click a record to open the bank account details.
4. Select **Edit**.
5. In the **Additional identification** section, enter a value in the **IBAN** field.
6. In the **SWIFT code** field, enter a value. A SWIFT\BIC isn't required for many payment formats, however we recommend that it's registered for a bank account.  
7. Select **Save**.

## Set up bank account for the legal entity
1. Go to **Organization administration** > **Organizations** > **Legal entities** and then select **Edit**.
2. In the **Bank account information** section, in the **Bank account** field, enter or select a value.
3. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
