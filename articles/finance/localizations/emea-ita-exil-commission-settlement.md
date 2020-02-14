---
# required metadata

title: Commission settlement on payments
description: Commission settlement on payments.
author: ilkond
manager: AnnBe
ms.date: 01/14/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: 10.0.10

---

# Commission settlement on payments

[!include [banner](../includes/banner.md)]

In Italy many companies use to settle the commissions to their sales agents when the invoices are paid by their customers and not when the invoice is issued. The reason is to lead the agents to debt collection.
## Prerequisites
Before you can use commission settlement on payment, the following prerequisites must be met:
- The primary address of the legal entity must be in Italy.
- In the **Feature management** workspace, turn on the **Commission settlement on payments** feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Set up commission settlement by default
In the Account receivable parameters (**Account receivable**/> **Setup**/> **Account receivable parameters**, tab **Settlement**, FastTab **Other**) set up **Commission settlement** method which will be used when creating sales order by default. 
 ![Account receivable parameters](media/emea-ita-exil-commission-setup-parameters.PNG)
The field **Commission settlement** has two values:
-	**On invoice**, if the commissions are made during the invoice process
-	**On payment**, if the commissions are made during the payment process
## Set up commission calculation
A user may additional setup of commission calculation for **On payment** commission in **Sales and marketing**/> **Commissions**/> **Commission calculation**.
 ![Account receivable parameters](media/emea-ita-exil-commission-%20calculation-setup.PNG)
If the **Payment thresholds** is set to **Yes** it is possible to specify two boundaries for commissions calculation:
-	If the reached commission amount (in percentage on the reachable amount) is below the lower threshold, no commissions are accrued.
-	When the upper bound is reached the whole reachable amount is accrued.
-	Within the two boundaries, commissions normally accrue.

_Example_:

Consider the following scenario:
-	Invoice total amount 1000€ 
-	Lower limit 10% 
-	Upper 80% 

Consider the following payments:
1.	50€ (5%)  >  Since commissions are below the threshold (10%), no accrual occurs.
2.	100€ (10% of the total) > The invoice is settled at 15%, so commissions accrue with that percentage
3.	500€ (other 50% of the total amount of the invoice) > The invoice is settled at 65%, commission are also accrued at 65%
4.	200€ (20%) > Invoice is settled ad 85%, above the upper threshold so commissions become fully settled (at 100%)
5.	Any further payment doesn’t change the accrued amount because it already reached the top, but accrual transactions are still created 

Another setup can be added to the single agent who belongs to a specify group. The setup of the employee has the priority in comparison to the setup on sales commission calculation.





## Use...

### Post

When you post...

> [!NOTE]
> Warning...
