---
# required metadata

title: Configure account structures
description: This topic provides information about account structures and financial dimensions.
author: aprilolson
manager: AnnBe
ms.date: 04/10/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerEliminationRule
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 13131
ms.assetid: 08fd46ef-2eb8-4942-985d-40fd757b74a8
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure account structures

[!include[banner](../includes/banner.md)]

Account structures use the main account and financial dimensions to create a set of rules that determine the order and values used when entering the account number. You can set up as many account structures as you need for your business. The account structures are assigned to a company’s ledger setup, so they can be shared.

When creating an account structure, the maximum number of segments is 11. If you need more segments than this, thoroughly evaluate your setup and need for this many as it will impact the user experience. Consider if a segment could be derived in a reporting scenario using a hierarchy instead of during data entry, or by using a user defined field. For example, if you want to report on location, but you can figure location by department or cost center, you would not need location as a financial dimension. If after evaluation you do determine more than 11 segments are needed, you can add additional ones using advanced rules.

Account structures require the main account. The main account does not need to be the first segment in the structure, but it does identify what account structure is being used during the account number entry. Because of this, a main account value can only exist in one structure assigned to the ledger so that they do not overlap. Once the account structure is identified, the allowed values list is filtered to guide the user through picking only valid dimension values, decreasing the possibility of an incorrect journal entry.

> [!NOTE] 
> If you plan to budget against a financial dimension, it will need to be part of an account structure. Budgeting does not currently utilize advanced rules.

## Example
To illustrate a best practice for setting up an account structure, let's assume that a company wants to track their balance sheet accounts (100000..399999) at the account and Business unit financial dimension level. For revenue and expense accounts (400000..999999), they track financial dimensions Business Unit, Department, and Cost center. If they make a sale, they also like to track Customer. Using this scenario, it would be recommended to have two account structures assigned to the company’s ledger. One for Balance sheet accounts, and one for Profit and Loss accounts. To optimize the user experience and validation, Customer should be an advanced rule that is only used when a sales account is used.

**Balance sheet account structure**

|Main account          | Business Unit    |
|----------------------|-----------|
|100000..399999 | *;” “|

**Profit and loss account structure**

|Main account          | Business Unit    |Department          | Cost center    |
|----------------------|-----------|----------------------|-----------|
|400000..999999 | *;” “|*;” “|*;” “|*;” “|

**Advanced rule for adding a Customer**
Criteria: Where Main account is between 400000 and 499999, then add customer. It cannot be left blank.

|Customer         |
|-----------------|
|* |

In this simplified example, all values and blank are allowed so * and “ “ are used.

## Segments and allowed values
The **Segments** and **Allowed values details** section provides a grid like experience for entering the rules that will be followed on validation during posting. You can type directly in the cells of the grid, import it from Excel, or use the **Allowed value details** section to guide you through it.

The **Allowed value details** section guides you through creating criteria using **Operators** such as begins with, is between and includes and many others.

[![Allow values](./media/account.png)](./media/account.png) 

## More than 7 criteria needed

If you have more than 7 criteria that are needed, you can continue adding them on the next line. You will notice when working in the **Allowed value details** section that the **+Add new** criteria is not longer active after the 7th criteria is entered. This is due to many factors such as: 
 - column width 
 - how the data is stored 
 - performance of the **Allowed value details** control
 - usability  
 
To continue to add additional criteria, click on **Duplicate in the Segment** and **Allowed values section**. This will copy the criteria to a new line. You can then type over or modify the **Allowed value details** section.

(LINK TO VIDEO THAT WILL BE CREATED)

## Best practices
When setting up your account structures there are some best practices you can follow. However, this is just guidance and a holistic discussion about your business, growth plan and maintenance plan should be considered as part of that discussion.

•	Make main account first or as close to the front of the account structure as possible, so users get the best guided experience they can during account entry.

•	Reuse account structures as much as possible to reduce maintenance across your legal entities.

•	For variations across legal entities, consider using advanced rules so that account structures can be reused.

•	When defining allowed values, use ranges and wildcards as much as possible. This not only allows you to grow and change without maintenance, but the system also performs more ideally with this configuration.

•	Do not just put an asterisk for every segment in the account structure and then solely rely on the advanced rules. This can be hard to manage and often leads to user error during maintenance that can make the system unable to post.

## Account structure activation
When you are happy with your setup or change to an account structure, you must activate it. If an account structure is assigned to a ledger, this activation can be a long running process, as all unposted transactions in the system must be synced to the new structure. Posted transactions are not impacted with account structure changes.


For more information, see [Plan your chart of accounts](plan-chart-of-accounts.md), [Financial dimensions](financial-dimensions.md) and [Enter account and dimension combinations (segmented entry control](enter-account-dimension-combinations-segmented-entry-control.md).







