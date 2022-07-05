---
title: Visual and collaborative execution
description:
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

# Visual and collaborative execution

[!include [banner](../../includes/banner.md)]

The topic described how the buffer for the pillow was replenished. Now, from an execution perspective it is important to see how is the actual on-hand of the buffer.

From the item coverage form, on the on-hand tab we can see its current value. And if we had historical data we could see how the on-hand progressed over time. We can also see if it was

- critically low (less than half of the minimum for that period of time),
- low (between half of the minimum and the minimum),
- average on-hand (if it between the minimum and the minimum plus the green zone)
- Or higher than that range, as it is our case.

Note that in the on-hand form the colors represent different ranges than in the buffer.

![Graphical user interface  text  application  Teams Description automatically generated](media/image20.png)

The value of the on-hand is recorded for a specific period every time planning optimization is run.

To give you an idea of how the on-hand would look over time if we had past data, the picture will show you the item V0002 the fabrik kit, that was also a decoupling point.

![Chart  line chart Description automatically generated](media/image21.png)

And you can see as well, that the buffer values are also shown over time, with its on-hand value and its net flow.

![Chart Description automatically generated](media/image22.png)

Also, you can use DDMRP Workspace to track planning process.

![Graphical user interface  application  table  calendar Description automatically generated](media/image23.png)
