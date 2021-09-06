---
title: Production scheduling doesn't consider the safety margins
description: Production scheduling doesn't consider the safety margins that are set on the item coverage for pegged supply
author: ChristianRytt
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.13
---

# Production scheduling doesn't consider the safety margins

## Symptoms

Master planning considers the safety margins. However, the safety margins are ignored when planned production orders are scheduled.

## Resolution

Margins are considered only during master planning, not during manual scheduling. Margins are designed to act as a buffer during the planning phase, to give some "margin" for the actual process.

To get the desired result, you can remove the margin. The route must then be updated so that it includes the desired time (for example, as queue time). Both master planning and manual scheduling should then produce the same result.
