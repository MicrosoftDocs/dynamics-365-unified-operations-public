---
# required metadata

title: Create and post depreciation for a fixed asset group by using depreciation books for India
description: This topic walks you through the process of creating and posting depreciation for a fixed asset group by using depreciation books for India in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
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

# Create and post depreciation for a fixed asset group by using depreciation books

[!include[banner](../includes/banner.md)]

You can calculate depreciation for a group of fixed assets. The calculation is based on the number of days that is defined in the **Asset group depreciation threshold** field on the **General ledger parameters** page. The following table shows the various formulas that are used to calculate depreciation for asset groups.

| Type of proposal   | Number of days that the asset is used                                                        | Formula |
|--------------------|----------------------------------------------------------------------------------------------|---------|
| Depreciation       | Equal to or more than the number of days in the **Asset group depreciation threshold** field | (Net book value of the fixed asset group on the date of depreciation) × (Rate of depreciation that is defined for the depreciation profile) |
| Depreciation       | Less than the number of days in the **Asset group depreciation threshold** field             | (Net book value of the fixed asset) × (Depreciation threshold percentage that is defined in the parameters) × (Rate of depreciation that is defined for the depreciation profile) |
| Bonus depreciation | Equal to or more than the number of days in the **Asset group depreciation threshold** field | (Cost of acquisition) × (Rate of depreciation that is defined in the depreciation profile) |
| Bonus depreciation | Less than the number of days in the **Asset group depreciation threshold** field             | (Cost of acquisition) × (Depreciation threshold percentage that is defined on the **General ledger parameters** page) × (Rate of depreciation that is defined in the depreciation profile) |

## Example

On April 1, 2008, you own three fixed assets: Machinery A, Machinery B, and Machinery C. The written-down value of Machinery A is INR 70,000, the written-down value of Machinery B is INR 1,64,000, and the written-down value of Machinery C is INR 84,000. The rate of depreciation is 15 percent. On November 2, 2008, you purchase Machinery D for INR 60,000. Then, on March 15, 2009, you sell Machinery B for INR 1,80,000 and Machinery C for INR 40,000.

The calculated written-down value of the asset group on March 31, 2009, is INR 1,58,000 (INR 3,18,000 + INR 60,000 – INR 2,20,000). This value is calculated by adding the amount of the new machinery to the sum of the written-down value of Machinery A, Machinery B, and Machinery C, and then deducting the proceeds from the sale of Machinery B and Machinery C.

You must calculate depreciation on the asset that is used for fewer than 180 days at a rate of 7.5 percent. In this case, the depreciation is INR 4,500 (INR 60,000 × 7.5%). The depreciation on the remaining amount of the written-down value of the asset group is calculated at a rate of 15 percent. In this case, the depreciation is INR 14,700.

On March 31, 2009, you must deduct the amount of depreciation from the written-down value of the group of assets (INR 1,58,000 – INR 60,000 = INR 98,000) to calculate the written-down value of the asset group on April 1, 2008. In this case, the written-down value is INR 1,38,800 (INR 1,58,000 – INR 19,200).

Depreciation isn't calculated for an asset group that has a written-down value of 0 (zero). If the sale amount of all or some assets in a fixed asset group exceeds the net book value of the group during a year, this situation is considered a short-term capital gain. Therefore, the asset group will have a written-down value of 0 (zero). If the sale amount of all assets in a fixed asset group is less than the net book value of the fixed asset group, this situation is considered a short-term capital loss. Therefore, the asset group will have a written-down value of 0 (zero).

If a positive or negative amount is entered in the **Debit** field on a journal line, the same amount is updated on the **Fixed asset balances** page. However, if a positive amount is entered in the **Credit** field, the amount is updated as a negative amount. This negative amount is then updated as a positive amount on the **Fixed asset balances** page.

## Create and post a depreciation book journal

1. On the **Depreciation book journal** page, create a new depreciation book journal.
2. In the **Name** field, select a journal name for the depreciation book journal.
3. Select **Lines**.
4. In the **Transaction type** field, select a transaction type.
5. In the **Fixed asset number** field, select a fixed asset number.

    > [!NOTE]
    > The **Fixed asset number** field isn't available on a journal line if the fixed asset group and depreciation book that are selected have the **Depreciation** or **Depreciation adjustment** transaction type, and if the **Asset group depreciation** check box is selected.

6. In the **Fixed asset group** field, select a fixed asset group.
7. In either the **Debit** field or the **Credit** field, enter an amount.
8. Select **Proposals** to generate different types of proposals for fixed asset groups that the **Asset group depreciation** check box has been selected for, and then select **OK**. You can create an acquisition, depreciation, revaluation, or bonus depreciation proposal.
9. Select **Post** to post the journal, or post lines that have no errors and transfer the lines that have errors to a new journal. 

    The totals of the amounts that are entered for fixed asset numbers that have the same fixed asset group and the same transaction type are updated on the **Fixed asset balances** page. (On the **Fixed assets** page, select a fixed asset. On the Action Pane, select **Depreciation books**. Select a depreciation book, and then select **Inquiry** &gt; **Balance**.)

    For example, you post a journal voucher of the acquisition type for fixed asset numbers Book 1 and Book 2 in a fixed asset group. You enter INR 20,000.00 for Book 1 and INR 30,000.00 for Book 2. In this case, the total amount, INR 50,000.00, is shown in the **Acquisition** field on the **Fixed asset balances** page.

    A new journal line is created for the proposal type, and the amount that is entered in the **Debit** field or the **Credit** field is updated on the **Fixed asset balances** page. (On the **Fixed assets** page, select a fixed asset. On the Action Pane, select **Depreciation books**. Select a depreciation book, and then select **Inquiry** &gt; **Balance**.)

    > [!NOTE]
    > Asset group depreciation doesn't apply to proposals of the **Consumption depreciation**, **Revenue recognition of reserves**, or **Extraordinary depreciation** type.
