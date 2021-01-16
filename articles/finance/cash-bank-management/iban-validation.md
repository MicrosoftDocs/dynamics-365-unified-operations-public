---
# required metadata

title: Manage International Bank Account Number (IBAN) account validation
description: This topic explains how to manage International Bank Account Number (IBAN) account validation.
author: mikefalkner
manager: aolson
ms.date: 08/24/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-08-30
ms.dyn365.ops.version: 8.0.4

---

# Manage International Bank Account Number (IBAN) account validation

[!include [banner](../includes/banner.md)]

International Bank Account Number (IBAN) validation increases the amount of validation that is done when you add an IBAN to a bank account.

Information about the structure of the IBAN is stored in Microsoft Dynamics 365 Finance. That information is automatically loaded when you first use the IBAN on bank accounts. It contains the length of the IBAN, the starting positions of the bank account number and the routing number, and the length of the bank account number and routing number.

## Set up IBAN structures

1. Go to **Cash and bank management \> Setup \> IBAN structures**.
2. Notice that the IBAN structures for each country or region have been set up automatically.
3. If you want to customize the structures for a specific country or region, you can edit them.
4. The structure definitions will be a part of each new release. You can use the **Reset structures** menu to load the latest definitions after each update.

## Validate the IBAN structure in a bank account

1. Go to **Cash and bank management \> Bank accounts \> Bank accounts**.
2. Create a bank account.
3. On the **Additional information** FastTab, enter an IBAN.

    If the length of the IBAN doesn't match the length that is defined for each country or region, you will receive a warning message. You can't continue if the length of the IBAN doesn't match the length specified in the IBAN structure.

    The validation also verifies that the bank account number matches the part of the IBAN that represents the bank account number. If the bank account number doesn't match, you will receive a warning message. This message is only a warning. You can continue even if the bank account number doesn't match.

    The validation also verifies that the bank routing number matches the part of the IBAN that represents the bank routing number. The routing number includes a bank number and often an additional bank branch. If the bank routing number doesn't match, you will receive a warning message. This message is only a warning. You can continue even if the bank routing number doesn't match.
