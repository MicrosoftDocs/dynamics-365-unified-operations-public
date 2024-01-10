---
title: Clean up staging tables
description: This article describes how to clean up staging history. 
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 1/10/2024
ms.custom:

---

# Clean up staging tables

[!include [banner](../includes/banner.md)]

In Dynamics 365 finance version 10.0.38, the **Truncate staging table** feature cleans up individual Data Management staging tables. This truncate action will permanently remove all records from the staging 
table for the selected entity and should be used with caution. Currently, executing data import/export jobs involving the selected staging table (imports or exports through staging) will be impacted if the staging 
table is truncated.  

>[!Note]
> Confirm that there are no currently executing jobs involving this staging table before using this feature. 

This feature is available to users with the Data Management Administrator role. It can be accessed via the Data Entities in the **Data management** workspace. Select a staging table, and click **Truncate 
staging table**. 
