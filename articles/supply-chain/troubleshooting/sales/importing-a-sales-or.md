---
title: Auto charges aren't calculated when importing sales orders
description: The system doesn't calculate auto charges when you import a sales order record through DMF
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: DataManagement
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: henrikan
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---
# Auto charges aren't calculated when importing sales orders

KB Number: 4612088

## Symptoms
<!-- KFM: Spell out "DMF" -->

The system doesn't calculate auto charges when you import a sales order record through DMF.

## Resolution

The data entity supports a field called `SkipCreateAutoCharges` that controls whether or not auto charges are calculated upon import. To calculated auto charges on import, set the value of `SkipCreateAutoCharges` in the imported file to *No*.
