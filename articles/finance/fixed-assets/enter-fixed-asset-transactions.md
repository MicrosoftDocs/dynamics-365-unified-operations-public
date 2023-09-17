---
# required metadata

title: Fixed asset transaction options
description: This article describes the different methods available for creating fixed asset transactions.
author: moaamer
ms.date: 08/10/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetTable, PurchCreateOrder
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 338c495b-a4d8-461e-b85b-a83faf673730
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Fixed asset transaction options

[!include [banner](../includes/banner.md)]

This article describes the different methods available for creating fixed asset transactions.

You can set up Fixed assets for integration with Accounts payable, Accounts receivable, Procurement and sourcing, and General ledger. You can also transfer items in Inventory management to Fixed assets if you want to use those items internally.

## Accounts payable
You can enter Fixed assets transactions in the Journal voucher page. This page can be opened from the Invoice journal page. You can also open the Journal voucher page from the Invoice approval journal page. In the Offset account type field, select Fixed assets. Then, in the Offset account field, select a fixed asset number. On the Fixed assets tab, enter values in the Transaction type and Book fields.

## Accounts receivable
You can enter Fixed assets transactions in the Free text invoice page.  In the Free text invoice page, in the Invoice lines grid, select a line item. Click the Line details FastTab. Enter the fixed asset number and book for the disposal transaction. For free text invoices, the fixed asset transaction type is always Disposal - sale.

## Procurement and sourcing
You can enter Fixed assets transactions in the Purchase order page. Enter the required information to create a purchase order, and then click OK. In the Purchase order page, click the Line details FastTab. Then, on the Fixed assets tab, enter information about the fixed asset. 

To post an acquisition transaction for an existing fixed asset, specify the fixed asset number, book, and transaction type. The fixed asset cannot be posted if any of this information is missing. To post an acquisition transaction for a new fixed asset, select the New fixed asset? option, and then select the fixed asset group to assign the new asset to. However, no fixed asset fields are available for a line if the item is in an inventory model group that uses a standard cost inventory model. Additionally, the options that are defined in the Fixed assets parameters page determine whether you can post acquisition transactions from the purchasing modules. 

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

The system prevents posting depreciation to the same period twice. For example, if two users create depreciation proposals separately for January, the depreciation from the first user will be posted in the first journal. When the second user posts depreciation in the second journal, the system checks the date that depreciation was last run and will not post depreciation for the same period a second time.

### Transactions that require a different voucher number

The following Fixed assets transactions will use different voucher numbers:

- An additional acquisition is made on an asset, and "catch-up" depreciation is calculated.
- An asset is split.
- A parameter to calculate depreciation on disposal is turned on, and then the asset is disposed of.
- An asset's service date is before the acquisition date. Therefore, a depreciation adjustment is posted.

> [!NOTE]
> When you enter transactions, be sure that all the transactions apply to the same fixed asset. A voucher won't be posted if it includes more than one fixed asset, even if the **New Voucher** field is set to **One voucher number only** on the **Journal names** page in General ledger. If you include more than one fixed asset in the voucher, the message you'll recieve the message, "There can only be one fixed asset transaction per voucher," and you won't be able to post the voucher.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
