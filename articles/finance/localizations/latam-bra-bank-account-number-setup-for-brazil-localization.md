---
# required metadata

title: Bank account number setup for Brazil Localization
description: This topic explains how to set up bank account numbers for Brazil.
author: gionoder
ms.date: 07/25/2019
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: gionoder
ms.search.validFrom: 2022-01-20
ms.dyn365.ops.version: 

---

# Bank account number setup for Brazil Localization

[!include [banner](../includes/banner.md)]

When creating a bank account, the bank account number must be entered following a specific mask that encompasses the necessary attributes to identify a bank account number according to the regulations from the Brazilian Central Bank.

Complete the following steps to create a bank account number as required.

1. Go to **Cash and Bank Management** > **Bank accounts** > **Bank accounts**.
2. Select an existing bank account or select **New** to create a new one.
3. In the **Bank account number** field, enter the bank account number in the following format.

   123 1234-1 012345678901-12

   Where:

   - **123** is the bank code as defined by the Brazilian Central Bank.
   - **1234** is the bank branch.
   - **1** is the check digit for the bank branch.
   - **012345678901** is the bank account number.
   - **12** is the check digit for the bank account number.

4. Select **Save**.

> [!NOTE]
> The spaces between the block of digits must be provided according to the mask. When the bank account number that is entered doesn't comply with the mask, the following validation message occurs, **Invalid bank account format. Expected format is "&lt;Bank code&gt; &lt;branch number&gt; &lt;account number&gt;**.
>
> The localization design doesn't extract those bank account number elements automatically from the IBAN code. The elements must be manually extracted and entered in the **Bank account number**.
