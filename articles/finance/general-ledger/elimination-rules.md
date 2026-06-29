---
title: Elimination rules
description: Learn about elimination rules and the various options for reporting about eliminations, including examples for various transaction types.
author: jchrist
ms.author: jchrist
ms.topic: article
ms.date: 06/24/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerEliminationRule
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 08fd46ef-2eb8-4942-985d-40fd757b74a8
---

# Elimination rules

[!include [banner](../includes/banner.md)]

This article provides information about elimination rules and the various options for reporting about eliminations.

Elimination transactions are required when a parent legal entity does business with one or more subsidiary legal entities and uses consolidated financial reporting. Consolidated financial statements must include only transactions that occur between the consolidated organization and other entities outside that organizations. Therefore, transactions between legal entities that are part of the same organization must be removed, or eliminated, from the general ledger, so they don't appear on financial reports. There are multiple ways to report about eliminations:

- Create an elimination rule and process it in a consolidation or elimination company.
- Use financial reporting to show the eliminations accounts and dimensions on a specific row or column.
- Use a separate legal entity to post manual transaction entries to track eliminations.

This article focuses on elimination rules that are processed in a consolidation or elimination company. You can set up elimination rules to create elimination transactions in a legal entity that is specified as the destination legal entity for eliminations. This destination legal entity is known as the elimination legal entity. Elimination journals can be generated either during the consolidation process or by using an elimination journal proposal. Before you set up elimination rules, you should become familiar with the following terms:

- **Source legal entity** – The legal entity where you post the amounts that you're eliminating.
- **Destination legal entity** – The legal entity where you post elimination rules.
- **Elimination legal entity** – The legal entity that you specify as the destination legal entity for eliminations.
- **Consolidated legal entity** – The legal entity that you create to report financial results for a group of legal entities. You consolidate the financial data from the legal entities into this legal entity, and then create a financial report by using the combined data.

The following table shows the types of transactions that you might have to eliminate.

| Transaction type | Example |
|---|---|
| Sales order entry and invoicing (centralized processing) | You sell a product to a customer on behalf of another legal entity in your organization. |
| Sales order entry (intercompany/intracompany) and invoicing | You sell products between legal entities in your organization. |
| Purchase orders (centralized processing) | You purchase inventory, supplies, services, fixed assets, and other products from a vendor on behalf of another legal entity in your organization. |
| Inventory management (intercompany/intracompany) | <ul><li>You transfer one legal entity’s inventory to the fixed assets of another legal entity in your organization.</li><li>You transfer one legal entity’s inventory to the inventory of another legal entity in your organization.</li></ul> |
| In-transit inventory tracking | You transfer items between warehouses in the same legal entity, but across different geographical sites. |
| Accounts payable centralized invoice processing | You record an invoice on behalf of another legal entity in your organization. |
| Accounts payable centralized payment processing | You pay an invoice on behalf of another legal entity in your organization. |
| Cash management and treasury (centralized processing) | <ul><li>You process tax payments, tax refunds, interest charges, loans, advances, dividend payments, and prepaid royalties or commissions.</li><li>You pay an expense on behalf of another legal entity in your organization. The invoice is entered in the destination legal entity’s books, and you must cross-settle between legal entities. For example, one legal entity pays the expense report of an employee in another legal entity. In this case, the employee’s expense report has expenses that are related to another legal entity.</li><li>You transfer cash from one legal entity to another in your organization.</li></ul> |
| Accounts receivable (centralized processing) | You receive cash for another legal entity’s customer invoice, and you deposit the check into that legal entity’s bank account. |
| Payroll (centralized processing, intercompany/intracompany) | <ul><li>You pay another legal entity’s payroll. For example, a legal entity pays its own payroll for its employees but charges back work that an employee did for another legal entity during that pay run. Or, an employee worked half-time for legal entity A and half-time for legal entity B, and the benefits are across all pay. In these cases, the employee’s pay includes pay from both legal entities. Not only are the salaries posted, but taxes, benefits, deductions, and accruals for salaries are also posted.</li><li>You transfer labor from one department or division to another.</li></ul> |
| Fixed assets (intercompany/intracompany) | You transfer fixed assets to another legal entity’s fixed assets or inventory. |
| Allocations (intercompany/intracompany) | You process corporate allocations. Allocations are activities to any account that is allocated, regardless of the originating module. |

## Example

Your legal entity, legal entity A, sells widgets to another legal entity in your organization, legal entity B. The following example shows how transactions that occur between the two legal entities might have to be eliminated:

- Legal entity A sells a widget that costs 10.00 to legal entity B for 10.00.
- Legal entity A sells a widget that costs 10.00 to legal entity B for 10.00, plus 2.00 in actual shipping costs.
- Legal entity A sells a widget that costs 10.00 to legal entity B for 15.00 and recognizes a margin on the sale.
- Legal entity A sells a widget that costs 10.00 to legal entity B for 15.00 and recognizes half the margin on the sale. Legal entity B recognizes the other half of the margin on the sale. Therefore, the revenue is split. Split revenue provides an incentive to order from another legal entity in the organization instead of an external organization.

All these transactions create intercompany transactions that you post to due-to and due-from accounts. In addition, these transactions might include markup and markdown amounts when the amount of the intercompany sale doesn't equal the cost of the goods that were sold.

## Set up elimination rules

When setting up elimination rules, create a financial dimension specifically for elimination purposes. Most customers name it Trading Partner or something similar. If you decide not to use a financial dimension, then be sure to use main accounts that are specific for intercompany transactions only.

You find the setup for eliminations in the Setup area of the Consolidations module. After you enter a description for the rule, select the company that the elimination journal posts to. Select a company that has **Use for financial elimination process** selected in the Legal entity setup.

You can set a date on which the elimination rule becomes effective and when it's expired, if needed. You must set **Active** to **Yes** if you want it to be available in the elimination proposal process. Select a journal name that has a type of **Elimination**.

After you have defined the basics, you can define the actual processing rules by clicking **Lines**. There are two options for eliminations, eliminating the net change amount or defining a fixed amount.

Select your source account. You can use an asterisk (\*) as a wildcard. For example, 1\* selects all accounts that start with a 1 as a source of data for the allocation.

After you select your source accounts, the **Account specification** determines the account from the destination company that is used. Select **Source** if you want to use the same main account defined in the **Source** account. If you select **User defined**, then you must specify a destination account.

The dimension specification acts in the same way. If you select **Source**, it uses the same dimensions in the destination company as the source company. If you select **User defined**, you need to specify the dimensions in the destination company by clicking the **Destination dimensions** menu item.

Select source dimensions and the financial dimensions and values that are used as a source of the elimination.

## Process elimination transactions

There are two ways to process elimination transactions, during the consolidate online process or by creating an elimination journal and running the elimination proposal process. This section focuses on creating the journal and running the elimination process.

In a company defined as an elimination company, select **Elimination journal** in the Consolidations module. After you have selected the journal name, select **Lines**. You can run the proposal by selecting the **Proposals** menu and then selecting **Elimination proposal**.

Select the company that is the source of the consolidated data, and then choose the rule that you want to process. Enter a start date to begin the search for elimination amounts, and an end date to end the search date for elimination amounts. The **GL posting date** field is the date used for posting the journal to the general ledger. After you select **OK**, you can review the amounts and post the journal.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
