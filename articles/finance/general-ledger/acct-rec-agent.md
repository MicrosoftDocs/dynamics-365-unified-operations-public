---
title: Account Reconciliation Agent (production ready preview)
description: Learn about the Account Reconciliation Agent in Microsoft Dynamics 365 Finance.
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

# Account Reconciliation Agent (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The Account Reconciliation Agent represents a transformative step toward a continuous financial close and offers significant benefits to Microsoft's customers. With it, we shift away from a reactive approach that relies on Microsoft SQL Server Reporting Services (SSRS) reports for reconciliation. In place of that approach, we introduce a proactive experience. The innovative **Account reconciliation** workspace raises exceptions and uses an intelligent agent to evaluate those exceptions and provide recommended actions.

Here are some of the benefits:

- **Enhanced efficiency** – Customers can maintain a reconciled state more consistently. Therefore, less time and effort are required for manual reconciliation.
- **Proactive management** – The intelligent agent proactively identifies and suggests mitigations for exceptions. In this way, it helps minimize the risk of errors and ensure financial accuracy.
- **Improved transparency** – Every exception is logged to capture the history of actions that were taken by users, automation, or agents. As a result, transparency and accountability are enhanced.
- **Regular reconciliation** – The ability to reconcile on a more regular basis ensures that customer financial records are always up to date. As a result, decision-making and financial planning improve.

## Set up the Account Reconciliation Agent

To set up the Account Reconciliation Agent, follow these steps.

1. In the **Feature management** workspace, enable the **(Preview) Account reconciliation agent** feature.
1. Go to **Modules** \> **Agents**.
1. On the **Agents** page, find the **Account reconciliation** template, and enable the agent.

## View agent recommendations for mitigating exceptions

The Account Reconciliation Agent evaluates exceptions and provides a recommended action for each one. The agent is best viewed from the **Account reconciliation** workspace.

For example, an exception of the **Voucher amount mismatch** type is raised for a transaction. When the Account Reconciliation Agent evaluates the exception, it recommends the following action: **Create journal entry**. You can either accept that recommendation or select among other available actions:

- Reverse
- Link transactions
- Accept without change

> [!NOTE]
> **Suggested action** shows a summary only if the user language is set to **EN-US**. Otherwise, it shows a recommended action.

The Account Reconciliation Agent processes the following exception types:

- Voucher amount mismatch
- Pending accounting transferred to general ledger

## View agent activity in the Activity pane

To view agent activity, select **Addressed exceptions**. The **Activity** pane has a timeline that shows the following information. (The most recent activity appears at the top of the timeline.)

- Agent activity is shown as **Fix suggested by agent**.
- For each addressed exception, there is a **Reconciled** activity. The activity includes an option that you can use to undo the action that reconciled the transaction. The exception then returns to an unmitigated state.

## View agent activity from the Account reconciliation agent card in the Account reconciliation workspace

The **Account reconciliation agent** card in the **Account reconciliation** workspace shows the number of agent suggestions during the selected period. Select the arrow on the card to view agent activity for the Account Reconciliation Agent.
