---
title: System administrators can't clear order holds because they aren't authorized
description: System administrators can't clear order holds because they aren't authorized.
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

KB number: 4614642

## Symptoms

System administrators can't clear sales order holds unless they have the specific role that is assigned in the order hold code.

## Resolution

Access to some operations, such as clearing sales order holds, is driven by the setup of a business policy. System administrators aren't typically allowed to perform operations of this type. 

More often, access to perform a specific task is governed by business policies, and only specific persons in an organization are approved to perform that task. Examples include approvals that are the result of workflow approvals and specific tasks that are the result of a workflow configuration.

Although no workflow is associated with order holds, the principle is similar. A relevant role designates the specific group of people in an organization who have the right to clear order holds. This right should not necessarily be granted to all administrators, because that approach violates the defined business policy.
