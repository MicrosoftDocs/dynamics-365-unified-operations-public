---
title: Dynamic adjustments
description: The article describes DDMRP dynamic adjustments, which flex buffer zones up or down based on market changes or future events.
author: t-benebo
ms.date: 06/30/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2022-06-30
ms.dyn365.ops.version: 10.0.28
---

# Dynamic adjustments

[!include [banner](../includes/banner.md)]

The article describes DDMRP dynamic adjustments, which flex buffer zones up or down based on market changes or future events.

In the **Buffer values** tab you see the periods for which you will have the different buffer values, remember these values are calculated by the system according to the equations that we have shown before.

But we also have the ability to manipulate the different buffer levels - by using a value of **Demand adjustment factor**. This factor will multiply the average daily usage in all calculations, so this way you modify the buffer zones.

For example, our pillow may be more demanded in August as people head to vacation. We expect sales to be higher, in which case I could change my demand adjustment factor to 1.5 as an example for all of the weeks in August.

Once we do that, you can select all of those weeks and update the calculations and see that they're adjusted based on this demand adjustment factor.

In this way we can look out over time and set buffer values and then adjust based on more than just the information that the system has, like seasonality. The calculated fields are for you to review the values and accept them. With a full DDMRP implementation, you would calculate the values every day with a batch job, and directly accept the values, run planning as well with a batch job, and review the planned orders every day for the buffers.
