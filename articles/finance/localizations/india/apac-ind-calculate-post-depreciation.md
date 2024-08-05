---
title: Create and post depreciation for a fixed asset group by using depreciation books
description: Learn about the process of creating and posting depreciation for a fixed asset group by using depreciation books for India in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 01/05/2018
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3
---

# Create and post depreciation for a fixed asset group by using depreciation books

[!include [banner](../../includes/banner.md)]

You can calculate depreciation for a group of fixed assets. The calculation is based on the number of days that is defined in the **Asset group depreciation threshold** field on the **Fixed assets parameters** page. The following table shows the various formulas that are used to calculate depreciation for asset groups.

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

## Create and post fixed asset depreciation in journal

1. Create a new **Fixed asset journal** to post depreciation transaction.
2. In the **Name** field, select journal for posting depreciation.
3. Select **Lines** and add new line.
4. In the **Transaction type** field, select **Depreciation** transaction type.
5. In the **Account** field, select a fixed asset.

    > [!NOTE]
    > The **Fixed asset number** field isn't available in a journal line if the **Asset group depreciation** is set to **Yes** in fixed asset book.

6. In the **Fixed asset group** field, select a fixed asset group.
7. Enter depreciation amount in the **Credit** field.
8. Select **Post** to post the journal.
9. Click **Fixed assets** > **Fixed assets** > Select a fixed asset > **Books** tab on Action Pane.
10. Click **Transactions** and notice that the depreciation amount was posted for the fixed asset group without the specification of an asset.
11. Close the **Fixed assets transactions** page.
12. Click **Inquiry** > **Asset group balances** and notice that the total depreciation amount was posted for the asset group in the selected book.

    > [!NOTE]
    > In the journal you can use the **Proposal** function for various proposal types to create transactions for fixed asset groups. Asset group depreciation doesn't apply to proposals of the **Consumption depreciation**, **Revenue recognition of reserves**, or **Extraordinary depreciation** type.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
