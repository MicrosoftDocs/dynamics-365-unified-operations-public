---
# required metadata

title: Project deferrals
description: This article provides information about project deferrals, which let you set up deferrals for project transactions for hours, expenses, fees, and sales orders.
author: msftbrking
ms.date: 04/06/2023
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
ms.author: brking
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.34

---

# Project deferrals

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Subscription billing enables organizations to manage revenue and expense deferrals through deferral schedules. Projects help you plan, create, manage, control, and complete customer-focused work for your organization.

On some time and material projects, the revenue or cost might have to be deferred and recognized over a period. For example, for one project, the customer agrees to pay for a yearly subscription for a service, such as cloud storage or a support contract. A deferral schedule can be created to enable  project revenue for the service to be recognized monthly. This approach helps manage revenue for the project, because it can be recognized when it's earned.

> [!NOTE]
> Billing schedules with projects are available only in Microsoft Dynamics 365 Project Operations – Stocked/Production-based deployments.

## Enable billing schedules with projects

In the **Feature management** workspace, you must enable the **Billing schedules and deferrals with projects** feature in the **Subscription billing** module. After it's enabled, refresh the browser window. This integration works with the **Project management and accounting** module in Dynamics 365 Finance.

## Project group setup

A project group option for **Deferred** has been added to the **Post costs** options for the **Post costs - hour**, **Post costs - expense**, and **Post costs - item** fields. In addition, **Deferred revenue - hour**, **Deferred revenue - expense**, **Deferred revenue - item**, and **Deferred revenue - fee** fields are added to the project group.

> [!NOTE]
> The deferred option for post costs and the deferred revenue options are available for only time and material projects.

## Create project transactions with deferrals

To create a deferral schedule from a time and material project, follow these steps.

1. On the **All projects** page, select a project.
2. Select the project contract.
3. Select **Add** to create a billing rule where the **Line type** field is set to **Time and material**.
4. Move the **ProjectID** project to the **Selected projects** list.
5. Select **Chargeable categories**, and then move the desired categories for deferrals to the **Selected categories** list.
6. Enter project hour, expense, fee, or sales order transactions.

    > [!NOTE]
    > A deferred option will appear and will be marked on the line for transactions that are correctly configured for deferrals.

7. Create and post the invoice proposal. Deferral schedules will be created when the invoice proposal is posted.

The **All deferral schedules** page shows the newly created deferral schedule. By default, the **Transaction type** field will reflect the originating project transaction type for the deferral.

## View a deferral schedule from a project or a project contract

To view a deferral for a project transaction, follow these steps.

1. In the project or project contract, select **Posted transactions**.
2. Select the project transaction.
3. Select **Subscription billing** and then **Deferral schedules**.
