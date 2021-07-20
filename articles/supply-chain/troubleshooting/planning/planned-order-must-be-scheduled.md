---
title: Planned production order must be scheduled before it can be firmed
description: When you try to firm a planned order, you receive an error message that states that the order must be scheduled before it can be firmed.
author: ankubik
ms.date: 06/10/2021
ms.topic: troubleshooting
ms.search.form: ReqTransPo
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: ankubik
ms.search.validFrom: 2021-06-10
ms.dyn365.ops.version: 10.0.20
---

# Planned production order must be scheduled before it can be firmed

Error code: SYS309802

## Symptoms

When you try to firm a planned order, you receive the following error message:

> The planned production order must be scheduled before it can be firmed.

## Cause

The scheduled start and end dates can't be blank.

## Resolution

To specify start and end dates for the planned order, follow these steps.

1. Go to **Master planning \> Master planning \> Planned orders**.
1. Open the relevant planned order.
1. On the **General** FastTab, in the **Scheduled** section, specify dates in the **Start date** and **End date** fields.
