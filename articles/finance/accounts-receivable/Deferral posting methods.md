---
# required metadata

title: Deferral posting methods example
description: This topic describes the differences in the Deferral posting methods in Revenue and expense deferrals in Subscription billing. 
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

This article explains the Deferral posting options in **Revenue and expense deferral parameters** in Subscription billing. 

In **Revenue and expense deferral parameters** the **Deferral posting options** are Balance Sheet and Profit and loss. This example will help explain the differences and why you may use one method or the other. 

The Balance sheet method uses only two accounts, so less setup is involved. The Profit and loss method has two additioanl accounts for revenue, discount, and costs depending on the transaction type; Initial recognition account and Recognition offset account. These accounts are setup on the **Deferral defaults** page under Subscription billing > Revenue and expense deferrals > Setup. The example below focuses on the revenue deferrals but the same concept can be applied for the deferred discount and deferred cost. 

## Example 

Sales invoice 1 totals $3000 and has deferred revenue. These are the distributions when the sales invoice is posted. 

**Balance sheet method**
| Type | Account |  |  |
|------|---------|--------|--------|
| Debit | Accounts receivable | 3000.00 | |
| Credit | Deferred revenue | | 3000.00 |

**Profit and loss method**
| Type | Account |  |  |
|------|---------|--------|--------|
| Debit | Accounts receivable | 3000.00 | |
| Debit | Revenue recognition offset | 3000.00 | |
| Credit | Deferred revenue | | 3000.00 |
| Credit | Initial revenue recognition | | 3000.00 |

Sales invoie 2 does not have deferred revenue with a total of $2000. Since it does not use deferred revenue these are the distributions. 

| Type | Account |  |  |
|------|---------|--------|--------|
| Debit | Accounts receivable | 3000.00 | |
| Credit | Revenue | | 3000.00 |

**Balance sheet method totals for sales invoice 1 and 2 combined**:
| Account | Debit | Credit |
|---------|--------|--------|
| Accounts receivable | 5000.00 | |
| Revenue | | 2000.00 |
| Deferred revenue | | 3000.00 |

When using the Balance sheet method it is not as easy to see the gross revenue for a period because some of that revenue is in deferred revenue. Keep in mind that as revenue is recognized each period there are multiple debits and credits in deferred revenue so gross revenue for a given period gets mixed with the ins/outs of revenue recognition. 

**Profit and loss method totals for sales invoice 1 and 2 combined**:
| Account | Debit | Credit |
|---------|--------|--------|
| Accounts receivable | 5000.00 | |
| Revenue | | 5000.00 |
| Revenue offset | 3000.00 | |
| Deferred revenue | | 3000.00 |

All revenue goes to the profit and loss Revenue account, then the deferred revenue is moved off the Profit and loss statement to the balance sheet. This let you see the gross revenue easily because everything hits the revenue account. However, some of that gross revenue is deferred, so it is moved to the deferred revenue account and recognized later. With the Profit and loss method you can look at the revenue account and its offset account to see gross revenue of $5000 and net revenue (net of deferred) of $2000. The Profit and loss method can make reporting easier but there are more accounts to setup. 

