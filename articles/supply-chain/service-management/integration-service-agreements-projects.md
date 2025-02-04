---
title: Integration for service agreements and projects 
description: When you work with service agreements and service agreement lines, you use data that is set up in the areas in Project management and accounting.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 05/01/2018
ms.custom:
ms.reviewer: kamaybac
ms.search.form: ProjParameters
---

# Integration for service agreements and projects

[!include [banner](../includes/banner.md)]

When you work with service agreements and service agreement lines, you use data that is set up in the following areas in **Project management and accounting**.

## Project prices

The cost and the sales price for a service agreement transaction are derived from the cost price setup that applies to the project that is attached to the service agreement. Cost and sales prices can be set up by project, employee, and category.

## Project validation

The projects, employees, and categories that are available for selection on a service agreement line can be limited by the validation setup in **Project management and accounting**. By using the validation setup, you can combine employees, projects, and categories for control access.

## Project line properties

A line property is entered automatically for a service agreement line.

Line properties are created on the **Line properties** page in **Project management and accounting**. The line property that is entered on a service agreement is attached to the project that is selected for the service agreement and inherited subsequently by the service agreement line.

## Default offset accounts

If you enter an expense transaction, a default expense offset account is selected automatically for the transaction. The default expense account is set up for the project that is attached to the current service agreement.

## Project categories

The categories that are available for service agreement lines are set up on the **Project categories** page in **Project management and accounting**.

> [!NOTE]
> Categories that have the **Active in journals** check box selected on the **Project** tab on the **Project categories** page are available for selection. However, if the **Inactive categories** check box is selected on the **Journals** tab on the **Project management and accounting parameters** page, all categories are available for selection.

## Project parameters

If the **Terminated workers** field on the **Journals** tab on the **Project management and accounting parameters** page is selected, you can select inactive employees and active employees on the **Service agreements** and **Service orders** pages.

Also, you can enable the **Start time** and **End time** fields on the **Project** tab on the **Service orders** page to enter starting and ending times on service order lines.

## Enable the starting and ending time feature for service orders

1. Select **Project management and accounting** \> **Setup** \> **Project management and accounting parameters**.

2. Select the **Journals** tab, and then select the **Show start/end times** check box.

3. Select **Project management and accounting** \> **Setup** \> **Journals** \> **Journal names**.

4. Select the journal name that is attached to the service order.

5. Select the **General** tab, and then select the **Show start/end times** check box.

> [!NOTE]
> Select the journal name for the service order in the **Hour** field on the **Journals** tab of the **Service management parameters** page.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
