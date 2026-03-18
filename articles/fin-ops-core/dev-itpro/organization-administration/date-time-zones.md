---
title: Date/time data and time zones
description: Learn about the three types of date and time fields that correspond to different data types in the database and time zones.
author: pvillads
ms.author: johnmichalak
ms.topic: article
ms.date: 03/17/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: SysUserSetup, SystemDate
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 3ce95bf2-02d7-44b5-95bc-cae6ae27e78e
---

# Date and time data and time zones

[!include [banner](../../../finance/includes/banner.md)]

This article provides information about date and time fields, and time zones.

## Date and time fields

Three types of date and time fields correspond to different data types in the database:

- **Combined date/time fields** – Use these fields to enter date and time data. The **utcdatetime** data type stores time and date data in a single field in Coordinated Universal Time (UTC). UTC is the primary time standard by which the world regulates clocks and time. It's, within about 1 second, mean solar time at 0° longitude. It doesn't observe daylight saving time. Time zones around the world are expressed using positive or negative offsets from UTC. For most purposes, UTC is considered interchangeable with Greenwich Mean Time (GMT). The current version of UTC is defined by International Telecommunications Union Recommendation (ITU-R TF.460-6).
- **Date fields** – Use these fields to enter dates only. The **date** data type stores a day, month, and year. However, these values aren't stored in UTC and can't be associated with a time zone.
- **Time fields** – Use these fields to display the number of seconds that have elapsed since midnight on the current date. The **timeofDay** data type stores an integer value. Time values aren't stored in UTC.

## Time zones

To express UTC times in the local time, you must provide a time zone. The time zone controls the offset from UTC that is the equivalent of the local time. For example, the offset for Moscow is UTC+3. The Windows locale of your computer first sets your preferred time zone, although an administrator might change it. Use your preferred time zone only when displaying combined dates and times. To set the preferred time zone for a user, go to the **Users** page. The page shows the list of users of the system. Select the user that you want to set the preferred time zone for, and select **User options**. On the **Language and region** tab, select the preferred time zone.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]