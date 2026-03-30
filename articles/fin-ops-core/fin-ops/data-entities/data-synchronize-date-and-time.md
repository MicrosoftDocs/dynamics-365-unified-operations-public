---
title: Synchronize date and time in import jobs
description: Learn about how to synchronize date and time in import jobs to Coordinated Universal Time (UTC), including a step-by-step process.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 11/20/2025
ms.reviewer: johnmichalak
audience: Application user
ms.search.region: Global
ms.search.validFrom: 2020-12-01
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Synchronize date and time in import jobs

[!include [banner](../../../finance/includes/banner.md)]

Set the time zone for your import job to Coordinated Universal Time (UTC). If you use a different setting, you might see unexpected dates and times in your imported data. Without the correct setting, the import process converts the UTC date to the local format, and then system settings convert it again.

This dual conversion causes dates to change between applications. For example, the dual conversion could cause an employee's start date to be different between Dynamics 365 Human Resources and Dynamics 365 Finance due to differences in local time zones. Setting the import job to UTC resolves this problem.

To synchronize date and time in import jobs, follow these steps:

1. In Dynamics 365 finance and operations, select **Data management**.
1. Select **Import projects**, then select the project.
1. Under **Source date format**, select **CSV-Unicode**.
1. Change **Timezone** to **Coordinated Universal Timezone**, and change **Language** to **En-US**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]