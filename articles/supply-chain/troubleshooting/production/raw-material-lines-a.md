---
title: Raw material lines are allowed for unpicking and deletion even after FG creation
description: Raw material lines are allowed for unpicking and deletion even after FG creation
author: johanhoffmann
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ProdTableListPage
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---
<!-- KFM: Please spell out "FG", but also keep the title under 80 chars. -->
# Raw material lines are allowed for unpicking and deletion even after FG creation

KB Number: 4614721

## Issue description

Raw material lines are allowed for unpicking and deletion even after FG creation

## Resolution

This is the expected behavior. Adjustments to raw material consumption can be done up until the production order reaches a status of *Ended*.
