---
title: Project deferrals
description: Learn about project deferrals, which let you set up deferrals for project transactions for hours, expenses, fees, and sales orders.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 08/11/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.scope: Core, Operations
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form:  
ms.dyn365.ops.version: 10.0.34
---

# Project deferrals

[!INCLUDE [banner](../includes/banner.md)]

Subscription billing enables organizations to manage revenue and expense deferrals through deferral schedules. Projects help you plan, create, manage, control, and complete customer-focused work for your organization.

On some time and material projects, you might need to defer revenue or costs and recognize them over a period. For example, for one project, the customer agrees to pay for a yearly subscription for a service, such as cloud storage or a support contract. If you create a deferral schedule, you can recognize project revenue for the service monthly. This approach helps you manage revenue for the project, because you can recognize it when you earn it.

> [!NOTE]
> Billing schedules with projects are available only in Microsoft Dynamics 365 Project Operations – Stocked/Production-based deployments.

## Enable billing schedules with projects

In the **Feature management** workspace, enable the **Billing schedules and deferrals with projects** feature in the **Subscription billing** module. After you enable it, refresh the browser window. This integration works with the **Project management and accounting** module in Dynamics 365 Finance.

## Project group setup

The system adds a project group option for **Deferred** to the **Post costs** options for the **Post costs - hour**, **Post costs - expense**, and **Post costs - item** fields. The system also adds **Deferred revenue - hour**, **Deferred revenue - expense**, **Deferred revenue - item**, and **Deferred revenue - fee** fields to the project group.

> [!NOTE]
> The deferred option for post costs and the deferred revenue options are available only for time and material projects.

## Create project transactions with deferrals

To create a deferral schedule from a time and material project, follow these steps:

If you're using billing rules:

1. On the **All projects** page, select a project.
2. Select the project contract.
3. Select **Add** to create a billing rule where the **Line type** field is set to **Time and material**.
4. Move the **ProjectID** project to the **Selected projects** list.
5. Select **Chargeable categories**, and then move the categories you want to defer to the **Selected categories** list.
6. Enter project hour, expense, fee, or sales order transactions.

    > [!NOTE]
    > The deferred option appears and is marked on the line for transactions that are correctly configured for deferrals.

7. Create and post the invoice proposal. Deferral schedules are created when you post the invoice proposal.

If you're not using billing rules:

1. On the **All projects** page, select a project.
2. Enter project hour, expense, fee, or sales order transactions. Select **Chargeable** for the line property.

    > [!NOTE]
    > The deferred option appears and is marked on the line for transactions that are correctly configured for deferrals.

3. Create and post the invoice proposal. Deferral schedules are created when you post the invoice proposal.

**All deferral schedules** displays the newly created deferral schedule. By default, the **Transaction type** field reflects the originating project transaction type for the deferral.

## View a deferral schedule from a project or a project contract

To view a deferral schedule for a project transaction, follow these steps:

1. In the project or project contract, select **Posted transactions**.
2. Select the project transaction.
3. Select **Subscription billing** and then **Deferral schedules**.
