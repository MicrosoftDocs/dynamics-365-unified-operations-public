---
# required metadata

title: Customer aging snapshots
description: This topic provides information about customer aging snapshots. An aging snapshot calculates aged balances for a group of customers at a point in time.
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

# Customer aging snapshots

[!include [banner](../includes/banner.md)]

This topic provides information about customer aging snapshots. An aging snapshot calculates aged balances for a group of customers at a point in time. You can create aging snapshot records either for all customers or for the customers in a customer pool.

Information from aging snapshots is shown on the **Aged balances** list page and the **Collections** page. You must create an aging snapshot before you can use the **Aged balances** list page. The list page lists only customers that an aging snapshot has been created for.

The **Customer credit and collections** workspace also shows the customer aging. For more information, see [Credit and collections management Power BI content](credit-collections-power-bi.md).

> [!NOTE]
> To help reduce the time that is required to create an aging snapshot, turn on the **Customer aging performance enhancement** feature in the **Feature management** workspace. However, don't use customer pools when this feature is turned on. If a customer pool is selected, the feature won't work, but you can still create an aging snapshot.

When you create a customer aging snapshot, use the following fields to enter information about it:

- **Aging period definition** – Select the aging period definition for the aging snapshot. You can have one aging snapshot for each aging period definition. The aging snapshot and the aging period definition must be created separately.
- **Pool ID** – This field is optional. You can use a pool to define the set of customers that should be processed in the aging snapshot. If you select a customer pool in this field, an aging snapshot is created only for the customer accounts that are part of that customer pool. The selected customer pool must be of the **Aging snapshot** type. If you leave this field blank, an aging snapshot is created for all customer accounts.

    > [!NOTE]
    > If the **Customer aging performance enhancement** feature is turned on, don't select a customer pool.

- **Criteria** – The aging snapshot will age based on the date that you select:

    - **Transaction date** – Each transaction is aged based on its transaction date.
    - **Due date** – Each transaction is aged based on its due date.
    - **Document date** – Each transaction is aged based on its document date.

- **Aging as of** – Select the date to use in the **Current date** field for the aging snapshot. Aging periods are then calculated based on that date. 

    - **Today's date** – Use the system date. Select this option if processing is set up to run in a recurring batch. Then, every time that the batch is run, the system date of that run is used.
    - **Selected date** – Use a date that you specify. If you select this option, you must enter an aging date.

    For example, the current aging period is 30 days. If you select **Today's date** in this field, the current aging period starts on today's date and then includes the previous 29 days. If you select **Selected date** and enter a date, the current aging period starts on the specified date and then includes the previous 29 days.

- **Update collection status** – Set this option to **Yes** to update the collection status of transactions on the **Collections** page from **Promise to pay** to **Promise to pay broken** if the aging date is beyond the date in the **Promise to pay date** field. Set this option to **No** to leave the collection status unchanged on the **Collections** page.
- **Include customers with zero balance** – Set this option to **Yes** to include all customers, regardless of their balance. If you include all customers, we recommend that you to turn on the **Customer aging performance enhancement** feature, and that you not use customer pools. Set this option to **No** to include only customers that have a balance. This setting helps speed up performance, because customers that don't have a balance are skipped.
- **Company range** – On the **Company range** tab, select the legal entities (companies) to include in the aging snapshot. Only legal entities that are set up for centralized payments are available for selection. Transactions from the selected legal entities are then included in the aging periods for customers that have the same party ID in all those legal entities. Currency amounts are converted to the currency of the legal entity that you're signed in to when you create the aging snapshot.

We recommend that you schedule this process to run in a batch.

> [!NOTE]
> To help improve batch performance when aging snapshots are created, enter a number in the **Maximum number of batch tasks** field on the **Collections defaults** FastTab on the **Collections** tab of the **Accounts receivable parameters** page. In the **Age customer balances** field, we recommend that you start with the default value of **100** and then adjust the value to optimize processing for your situation.

