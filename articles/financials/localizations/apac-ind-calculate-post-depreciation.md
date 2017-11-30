---
# required metadata

title: Create and post depreciation for a fixed asset group using depreciation books for India
description:  This topic for India in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
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

# Create and post depreciation for a fixed asset group using depreciation books
[!include[banner](../includes/banner.md)]

You can calculate depreciation for a fixed asset group based on the number of days defined in the **Asset group depreciation threshold** field in the **General ledger parameters** page. The following table shows the various formulas that are used to calculate asset group depreciation.

| Type of proposal   | Number of days the asset is used   | Formula    |
|--------------------|-----------|----------------------------|
| Depreciation       | Equal to or more than the number of days defined in the **Asset group depreciation threshold** field | (Net book value of the fixed asset group on the date of depreciation) \* (Rate of depreciation defined for the depreciation profile)                                         |
| Depreciation       | Fewer than the number of days defined in the **Asset group depreciation threshold** field            | (Net book value of the fixed asset) \* (Depreciation threshold percentage defined in parameters) \* (Rate of depreciation defined for the depreciation profile)              |
| Bonus depreciation | Equal to or more than the number of days defined in the **Asset group depreciation threshold** field | (Cost of acquisition) \* (Rate of depreciation defined in the depreciation profile)                                                                                          |
| Bonus depreciation | Fewer than the number of days defined in the **Asset group depreciation threshold** field            | (Cost of acquisition) \* (Depreciation threshold percentage defined in the **General ledger parameters** form) \* (Rate of depreciation defined in the depreciation profile) |

**Example**

You own Machinery A, B, and C on April 1, 2008. The written-down value of machinery A is INR 70,000, Machinery B is INR 1,64,000, and Machinery C is INR 84,000. The rate of depreciation is 15 percent. You purchased Machinery D for INR 60,000 on November 2, 2008. On March 15, 2009, Machinery B is sold for INR 1,80,000 and Machinery C is sold for INR 40,000.

The calculated written-down value of the group of assets on March 31, 2009 = INR 1,58,000 (INR 3,18,000 + INR 60,000 – INR 2,20,000). This is calculated by adding the amount of the new machinery to the sum of the written-down value of Machinery A, B, and C and then deducting the sale proceeds of Machinery B and C.

You must calculate depreciation on the asset that is used for fewer than 180 days at the rate of 7.5 percent, which in this case is INR 4,500 (INR 60,000 \*7.5%). The depreciation on the remaining amount of the written-down value of the group of assets is calculated at the rate of 15 percent, which is INR 14,700.

On March 31, 2009, you must deduct the amount of depreciation from the written-down value of the group of assets (INR 1,58,000 – INR 60,000 = INR 98,000) to calculate the written-down value of the group of assets on April 1, 2008, which is INR 1,58,000 – INR 19,200 = INR 1,38,800.

Depreciation is not calculated for the asset group that has a zero written-down value. If the sale amount of all assets or some assets in a fixed asset group is greater than the net book value of the group during a year, it is considered a short-term capital gain, so it will have a zero written-down value. If the sale amount of all assets in a fixed asset group is less than the net book value of
the fixed asset group, it is considered a short-term capital loss, so it will have a zero written-down value.

If the positive or negative amount is entered in the **Debit** field of a journal line, the same amount is updated in the **Fixed asset balances** form. However, if a positive amount is entered in the **Credit** field, the amount is updated as negative and the negative amount in the **Credit** field is updated as a positive amount in the **Fixed asset balances** form.

## Create and post a depreciation book journal

1.   Go to the **Depreciation book journal** page.
2.   Create a new depreciation book journal.
3.   Select a depreciation book journal name in the **Name** field.
4.   Click **Lines**.
5.   Select a transaction type in the **Transaction type** field.
6.   Select a fixed asset number in the **Fixed asset number** field.
      > [!NOTE]
      > The **Fixed asset number** field is not available in the journal line when a fixed asset group and depreciation book is selected with the **Depreciation** or **Depreciation adjustment** transaction type, and the **Asset group depreciation** check box is selected.
7.   Select a fixed asset group in the **Fixed asset group** field.
8.   Enter an amount in the **Debit** field or the **Credit** field.
9.   Click **Proposals** to generate different types of proposals for fixed asset groups for which the **Asset group depreciation** check box has been selected, and then click **OK**. You can create an acquisition, depreciation, revaluation, or bonus depreciation proposal.
10.   Click **Post** to post the journal, or post lines with no errors and transfer the lines with errors to a new journal. 

      The totals of the amounts that are entered for the fixed asset numbers with the same fixed asset group and transaction type are updated in the **Fixed asset balances** page (**Fixed assets** > Select a fixed asset. On the **Action Pane**, click **Depreciation books**. Select a depreciation book and then click **Inquiry** > **Balance**).

      For example, if you post an acquisition type of journal voucher for fixed asset numbers Book 1 and Book 2 in a fixed asset group. You enter INR 20,000.00 for Book 1 and INR 30,000.00 for Book 2. The total amount of INR 50,000.00 is displayed in the **Acquisition** field of the **Fixed asset balances** form.

      A new journal line is created for the proposal type, and the amount that is entered in the **Debit** field or the **Credit** field is updated in the **Fixed asset balances** form (**Fixed assets** > Select a fixed asset. On the **Action Pane**, click **Depreciation books**. Select a depreciation book and then click **Inquiry** > **Balance**).

      > [!NOTE]
      > Asset group depreciation is not applicable for **Consumption depreciation**, **Revenue recognition of reserves**, and **Extraordinary depreciation** types of proposals.
