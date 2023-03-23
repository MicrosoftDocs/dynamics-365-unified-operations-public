---
# required metadata

title: Change the accounting or reporting currency 
description: This article explains how to change the accounting or reporting currency, or add a reporting currency to the setup of a ledger.
author: kweekley
ms.date: 03/01/2023
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2023-03-05
ms.dyn365.ops.version: 10.0.14

---

# Change the accounting or reporting currency

[!include [banner](../includes/banner.md)]

This article explains how to change the accounting or reporting currency, or add a reporting currency to the setup of a ledger.

## Symptom

You want to change the accounting or reporting currency, or add a reporting currency to the ledger setup. This typically occurs in the following scenarios:

- The wrong accounting or reporting currency was specified when a legal entity was set up. You now want to change that currency.
- A reporting currency was specified when a legal entity was set up, but the organization now wants to remove the reporting currency.
- The organization is upgrading or migrating to Microsoft Dynamics 365 Finance, and wants to change the accounting or reporting currency.

An organization that didn't previously use the Dual currency capability wants to start to use it. This issue typically occurs in the following scenarios.

- No reporting currency was specified when a legal entity was set up. (A reporting currency is optional.) You now want to add a reporting currency.

## Resolution

The most important consideration is whether any transactions (actual or budget) have been posted in the legal entity for the ledger setup. **You can't change the accounting or reporting currency, or add a reporting currency, if any transactions (actual or budget) have been posted in the legal entity.** Follow the steps in one of the following sections, depending on whether transactions have been posted.

### No transactions have been posted

1. In the legal entity that you're updating currencies for, go to **General ledger \> Ledger setup \> Ledger**.
2. On the **Ledger** page, select **Edit**.
3. On the **Currency** FastTab, select the accounting currency and reporting currency to use for the legal entity.
4. Select **Save**.

If the fields for the accounting currency and the reporting currency aren't available on the **Ledger** page, one or more transactions (actual or budget) have been posted in the legal entity. Therefore, the currencies can't be changed. In this case, follow the steps in the next section.

### Transactions have been posted

**If transactions have been posted in the legal entity, the only way to change or add accounting and reporting currencies is to create a new legal entity that has the correct currencies.** To help make this process easier, Data management in the system lets you copy setup records and master records from the current legal entity to a new legal entity.

Changes to the accounting and reporting currencies are pervasive. They affect not only General ledger but also every subledger (Accounts receivable, Accounts payable, Inventory, Project, and so on), every independent software vendor (ISV) solutions, and any extension that you've made that stores amounts.

The process of finding and translating each amount to a different currency is subject to error. Therefore, the engineering team won't approve a script that changes or adds accounting and reporting currencies. Additionally, although a tool that used to be available for Microsoft Dynamics AX 2012 let you change or add accounting and reporting currencies, that tool was deprecated for both AX 2012 R3 and Finance.

Follow these steps to copy the setup and master data from the current legal entity to a new legal entity.

1. Go to **Workspaces \> Data management**.
2. Select **Templates** under the **Import/Export** group.
3. Make sure that templates are available. If no templates are available, select **Load default templates**, and wait for the templates to be generated.
4. Return to the **Data management** workspace.
5. Select **Copy into legal entity**.
6. Enter a group name and description.
7. In the **Source legal entity** field, select the legal entity to copy data from.
8. In the **Destination legal entities** FastTab, select **Create legal entities** to create a new legal entity that you can copy the source legal entity data to. Select **Select existing** to copy data to an existing legal entity.
9. Optional: Set the **Copy number sequences** field to **Yes**. (This step is recommended when you copy data.)
10. In the **Selected entities** area, select **Add template**.
11. Select the templates to use. Suggested templates for a new legal entity include **025 - General Ledger** and **Financials**. We recommend that you review all the other available templates to determine whether any of them apply to your requirements.
12. Select **Copy into legal entity** to start a batch process that will create the selected entities and copy them into the destination legal entity.
13. After the process is completed, but before any transaction are posted, go to the ledger, and update the accounting and reporting currencies as described earlier in this article.

If you created a new legal entity so that you can change the accounting or reporting currency, verify that the beginning balances are translated from the currencies of the old legal entity to the new currencies.

For a video that shows the preceding steps, see [Copy Into Legal Entity](https://community.dynamics.com/365/b/techtalks/posts/copy-into-legal-entity-october-24-2017).
