---
# required metadata

title: Create allocation rules and allocate depreciation costs | Microsoft Docs
description: This topic explains the process of creating allocation rules and allocating depreciation costs of fixed assets for Japan.
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-02 22:19:26
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 81
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 261434
ms.assetid: 4e186e80-f99f-40a9-b7fb-13757bb48b12
ms.region: China (PRC), Japan
# ms.industry: 
ms.author: leguo

---

# Create allocation rules and allocate depreciation costs

This topic explains the process of creating allocation rules and allocating depreciation costs of fixed assets for Japan.

You can set up an allocation rule to allocate the depreciation cost of a fixed asset to multiple cost accounts instead of the main cost account of your legal entity. An allocation rule can determine the percentage of the depreciation cost to assign to a cost account, and which cost account this percentage is assigned to. When you depreciate a fixed asset that is put into service for multiple operation units, such as departments or cost centers, Microsoft Dynamics AX can use the allocation rule to automatically calculate and allocate percentages of the depreciation cost to the individual cost accounts of the operation units.
Prerequisites
-------------

The following table shows the prerequisites that must be in place before you create allocation rules.

| Category            | Prerequisite                                                                                                                                                                                           |
|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Company information | Ensure that you have created a legal entity record for your organization. For more information, see Create or modify a legal entity.                                                                   |
| Accounting          | Create ledger accounts that the depreciation costs for operation units must be posted to. For more information, see About main accounts for fixed assets and Main accounts - chart of accounts (form). |
| Related setup tasks | Set up books for the fixed assets that you want to depreciate. For more information, see Set up books and Books(form).                                                                                 |

## Allocation rules
You can create allocation rules that are used to calculate and allocate a percentage of the total depreciation cost of a fixed asset. You can also specify ledger accounts to which the depreciation costs can be posted. Allocation rules can be assigned to a fixed asset posting profile of type Depreciation or Extraordinary depreciation.

## Calculate and allocate depreciation costs
After you set up allocation rules and assign them to a fixed asset posting profile, you can post the fixed asset journal voucher. When the depreciation proposal takes effect, the depreciation costs are calculated and allocated to the operation unit cost accounts. **Note:** You can also use the allocation rules for consumption depreciation proposals and extraordinary depreciation proposals.



See also
--------

[Allocation rules for fixed assets](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/asia-pacific/chn-jpn-allocation-rules-for-fixed-assets)

