---
# required metadata

title: Manage expense delegation
description: An expense delegate user can create and manage expense reports on behalf of another employee in the organization.
author: KimANelson
manager: AnnBe
ms.date: 01/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  TrvParameters
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: knelson 
ms.search.validFrom: 2020-01-10
ms.dyn365.ops.version: 10.0.9
---

# Manage expense delegation

[!include [banner](../includes/banner.md)]

An expense delegate user can create and manage expense reports on behalf of another employee in the organization.

## Configuring expense delegation

To set up a user as an expense delegate, go to **Expense management > Setup > General > Delegates** to open the **Delegates** page. Select **New** and then select the employee that will have a delegate defined. Enter the alias of the delegate user and the start and end date for the delegation period.

## Managing expense delegation on behalf of another employee

If the feature management key **Enable expense delegates list page** is enabled, the **Expenses delegated to me** list page will be available by navigating to **Expense management > My expenses > Expenses delegated to me**.

A delegate user can quickly filter and search on existing expense reports that hae been delegated to the user. The user can also quickly create a new expense report on behalf of other users by clicking **New expense report**.

Delegate users can also create and manage expense reports on behalf of other employees by navigating to **Expense management > My expenses > Expense reports** and clicking the **Open other user's expenses** button.
