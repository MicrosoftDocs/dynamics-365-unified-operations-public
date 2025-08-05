---
title: Fixed asset depreciation
description: Learn about depreciation in Fixed assets, including outlines on depreciation adjustment, extraordinary depreciation, and special depreciation allowance.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 08/05/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: AssetBonus, AssetBookTable
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 98ff891f-e0e2-4184-b618-28107a50851f
---

# Fixed asset depreciation

[!include [banner](../includes/banner.md)]

This article provides an overview of depreciation in Fixed assets.

Depreciation is a periodic transaction that typically reduces the value of the fixed asset on the balance sheet, and is charged as an expenditure to a profit and loss account. Therefore, a main account is typically used to credit the periodic depreciation on the balance sheet. An offset account is an account in the profit and loss part of the chart of accounts.

## Depreciation adjustment
Usually, only a correction to a posted depreciation transaction is posted as a depreciation adjustment. Therefore, both the main account and the offset account are set up just like the accounts for depreciation. A depreciation adjustment can be either a positive amount or a negative amount, but the functionality of the main account (as a balance sheet account) and the functionality of the offset account (usually as a profit and loss account) remain the same.

## Extraordinary depreciation
Extraordinary depreciation works like basic depreciation. Therefore, a main account is used to credit the depreciation amount to the balance sheet and reduce the value of the fixed asset. An offset account is a profit and loss account, where the depreciation that is calculated for the fiscal period is charged as an expenditure. 

Extraordinary depreciation works independently of basic depreciation. By having extraordinary depreciation as a separate transaction type, you can post and report the extraordinary depreciation separately from the basic depreciation.

## Special depreciation allowance
You can use special depreciation allowances to take extra depreciation amounts during the first year that an asset is put in service and depreciated. Special depreciation allowances must be taken before any other depreciation calculations. Because special depreciation allowances are often unknown until later in the service life of the fixed asset, it's best to use this type of depreciation with a book that doesn't post to the general ledger. You can use the Delete transactions not posted to general ledger periodic function to delete the transaction history for these books. You can then delete the depreciation history for the fixed asset book, post the special depreciation allowance when it's known, and then post the remaining depreciation transactions for the year. 

You can create an unlimited number of special depreciation allowance records. After you assign those records to an asset group book, they are applied to the asset book. 

A special depreciation allowance is entered as either a percentage or a fixed amount. When you post depreciation proposals, special depreciation allowance transactions are posted to the book as transactions that are separate from the depreciation transactions.

## Depreciation calendars
Each book has a calendar that is used when you depreciate fixed assets. By default, if you don't indicate a calendar on the book, the book uses the ledger fiscal calendar. You must select a fiscal calendar for a book when the depreciation profile that is associated with the book uses a fiscal depreciation year. 

You can create shared calendars by using the **Fiscal calendars** page in General ledger.

For more information, see [Depreciation methods and conventions](depreciation-methods-conventions.md).


## Depreciation posting date
The **Depreciation posting date** field enforces consistent posting dates for depreciation transactions. The **Depreciation posting date** field is only available when the **Summary depreciation** option is set to **Yes**. When **Depreciation posting date** option is enabled, the system ensures that the posting date matches the defined depreciation date. If the defined date isn't the last day of the depreciation period, the system defaults to the final day of the previous period.

This behavior is especially beneficial in catch-up depreciation scenarios, where depreciation for prior periods are consolidated and posted on a single, consistent date. This contrasts with the default behavior, which may distribute postings across multiple dates. 

For example, an asset is acquired on January 1, 2021, and depreciation proposal is run on January 31 2025:
When the **Depreciation posting date** option is disabled, depreciation entries are posted at the end of each year, 12/31/2021 to 12/31/2024, resulting in multiple transactions across different dates.
When the option is enabled, all prior period depreciation entries are posted on a single, consistent date, 1/31/2025, simplifying catch-up scenarios by consolidating postings while maintaining period-specific descriptions.

>[!Note]
> This feature is only supported using the Straight Line – Service Life depreciation method. It's not available for localized versions.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
