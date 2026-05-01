--- 
title: Set up company bank accounts for ISO20022 direct debits
description: Learn how to set up company-specific bank account information, such as IBAN and SWIFT codes, that's required to generate customer payment files. 
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak   
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: BankAccountTable, OMLegalEntity, BankAccountTableLookUp
---

# Set up company bank accounts for ISO20022 direct debits

[!include [banner](../../includes/banner.md)]

This article explains how to set up company-specific bank account information that's required to generate customer payment files.

## Set up the IBAN and SWIFT codes

1. Go to **Cash and bank management** > **Bank accounts**.
1. Use the **Quick Filter** to filter on the **Bank account** field.
1. In the list, select a row and then select the link in the row.  
1. Select **Edit**.
1. In the **Additional identification** section, enter a value in the **IBAN** field.
1. Enter a value in the **SWIFT code** field. For many payment formats, SWIFT/BIC isn't required, but register it for a bank account.  
1. Select **Save**.

## Set up a bank account for the legal entity

1. Go to **Organization administration** > **Organizations** > **Legal entities** and select **Edit**.
1. In the **Bank account information** section, select a value in the **Bank account** field.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
