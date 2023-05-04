---
# required metadata

title: Deferral posting methods
description: This article describes the differences between the deferral posting methods for revenue and expense deferrals in Subscription billing.
author: JodiChristiansen
ms.date: 6/10/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Deferral posting methods

This article describes the differences between the deferral posting methods for revenue and expense deferrals in Subscription billing.

On the **Revenue and expense deferral parameters** page, the options for deferral posting methods are **Balance sheet** and **Profit and loss**. The example in this article will help explain the differences between the two methods and the reasons why you might use one method or the other.

The **Balance sheet** method uses only two accounts. Therefore, less setup is involved. The **Profit and loss** method has two additional accounts, **Initial recognition** and **Recognition offset**, for revenue, discounts, and costs, depending on the transaction type. These accounts are set up on the **Deferral defaults** page (**Subscription billing \> Revenue and expense deferrals \> Setup**). Although the example is focused on deferred revenue, the same concept can be applied to deferred discounts and deferred costs.

## Example

Sales invoice 1 has a total of $3,000 and has deferred revenue. The following tables show the distributions when this sales invoice is posted.

**Balance sheet method**

| Type | Account | Debit | Credit|
|---|---|---|---|
| Debit | Accounts receivable | 3,000.00 | |
| Credit | Deferred revenue | | 3,000.00 |

**Profit and loss method**

| Type | Account | Debit | Credit |
|---|---|---|---|
| Debit | Accounts receivable | 3,000.00 | |
| Debit | Revenue recognition offset | 3,000.00 | |
| Credit | Deferred revenue | | 3,000.00 |
| Credit | Initial revenue recognition | | 3,000.00 |

Sales invoice 2 has a total of $2,000 and doesn't have deferred revenue.

| Type | Account | Amount |
|---|---|---|
| Debit | Accounts receivable | 2,000.00 |
| Credit | Revenue | 2,000.00 |

**Balance sheet method totals for sales invoice 1 and 2 combined**

| Account | Debit | Credit |
|---|---|---|
| Accounts receivable | 5,000.00 | |
| Revenue | | 2,000.00 |
| Deferred revenue | | 3,000.00 |

When the **Balance sheet** method is used, it isn't as easy to see the gross revenue for a period. Some of the revenue is posted to the **Deferred revenue** account. Keep in mind that, as revenue is recognized each period, there are multiple debits and credits in the **Deferred revenue** account. Gross revenue for a given period will be mixed with the ins/outs of revenue recognition.

**Profit and loss method totals for sales invoice 1 and 2 combined**

| Account | Debit | Credit |
|---|---|---|
| Accounts receivable | 5,000.00 | |
| Revenue | | 5,000.00 |
| Revenue offset | 3,000.00 | |
| Deferred revenue | | 3,000.00 |

All revenue goes to the profit and loss **Revenue** account. Then the deferred revenue is moved from the profit and loss statement to the balance sheet. You can easily see the gross revenue, because everything is posted to the **Revenue** account. However, some of that gross revenue is deferred. Therefore, it's moved to the **Deferred revenue** account and recognized later.

In the **Profit and loss** method, you can look at the **Revenue** account and **Revenue offset** account to see gross revenue of $5,000 and net revenue (net of deferred) of $2,000. Although the **Profit and loss** method can make reporting easier, there are more accounts to set up.
