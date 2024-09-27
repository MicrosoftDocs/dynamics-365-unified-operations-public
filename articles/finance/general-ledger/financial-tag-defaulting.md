---
title: Financial tag rules 
description: Learn about financial tags rules, including outlines on setup, the process of creating financial tag rules, and defaulting financial tag values on transactions using copilot with PowerFx formulas
author: rcarlson
ms.author: rcarlson
ms.topic: article
ms.date: 10/27/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-03-23
ms.search.form: DimensionFocus, LedgerTrialBalanceListPage, FinTagRule, FinancialTags
ms.dyn365.ops.version: 10.0.42
---

# Financial tag rules

Financial tag rules provide a powerful way to default or automatically populate values onto your [Financial tags](financial-tag.md). Enable this functionality with the new feature **Financial tag defaulting rules** found in feature management starting with 10.0.42. 

The **Financial tags rules** feature provides a .

Financial tag rules were introduced in the 10.0.42 release of Dynamics 365 Finance. In each new release, more document entry points will be implemented. In the 10.0.37 release, the following journals are supported for financial tag rules:

- General journal
- Global general journal | *NOTE: the setup of financial tag rules is common for the General journal and Global general journal.*
- Allocation journal
- Reporting currency adjustment journal
- Invoice journal (vendor)
    > [!NOTE]
    > ?? do I need to note anything?

## Setup

To use the functionality, you must enable the **Financial tag defaulting rules** feature in the **Feature management** workspace. The feature can be disabled at any time. If the feature is enabled but later disabled, any rules defined for financial tags will be maintained in the database. However, they'll no longer be used on any transactions in Dynamics 365 Finance.

In addition at least one [Financial tags](financial-tag.md) must be setup in the company you are creating a rule in before the financial tag rules form can be used.

## Creating financial tag rules

Before you create financial tags rules, note the following points:
- System rules already exist to mimic the behavior already running for documets.  In journal entry, tag header values will be copied to the account tag field, and account tag values will be copied to the offset account tag field by these system rules. You may enable or disable these as needed, but you cannot remove them from the system or modify them in any way.
- [Power Fx](https://learn.microsoft.com/en-us/power-platform/power-fx/overview) us the language used for defining and executing the financial tag rules. You may want to spend some time getting familiar with the [formulas](https://learn.microsoft.com/en-us/power-platform/power-fx/formula-reference-overview) available, however not all will be supported for Dynamics 365 Finance.
- 

### Create a financial tag rule

Follow these steps to create a financial tag rule.

1. Go to **General ledger \> Chart of accounts \> Financial tags \> Financial tags**.
2. Select **New** to create a financial tag

## Understanding how financial tag values can be set on transactions


*fix everything that are examples below here*
  
### Journals and lines

[![Financial tags entered on the journal batch header.](./media/Financial-tag1.png)](./media/Financial-tag1.png)

### Default values for journals

1. Tag values can be defined on the header of the document.
2. Tag values from the header are used as default values on the lines of the document.
3. Tag values from the lines of the document are used as default values in the accounting distributions (if the document is a source document and supports accounting distributions).


