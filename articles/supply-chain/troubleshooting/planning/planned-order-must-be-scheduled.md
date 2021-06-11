---
title: The planned production order must be scheduled before it can be firmed.
description: "When you are trying to firm a planned order, you get the error: 'The planned production order must be scheduled before it can be firmed'"
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

# The planned production order must be scheduled before it can be firmed

Error code: SYS309802

## Symptoms

When you are trying to firm a planned order, the system shows the following error message:

> The planned production order must be scheduled before it can be firmed.

## Cause

The scheduled start and end dates can't be empty.

## Resolution

Specify start and end dates for the planned order by doing the following:

1. Go to **Master planning \> Master planning \> Planned orders**.
1. Open the relevant planned order.
1. Expand the **General** FastTab.
1. In the **Scheduled** field group, specify dates for the **Start date** and **End date** fields.
