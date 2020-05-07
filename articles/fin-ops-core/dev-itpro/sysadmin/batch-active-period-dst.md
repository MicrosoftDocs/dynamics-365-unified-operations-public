---
# required metadata

title: Daylight Saving Time support for batch job active periods
description: This topic provides information about a feature to introduce daylight saving time support for batch job active periods.
author: karimelazzouni
manager: AnnBe
ms.date: 05/07/2020
ms.topic: article
ms.prod:
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

audience: IT Pro 
ms.reviewer: kfend
ms.search.scope: Core, Operations
ms.custom: NotInToc
ms.assetid: a6685c6f-74bf-4f09-a19d-76130d7ce2da
ms.search.region: Global
ms.author: kaelazzo
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: Platform update 36
---

# Daylight Saving Time support for batch job active periods

[!include [banner](../includes/banner.md)]

With the release of Platform update 36, it is possible to enable **Daylight Saving Time support for batch job active periods**, in [Feature management](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview). 
As the name suggests, this feature will introduce DST support to [batch job active periods](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/sysadmin/activeperiod). It will also enable the user to associate their different active periods to different time zones.

> [!NOTE] 
> This feature is a one-way feature. It cannot be disabled once it's enabled.

## What happens once you enable the feature

1. The Batch jobs active periods form will have one additional field next to each active period: Timezone. This is the time zone that the active period would follow from now on. Every active period would initially follow the UTC time zone.
![Active Period Form](./media/active-periods-dst.png)
1. Start and end times of the existing active periods will be adjusted to the UTC time zone. Effectively, they will run at the same time as before, but their displayed start and end times might change if the user’s preferred time zone is not UTC.
1. Active periods will follow the daylight savings time adjustments of the time zones they’re associated with.
