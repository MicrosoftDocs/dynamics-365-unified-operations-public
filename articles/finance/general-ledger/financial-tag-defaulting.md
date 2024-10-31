---
title: Financial tag rules 
description: Learn about setting up, creating, defaulting financial tags on transactions.
author: rcarlson
ms.author: rcarlson
ms.topic: article
ms.date: 10/31/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-03-23
ms.search.form: DimensionFocus, LedgerTrialBalanceListPage, FinTagRule, FinancialTags
ms.dyn365.ops.version: 10.0.42
---

# Financial tag rules

Financial tag rules provide a powerful way to default or automatically populate values onto your [Financial tags](financial-tag.md).  This streamlines the process, ensuring consistency and efficiency in transaction tagging, which is essential for accurate financial tracking and reporting. This featue is available starting in Dynamics 365 Finance version 10.0.42 and in feature management.
In each new release, more document entry points will be implemented. 

Currently, the following journals are supported for financial tag rules:

- General journal
- Global general journal
   >[!NOTE]
   >The setup of financial tag rules is common for the General journal and Global general journal.
- Allocation journal
- Reporting currency adjustment journal
- Invoice journal (vendor)

## Setup

To use the functionality, enable the **Financial tag defaulting rules** feature in **Feature management**. The feature can be disabled at any time. If the feature is enabled but later disabled, any rules defined for financial tags are maintained in the database. However, they'll no longer be used on any transactions in Dynamics 365 Finance.

At least one [Financial tags](financial-tag.md) must be set up in the company you are creating a rule in before the **Financial tag rules** page can be used.

## Creating financial tag rules

Before you create financial tags rules, note the following:
- System rules exist to mimic the behavior already running in the system today. In a journal entry, tag header values are copied to the account tag field, and account tag values are copied to the offset account tag field by these system rules. You may enable or disable these as needed, but you can't remove them from the system or modify them in any way.
- [Power Fx](https://learn.microsoft.com/en-us/power-platform/power-fx/overview) is the language used for defining and executing the financial tag rules. You may want to spend some time getting familiar with the [formulas](https://learn.microsoft.com/en-us/power-platform/power-fx/formula-reference-overview) available. Not all formulas are supported for Dynamics 365 Finance. Additional features have been added to the language to be aware of Dynamics 365 Finance and the tables and fields allowed for use with the rule definition.
- Power Fx knowledge isn't requried to create a rule, as the feature has a rule builder that allows you to select appropriate fields to generate the proper condition for your rule to be applied. 

### Create a financial tag rule

To create a financial tag rule, follow these steps:
1. Go to **General ledger \> Chart of accounts \> Financial tags \> Financial tags**.
2. Select **New** to create a financial tag. A dialog appears with several options to select including three fields that are required.
   - **Transaction entry point** - this is the document where the data is entered.
   - **Transaction level** - this refers to the location or level where financial tags are located. For example, Header refers to the top level table that has one set of financial tags for all lines that belong to that header. Account is special for journals as the general journal has financial tags for both the account entry and for the offset account.
   - **Target** - this refers to the exact tag field you wish to set.
3. On the **PowerFx formula** tab, enter a PowerFx formula to set the value with any conditional logic desired. The return from this function is the value set on the "Target" financial tag.
   - For additional information, see [Financial tag rule reference](financial-tag-rule-reference.md) about supported fields enabled for each document or transaction entry point.  
4. On the **Conditions** build a set of conditions and outcome that populates the target financial tag.
5. Review the **Name**, the **Enabled status** and the **Overwrite existing value** options.  
6. Click **OK** to save the new rule. 

[![New Financial tag rule definition](./media/NewRule.png)](./media/NewRule.png)

## How financial tag rules apply to transactions

- At creation of a record, the rules defined for that transaction entry point and transaction level executes the first defaulting of values into the corresponding financial tag fields as defined for each target.
- For journals, when the account field or the offset account field is set all of the user defined rules for transaction level, the financial tags are populated for each target.  It's important to know which rules have been defined with the **Overwrite existing value** set to **Yes**. Any value previously set by the user or a system rule are overwritten according to that setting.
- When the final record is saved, the user rules run again to provide the final overwrite of financial tags. This is based on the overwrite that a user may have changed before saving the record or moving to a new row which causes a record save. 





