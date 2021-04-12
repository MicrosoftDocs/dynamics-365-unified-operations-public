---
title: Planned orders are getting generated for phantom item after running master planning
description: Planned orders are getting generated for phantom item after running master planning
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ReqTransPo
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: anderso
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Planned orders are getting generated for phantom item after running master planning

KB Number: 4614729

## Issue description

Planned orders are getting generated for phantom item after running master planning

## Resolution

The "Phantom" check mark on the released product is used to determine what the default line type on the BOM should be. There will still be created planned orders for the item, however they will have the "Directly derived" flag set to true. This means that the planned production order cannot be firmed on its own, it will always be included automatically when the parent production is firmed, and the BOM lines of the planned "phantom" order will be included in the BOM of the parent production.  
