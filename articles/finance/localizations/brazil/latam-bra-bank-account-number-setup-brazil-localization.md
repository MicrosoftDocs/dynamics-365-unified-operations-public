---
title: Set up bank account numbers for Brazil
description: Learn how to set up bank account numbers for the Brazilian localization, including a step-by-step process for creating a bank account number in the require format.
author: ankviklis
ms.author: ankviklis
ms.topic: overview
ms.date: 03/03/2026
ms.custom:
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Brazil
ms.search.validFrom: 2022-01-20
ms.search.form: 
ms.dyn365.ops.version: 
---

# Set up bank account numbers for Brazil

[!include [banner](../../includes/banner.md)]

When you create a bank account, you must enter the bank account number in a specific format (mask). This mask includes all the attributes that are required to identify a bank account number according to the regulations from the Brazilian Central Bank.

Follow these steps to create a bank account number in the required format.

1. Go to **Cash and Bank Management** > **Bank accounts** > **Bank accounts**.
1. Select an existing bank account, or select **New** to create a new bank account.
1. In the **Bank account number** field, enter the bank account number in the following format:

    123 1234-1 012345678901-12

    Here's an explanation of the digits in the mask:

    - **123** – The bank code that the Brazilian Central Bank defines.
    - **1234** – The bank branch number.
    - **1** – The check digit for the bank branch number.
    - **012345678901** – The bank account number.
    - **12** – The check digit for the bank account number.

    > [!IMPORTANT]
    > You must include the spaces between the block of digits according to the mask. If the bank account number that you enter doesn't follow the mask, you receive the following validation message: "Invalid bank account format. Expected format is "&lt;Bank code&gt; &lt;branch number&gt; &lt;account number&gt;"."
    >
    > The localization design doesn't automatically extract the elements of the bank account number from the International Bank Account Number (IBAN) code. You must manually extract the elements and enter them in the **Bank account number** field.

1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]