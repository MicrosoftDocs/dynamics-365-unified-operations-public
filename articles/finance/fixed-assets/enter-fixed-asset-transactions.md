---
title: Fixed asset transaction options
description: Learn about the different methods available for creating fixed asset transactions, including outlines on Accounts payable and Accounts receivable.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 05/27/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: AssetTable, PurchCreateOrder
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 338c495b-a4d8-461e-b85b-a83faf673730
---

# Fixed asset transaction options

[!include [banner](../includes/banner.md)]

This article describes the different methods available for creating fixed asset transactions.

Set up fixed assets for integration with Accounts payable, Accounts receivable, Procurement and sourcing, and General ledger. You can also transfer items in Inventory management to fixed assets if you want to use those items internally.

## Accounts payable
Enter fixed asset transactions on the **Journal voucher** page. Open this page from the **Invoice journal** page. You can also open the **Journal voucher** page from the **Invoice approval journal** page. In the **Offset account type** field, select **Fixed assets**. Then, in the **Offset account** field, select a fixed asset number. On the **Fixed assets** tab, enter values in the **Transaction type** and **Book**   fields.

## Accounts receivable
Enter fixed asset transactions on the **Free text invoice** page. On the **Free text invoice** page, in the **Invoice lines** grid, select a line item. Select the **Line details** FastTab. Enter the fixed asset number and book for the disposal transaction. For free text invoices, the fixed asset transaction type is always Disposal - sale.

## Procurement and sourcing
Enter fixed asset transactions on the **Purchase orde**r page. Enter the required information to create a purchase order, and then select **OK**. On the **Purchase order** page, select the **Line details** FastTab. Then, on the **Fixed assets** tab, enter information about the fixed asset.  

To post an acquisition transaction for an existing fixed asset, specify the fixed asset number, book, and transaction type. The fixed asset can't be posted if any of this information is missing. To post an acquisition transaction for a new fixed asset, select the **New fixed asset?** option, and then select the fixed asset group to assign the new asset to. However, no fixed asset fields are available for a line if the item is in an inventory model group that uses a standard cost inventory model. Additionally, the options that are defined in the Fixed assets parameters page determine whether you can post acquisition transactions from the purchasing modules. 

When a purchase order or the Inventory to fixed assets journal is used to acquire fixed assets, the inventory value is affected.

## General ledger
Any fixed asset transaction type can be posted in the General journal page. You can also use journals in Fixed assets to post fixed asset transactions.

### Options for entering fixed asset transaction types


| Transaction type                    | Module                   | Options                                   |
|-------------------------------------|--------------------------|-------------------------------------------|
| Acquisition, Acquisition adjustment | Fixed assets             | Fixed assets, Inventory to fixed assets   |
|                                     | General ledger           | General journal                           |
|                                     | Accounts payable         | Invoice journal, Invoice approval journal |
|                                     | Procurement and sourcing | Purchase order                            |
| Depreciation                        | Fixed assets             | Fixed assets                              |
|                                     | General ledger           | General journal                           |
| Disposal                            | Fixed assets             | Fixed assets                              |
|                                     | General ledger           | General journal                           |
|                                     | Accounts receivable      | Free text invoice                         |

The remaining value isn't updated for the depreciation periods of a fixed asset when a depreciation transaction type journal line is created manually or imported through a data entity. The remaining value is updated when the depreciation proposal process is used to create the journal line.

For more information, see [Fixed assets integration](fixed-asset-integration.md).

The system prevents posting depreciation to the same period twice. For example, if two users create depreciation proposals separately for January, the depreciation from the first user posts in the first journal. When the second user posts depreciation in the second journal, the system checks the date that depreciation was last run and doesn't post depreciation for the same period a second time.

### Transactions that require a different voucher number

The following Fixed assets transactions will use different voucher numbers:

- You make an additional acquisition on an asset and calculate "catch-up" depreciation.
- You split an asset.
- You turn on a parameter to calculate depreciation on disposal, and then dispose of the asset.
- An asset's service date is before the acquisition date. Therefore, you post a depreciation adjustment.

> [!NOTE]
> When you enter transactions, make sure that all the transactions apply to the same fixed asset. You can't post a voucher if it includes more than one fixed asset, even if you set the **New voucher** field to **One voucher number only** on the **Journal names** page in General ledger. If you include more than one fixed asset in the voucher, you receive the message, "There can only be one fixed asset transaction per voucher," and you can't post the voucher.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
