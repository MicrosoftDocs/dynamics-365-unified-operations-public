---
title: Account reconciliation agent (Production ready preview)
description: Learn about the Account reconciliation agent in Dynamics 365 Finance.
author: twheeloc
ms.author: bking
ms.topic: overview
ms.date: 04/30/2025
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerConsolidate
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9d8f55cb-b2cf-4e01-89cf-0e21f5c8ae1f
---

# Account reconciliation agent

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The Account reconciliation agent is a transformative step towards achieving a continuous financial close, offering significant benefits to our customers. By shifting from a reactive approach that relies on SSRS 
reports for reconciliation, we are introducing a proactive experience. This innovative workspace raises exceptions and employs an intelligent agent to evaluate these exceptions and provide recommended actions.
Some benefits include:
 - Enhanced efficiency - Customers can maintain a reconciled state more consistently, reducing the time and effort required for manual reconciliation.
 - Proactive management - The intelligent agent proactively identifies and suggests mitigations for exceptions, minimizing the risk of errors and ensuring financial accuracy.
 - Improved transparency - Every exception is meticulously logged, capturing the history of actions taken by users, automation, or agents, thereby enhancing transparency and accountability.
 - Regular reconciliation - The ability to reconcile on a more regular basis ensures that customers' financial records are always up-to-date, leading to better decision-making and financial planning.

## Set up Account reconciliation agent 

To set up the Account reconciliation agent, follow these steps:
1.	Go to **Feature management**, enable **(Preview) Account reconciliation agent** feature.
2.	Go to **Modules** > **Agents**. On the **Agents** page, locate the **Account reconciliation** template and enable the agent.

### View agent recommendations to mitigate exceptions
The Account reconciliation agent evaluates exceptions and provides a recommended action for the exception. The agent is best viewed from the **Account reconciliation** workspace. For example, an exception is 
raised for a transaction for a **Voucher amount mismatch**. When the agent evaluates the exception, it proposes the **Create journal entry**. 
The user can accept the recommendation or choose available other actions:
 - Reverse
 - Link transactions
 - Accept without change
 
>[!NOTE]
> If the user language is set to a language that's not EN-US, the summary isn't displayed in the **Suggested action**. A recommended action is diplayed.
The account reconciliation agent processes the following exception types:
 - Voucher amount mismatch
 - Pending accounting transferred to general ledger

### View agent activity
To view agent activity, follow these steps:
1. Click **Addressed exceptions** and view the **Activity** pane.
2. Agent activity is displayed in a timeline with the most recent activity listed at the top of the timeline. Agent activity is shown as **Fix suggested by agent**.
3. Addressed exceptions have a **Reconciled** activity on the timeline with an option to undo the action that reconciled the transaction to bring the exception back to an unmitigated state.

### Account reconciliation agent card on Account reconciliation workspace
The **Account reconciliation agent** card shown on the **Account reconciliation** workspace displays the number of agent suggestions during the selected period. 
Click the arrow on the card to view **Agent activity** for the **Account reconciliation agent**.





