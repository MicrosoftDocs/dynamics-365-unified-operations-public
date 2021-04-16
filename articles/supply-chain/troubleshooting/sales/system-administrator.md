---
title: System administrators can't clear order holds because they aren't authorized
description: System administrators cannot clear order holds because they are not authorized
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: SalesTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: henrikan
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# System administrators can't clear order holds because they aren't authorized

KB Number: 4614642

## Issue description

System administrators can't clear sales order holds unless they also have the specific role assigned in the order hold code.

## Resolution

This is the expected behavior. System administrators aren't normally permitted to do certain operations when access to those operations is driven from a business policy setup, such as in this case.

There are more cases where access to perform a specific task is governed by business policies, where only specific persons within an organization are approved to perform the task. Consider approvals resulting from workflow approvals, or specific tasks resulting from a workflow configuration, for example. The same comes into play for order holds. There is no workflow associated, but the rational is similar. The relevant role designates a select group of people, who within an organization, have the agility to clear an order hold. The right to clear an order hold should not necessarily be granted to all administrators because that would violate the defined business policy.
