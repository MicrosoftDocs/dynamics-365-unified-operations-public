---
title: Parameters for the master plan don't exist
description: When you try to firm a planned order, you receive an error message that states that no parameters exist for the master plan.
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

# Parameters for the master plan don't exist

Error code: SYS25368

## Symptoms

When you try to firm a planned order, you receive the following error message:

> Parameters for master plan %1 do not exist.

## Cause

Because of configuration issues, the system can't find the settings for the specified plan.

## Resolution

- Go to **Master planning \> Setup \> Plans \> Master plans**, and make sure that a plan that has the specified name exists.
