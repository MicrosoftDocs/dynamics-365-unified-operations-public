---
# required metadata

title: Set up global withholding tax
description: This article lists the steps for setting up global withholding tax for sales and purchases. 

author: kailiang
ms.date: 01/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# 
# ms.tgt_pltfrm: 
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2020-01-12
ms.dyn365.ops.version: AX 10.0.17

---

# Set up global withholding tax

This article lists the steps for setting up global withholding tax for sales and purchases. 

1. Set up withholding tax authorities on the **Withholding tax authorities** page.

2. Set up withholding settlement periods on the **Withholding tax settlement periods** page.

3. Set up withholding ledger posting group on the **Withholding tax > ledger posting group** page.

   > [!Note] 
   >
   > **Withholding tax** account will be assigned with a main account with **Posting type** of Withholding tax. **Withholding tax offset** account will also be assigned with a main account with **Posting type** "Withholding tax offset". Go to **General ledger > Chart of accounts > Accounts > Main accounts**, set up the **Posting type** in the **Posting validation** sub-form for the main accounts.

4. Set up withholding tax codes on the **Withholding tax codes** page.

5. Set up withholding tax groups on the **Withholding tax groups** page.

6. Set up withholding tax revenue types on the **Withholding tax revenue** **types** page.

7. Set up withholding tax groups on the **Item withholding tax groups** page for an item or service.

8. Set up **Minimum invoice amount** on the **General ledger parameters > Withholding tax** page.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
