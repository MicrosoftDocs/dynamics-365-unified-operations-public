---
# required metadata

title: Daylight saving time support for active batch periods
description: This topic provides information about daylight saving time support for active batch periods.
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

# Daylight saving time support for active batch periods

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

With the release of Microsoft Dynamics 365 Finance version 10.0.12, it is possible to enable **Daylight Saving Time support for batch job active periods**, in [Feature management](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview). 
This feature introduces daylight saving time (DST) support to [batch job active periods](activeperiod.md) and enables users to associate their different active periods to different time zones.

> [!NOTE] 
> This feature is a one-way feature. It can't be disabled after it's been enabled.

When this feature is enabled, the following occurs:

- The **Batch jobs active periods** page will have the field, **Timezone** added next to each active period. This is the time zone that the active period would follow. Every active period initially follows the UTC time zone.

![Active Period Form](./media/active-periods-dst.png)

- The start and end times of the existing active periods will be adjusted according to the UTC time zone. The times will run at the same time as before, but the displayed start and end times might change if the user’s preferred time zone is not UTC.

- Active periods will follow the daylight savings time adjustments of the time zones they’re associated with.
