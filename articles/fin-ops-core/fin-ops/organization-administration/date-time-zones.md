---
# required metadata

title: Date/time data and time zones
description: This article provides information about date and time fields, and time zones.
author: pvillads
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysUserSetup, SystemDate
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: 3ce95bf2-02d7-44b5-95bc-cae6ae27e78e
ms.search.region: Global
# ms.search.industry: 
ms.author: pvillads
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Date/time data and time zones

[!include [banner](../includes/banner.md)]

This article provides information about date and time fields, and time zones.

## Date and time fields

There are three types of date and time fields that correspond to different data types in the database:

- **Combined date/time fields** – These fields are the preferred method of entering date and time data. The **utcdatetime** data type stores time and date data in a single field in Coordinated Universal Time (UTC). UTC is the primary time standard by which the world regulates clocks and time. It is, within about 1 second, mean solar time at 0° longitude; it does not observe daylight saving time. Time zones around the world are expressed using positive or negative offsets from UTC. For most purposes, UTC is considered interchangeable with Greenwich Mean Time (GMT). The current version of UTC is defined by International Telecommunications Union Recommendation (ITU-R TF.460-6).
- **Date fields** – These fields are used to enter dates only. The **date** data type stores a day, month, and year. However, these values are not stored in UTC and cannot be associated with a time zone.
- **Time fields** – These fields are used to display the number of seconds that have elapsed since midnight on the current date. The **timeofDay** data type stores an integer value. Time values are not stored in UTC.

## Time zones

To express UTC times in the local time, you must provide a time zone. The time zone controls the offset from UTC that is the equivalent of the local time. For example, the offset for Moscow is UTC+3. Your preferred time zone is first set according to the Windows locale of your computer, although it might have been changed by an administrator. Your preferred time zone is used only when displaying combined dates and times. To set the preferred time zone for a user, go to **Users** page. The page will show the list of users of the system. Select the user that you want to set the preferred time zone for, and click **User options**. On the **Language and region** tab, select the preferred time zone.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]