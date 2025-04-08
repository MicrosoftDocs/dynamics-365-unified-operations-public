---
title: Synchronize date and time in import jobs
description: Learn about how to synchronize date and time in import jobs to Coordinated Universal Time (UTC), including a step-by-step process.
author: sericks007
ms.author: sericks
ms.topic: article
ms.date: 12/01/2020
ms.reviewer: johnmichalak
audience: Application user
ms.search.region: Global
ms.search.validFrom: 2020-12-01
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Synchronize date and time in import jobs

[!include [banner](../../../finance/includes/banner.md)]

It's important to set the time zone for your import job to Coordinated Universal Time (UTC). You might see unexpected dates and times in your imported data if you use a different setting. Without the correct setting, the import process converts the UTC date to the local format, and then system settings converts it again.

This dual conversion causes dates to change between applications. For example, the dual conversion could cause an employee's start date to be different between Dynamics 365 Human Resources and Dynamics 365 Finance due to differences in local time zones. Setting the import job to UTC resolves this problem.

1. In Dynamics 365 finance and operations, select **Data management**.

2. Select **Import projects**, and then select the project.

3. Under **Source date format**, select **CSV-Unicode**.

   <!-- [![Change source date format to UTC.](../../dev-itpro/data-entities/media/data-source-date-format.png)](/media/data-source-date-format.png) -->

4. Change **Timezone** to **Coordinated Universal Timezone**, and change **Language** to **En-US**.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

