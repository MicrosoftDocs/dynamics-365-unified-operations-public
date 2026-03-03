---
title: Configure account structures
description: Learn about account structures and financial dimensions, including an example and outlines on segments, allowed values, and account structure activation.
author: aprilolson
ms.author: aolson
ms.topic: article
ms.date: 03/14/2024
ms.update-cycle: 1095-days
ms.custom: evergreen
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerEliminationRule
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 08fd46ef-2eb8-4942-985d-40fd757b74a8
---

# Configure account structures

[!include[banner](../includes/banner.md)]

Account structures use the main account and financial dimensions to create a set of rules that determine the order and values used when entering the account number. You can set up as many account structures as you need for your business. Assign the account structures to a company's ledger setup so you can share them.

When creating an account structure, you can use up to 11 segments. If you need more than 11 segments, thoroughly evaluate your setup and requirements, as it impacts the user experience. Consider if a segment could be derived in a reporting scenario by using a hierarchy instead of during data entry, or by using a user-defined field. For example, if you want to report on location, but you can figure location by department or cost center, you don't need location as a financial dimension. If after evaluation you determine more than 11 segments are needed, you can add extra segments by using advanced rules.

Account structures require the main account. The main account doesn't need to be the first segment in the structure, but it does identify what account structure is used during the account number entry. Because of this main account value, it can only exist in one structure assigned to the ledger so that they don't overlap. After the account structure is identified, the allowed values list is filtered to guide the user through picking only valid dimension values, decreasing the possibility of an incorrect journal entry.

> [!NOTE]
> If you plan to budget against a financial dimension, include it in an account structure. Budgeting doesn't currently utilize advanced rules.

## Example

To illustrate a best practice for setting up an account structure, assume that a company wants to track their balance sheet accounts (100000..399999) at the account and business unit financial dimension level. For revenue and expense accounts (400000..999999), they track financial dimensions Business Unit, Department, and Cost center. If they make a sale, they also like to track Customer. Using this scenario, it's recommended to have two account structures assigned to the company's ledger - one for Balance sheet accounts, and one for Profit and Loss accounts. To optimize the user experience and validation, Customer should be an advanced rule that is only used when a sales account is used.

### Balance sheet account structure

|Main account          | Business unit    |
|----------------------|-----------|
|100000..399999 | *;"&nbsp;"|

### Profit and loss account structure

|Main account          | Business unit    |Department          | Cost center    | &nbsp; |
|----------------------|------------------|--------------------|-----------|---|
|400000..999999 | *;"&nbsp;"| *;"&nbsp;"| *;"&nbsp;"| *;"&nbsp;"|

**Advanced rule for adding a Customer**

Criteria: Where Main account is between 400000 and 499999, then add customer. It can't be left blank.

|Customer         |
|-----------------|
|\* |

In this simplified example, all values and blank are allowed so * and "&nbsp;" are used.

## Segments and allowed values

The **Segments** and **Allowed values details** section provides a grid like experience for entering the rules that the system follows during validation when posting. You can type directly in the cells in the grid, import the rules from Excel, or use the **Allowed value details** section for guidance.

The **Allowed value details** section guides you through creating criteria by using **Operators** such as begins with, is between, includes, and many others.

:::image type="content" source="./media/account.png" alt-text="Screenshot of allowed values.":::

Allowed values default on to a journal or accounting distribution entry page when the account structure setup doesn't provide any other possible values to select.

Here's an example of the **Profit and loss account structure**.

|Main account          | Business unit    |Department          | Cost center    |
|----------------------|-----------|----------------------|-----------|
|400000..999999 | 002 | 022 | 014 |

When you enter a journal and select an account in the profit and loss range, if you select business unit `002`, the system defaults values `022` and `014` on the account control. This behavior also occurs with the accounting distribution page.

> [!NOTE]
> If you can't enter blank segments in a ledger account, check whether the account structure or any advanced rules restrict blank segments. If either one disallows blank segments, the ledger account fails validation.

## More than seven criteria needed

If you need more than seven criteria, add them on the next line. When you work in the **Allowed value details** section, you see that the **+Add new** criteria isn't active after the seventh criterion is entered. This restriction happens because of factors such as:

- Column width
- How the data is stored
- Performance of the **Allowed value details** control
- Usability  

> [!NOTE]
> An upgrade from Microsoft Dynamics AX 2012 isn't supported when you specify more than seven criteria. You must correct this issue before you complete the upgrade to finance and operations apps.

To add more criteria, select **Duplicate in the Segment** and **Allowed values section**. This action copies the criteria to a new line. You can then type over or modify the **Allowed value details** section.

## Best practices

When you set up your account structures, follow these best practices. However, consider your business, growth plan, and maintenance plan when you make decisions.

- Make the main account first or as close to the front of the account structure as possible, so users get the best guided experience they can during account entry.
  
  - Verify that any third-party solutions you intend to use support main account in the first position.

- Reuse account structures as much as possible to reduce maintenance across your legal entities.

- For variations across legal entities, consider using advanced rules so that account structures can be reused.

- When you define allowed values, use ranges and wildcards as much as possible. This approach allows you to grow and change without maintenance, and the system performs more ideally with this configuration.

- Don't put an asterisk for every segment in the account structure and then solely rely on the advanced rules. This approach can be difficult to manage and often leads to user error during maintenance that can make the system unable to post.

## Account structure activation

When you're satisfied with your new setup or a change to an account structure, activate it. If you assign an account structure to a ledger, the activation process can take a long time because the system syncs all unposted transactions to the new structure. Account structure changes don't impact posted transactions. As of application version 10.0.31, a new feature named **Account structure activation performance enhancement** is available in feature management. For more information about this new feature for account structure activation, see [Account structure activation performance enhancement](account-structure-improvement.md).

For more information, see [Plan your chart of accounts](plan-chart-of-accounts.md), [Financial dimensions](financial-dimensions.md), and [Enter account and dimension combinations (segmented entry control)](enter-account-dimension-combinations-segmented-entry-control.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
