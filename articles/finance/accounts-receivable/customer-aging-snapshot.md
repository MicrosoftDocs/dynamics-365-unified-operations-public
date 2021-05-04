---
# required metadata

title: Customer aging snapshot
description: This topic provides information about customer aging snapshots. The aging snapshot calculates aged balances for a group of customers at a point in time.
author: JodiChristiansen
ms.date: 05/05/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschloma
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2021-05-05
ms.dyn365.ops.version: 10.0.17

---

# Customer aging snapshot

[!include [banner](../includes/banner.md)]

This topic provides information about customer aging snapshots. The aging snapshot calculates aged balances for a group of customers at a point in time. You can create aging snapshot records for all customers, or for the customers in a customer pool. Information from aging snapshots is shown on the **Aged balances** list page, and on the **Collections** page. You must create an aging snapshot before you can use the list page. The list page only lists customers that an aging snapshot has been created for.

> [!NOTE] 
> Turn on the Customer aging performance enhancement feature using the **Feature management** workspace. This reduces the time it takes to create an aging snapshot. Don't use customer pools with this enhancement turned on. If a customer pool is selected the enhancement feature won’t run, although you can still create an aging snapshot.

Enter information as indicated in the following fields when you're creating a customer aging snapshot. 

**Aging period definition** - Select the aging period definition for this aging snapshot. You can have one aging snapshot for each aging period definition, but they must be created separately. 

- **Pool ID** - This field is optional. Use a pool to define the set of customers to be processed in the aging snapshot. Leave this field blank to create an aging snapshot for all customers. If a customer pool is selected, the aging snapshot process is applied only to the customer accounts that are part of the customer pool. The selected customer pool must be of the **Aging snapshot** type.

> [!NOTE]
> If the Customer aging performance enhancement feature is turned on, do not select a pool ID. 

- **Criteria** - The aging snapshot will age based on the date selected. 

  - Transaction date – This option will age each transaction based on its transaction date.
  - Due date – This option sill age each transaction based on its due date.
  - Document date – This option will age each transaction based on its document date.

- **Aging as of** - Select a date to use in the **Current date** field for the aging snapshot. Aging periods are calculated based on this date. If current aging period is 30 days and today’s date is used, then the Current aging period includes today’s date and the prior 29 days. If you specify a date the Current aging period starts with that date and includes the prior 29 days. 

Today’s date – Uses the system date. Use this option if processing is set up to occur in a recurring batch. If you use this date, the recurring batch can be run periodically and the system date at that time is used. 

Selected date – Use a date that you specify. If you select this option, enter an aging date. 

- **Update collection status** - Select **Yes** to update the collection status on transactions on the **Collections** page **Promise to pay** to **Promise to pay broken** if the aging data is beyond the in the **Promise to pay date** field. 

Select No to not update the collection status on the Collections form. 

- **Include customers with zero balance** - Select Yes to include all customers regardless of a balance. When including all customers, it is recommended to turn on the Customer aging performance enhancement feature and not use customer pools.

Select No to only include customers with a balance. This option will speed up performance as it will skip customers that do not have a balance.

 - **Company range** - Click the Company range tab and select the legal entities to include in the aging snapshot. Only the companies that are set up for centralized payments are available to select. Transactions from those legal entities are then included in the aging periods for customers with the same party ID in all legal entities that are selected. Currency amounts are converted to the currency of the legal entity that you are logged on to when you create the aging snapshot. 

We recommend scheduling this process to run in a batch.

> [!NOTE]
> In Accounts receivable parameters, select the **Collections** tab and expand **Collections defaults**. Enter a number in the **Maximum number of batch tasks** field to improve batch performance during the process for creating aging snapshots. We recommend starting with the default setting of 100 in the **Age customer balances** field, and then adjusting it to optimize processing in your situation.

The Customer credit and collections workspace displays the customer aging as well. For more information, see [Credit and collections management Power BI content](https://docs.microsoft.com/dynamics365/finance/accounts-receivable/credit-collections-power-bi)
