---
title: Parameters for master plan do not exist
description: Parameters for master plan do not exist
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

# Parameters for master plan do not exist

Error code: SYS25368

## Symptoms

When you are trying to firm a planned order, you see the following error message:

> Parameters for master plan %1 do not exist.

## Cause

Due to configuration issues, the system can't find the settings for the specified plan.

## Resolution

Go to **Master planning \> Setup \> Plans \> Master plans** and make sure that a plan with specified name exists.
