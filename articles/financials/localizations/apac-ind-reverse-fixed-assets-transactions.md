---
# required metadata

title: Reversing fixed asset transactions for India
description:  This topic walks you through reversing a fixed asset transaction for India in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: AdamTrukawka
manager: AnnBe
ms.date: 12/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: atrukawk
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Reversing fixed asset transactions

[!include[banner](../includes/banner.md)]

You can reverse a fixed asset transaction, reverse direct and indirect taxes for the transaction, and update general ledger accounts. Information about the updated asset is displayed in the **Asset group balances** form for the selected tax layer book and depreciation.

You can reverse fixed asset acquisitions or acquisition adjustment transactions on which VAT were calculated. The posted VAT tax codes should also be reversed along with the fixed asset transaction entries. If the settlement process is already run for the original transaction period, the tax amounts which were posted to the VAT recoverable account at the time of posting the original
transaction should be reversed to the VAT payable account. All the indirect taxes for India, other than the VAT tax type, that is calculated and posted to the fixed asset at the time of posting the acquisition or acquisition adjustment transaction, are reversed as is when a fixed asset acquisition or acquisition adjustment transaction is reversed.

The **Companies Act depreciation** and the **Income tax Act depreciation** check boxes must be selected in the **General ledger parameters** form.

1. **Fixed assets** > Select a fixed asset line, and click **Books** > **Books**.

2. Select the book with a tax layer in the **Book** field.

3. Click **Transactions** to open the **Fixed asset transactions** page.

4. Select the transaction posted for acquisition to activate the **Reverse** > **transaction**.

5. Click **Reverse transaction** to open the **Transaction reversal** page.

6. Enter the **Reversal posting date**.

7. Click **OK** to reverse the transactions.

## Example 1

You can post multiple journals to account for the acquisition of fixed assets.

| Journal  | Value model | Fixed asset group | Fixed asset number | Amount    | Date of acquisition |
|----------|-------------|-------------------|--------------------|-----------|---------------------|
| 0001\_FA | VM1         | FAG1              | FA-001             | 75,000.00 | 01/01/2009          |
| 0002\_FA | VM1         | FAG2              | FA-002             | 65,000.00 | 01/01/2009          |
| 0003\_FA | VM1         | FAG3              | FA-003             | 35,000.00 | 01/01/2009          |

When you post the journals for value model 1 (VM1), the **Asset group balances** form displays the following details:

- The amount INR 175,000.00 (75,000.00 + 65,000.00 + 35,000.00) is displayed in the **Acquisition** field.

If you reverse the fixed asset FA-002 using the transaction reversal functionality, the **Acquisition** field on the **Asset group balances** page must display the amount as INR 110,000.00 (75,000.00 + 35,000.00).

The value of the reversed transaction must not be displayed on the **Asset group balances** page.

## Example 2

When the acquisition transaction that was reversed earlier is revoked, the revoked transaction appears again on the **Asset group balances** page.

With reference to Example 1, if you revoke the reversal of fixed asset FA-002 using transaction reversal, the **Acquisition** field on the **Asset group balances** page displays the amount as INR 175,000.00 (75,000.00 + 65,000.00 + 35,000.00)

The revoked transaction is updated back on the **Asset group balances** page.
