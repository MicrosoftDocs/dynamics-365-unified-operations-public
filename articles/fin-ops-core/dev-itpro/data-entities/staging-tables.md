---
title: Clean up staging tables
description: Learn how to clean up staging history, a feature available to users who have the Data Management Administrator role.
author: pnghub
ms.author: twheeloc
ms.reviewer: twheeloc
ms.topic: article
ms.date: 01/14/2026
ms.custom:

---

# Clean up staging tables

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics 365 Finance version 10.0.38, the **Truncate staging table** feature cleans up individual Data Management staging tables. The truncate action permanently removes all records from the staging table for the selected entity and should be used with caution. Currently, if you truncate a staging table, it affects the execution of data import and export jobs that involve the selected staging table (imports or exports through staging).

> [!IMPORTANT]
> Before you use this feature, confirm that none of the currently running jobs involve the selected staging table.

Users with the Data Management Administrator role can use this feature. Access it through the data entities in the **Data management** workspace. Select a staging table, and then select **Truncate staging table**.
