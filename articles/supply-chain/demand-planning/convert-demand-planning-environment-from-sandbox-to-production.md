---
title: Convert a Demand planning environment from sandbox to production
description: Learn the steps, considerations, and best practices for converting a Demand planning environment from sandbox to production.
author: AndersEvenGirke
ms.author: aevengir
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 03/18/2025
ms.custom: 
- bap-template 
---

# Convert a Demand planning environment from sandbox to production

You can convert a Demand planning environment from sandbox to production. You might want to do this conversion if, for example, you use a sandbox environment to set up models and check integrations before you use them with production data.

## Conversion process

The process for converting a Demand planning environment from sandbox to production is the same as the process for converting an environment for any other Microsoft Power Platform–based application. Follow the instructions in [Change environment type](/power-platform/admin/switch-environment).

## Special considerations

Although the process for environment conversion is the same for every Microsoft Power Platform–based application, conversion of a Demand planning environment involves some special considerations, as described in the following subsections.

### Remove sandbox connections

After you convert a Demand planning environment from sandbox to production, the environment can no longer connect to its sandbox sources of data. (Those sources include the previous instance of Dynamics 365 Supply Chain Management and Power Query tables.) This behavior makes sense from a security standpoint, because it prevents accidental leakage of production data. However, one result is that some of your configurations, such as import or export profiles, no longer work as you expect. Therefore, you should delete all existing import and export profiles before you convert the environment to production. Then re-create them after the conversion is completed. Configure the new profiles so that they point to production sources of data.

To delete import and export profiles, follow these steps:

1. Go to **Data management** \> **Import** or **Data management** \> **Export**.
1. Select the profile to delete.
1. Select **Delete**.

Learn more about how to create new profiles in the following articles:

- **Import profiles:** [Import data into Demand planning](/dynamics365/supply-chain/demand-planning/import-data)
- **Export profiles:** [Export and download data](/dynamics365/supply-chain/demand-planning/export-data)

### Consider removing test data

After you convert a Demand planning environment from sandbox to production, you will probably start to use production data. To avoid mixing test data and production data, consider going through tables and time series, and deleting any that contain test data.

To delete tables and time series, follow these steps:

1. Go to **Data management** \> **Tables and data** or **Planning data** \> **All**.
1. Select the table or time series to delete.
1. Select **Delete**.

> [!NOTE]
> The system might block you from deleting some tables or time series (for example, if a time series is used as an input in a forecast or calculation profile). In this case, read the error messages that you receive to learn how to address the issue. For example, you might first have to delete dependent records.

### Review user access roles

After you convert a Demand planning environment from sandbox to production, the environment uses production data and generates production forecasts. Therefore, you should review who can access Demand planning, and what kind of data they can view or edit. Learn more in the following articles:

- **Security roles and row-level security:** [Security roles and row-level security in Demand planning](/dynamics365/supply-chain/demand-planning/users-access)
- **Time fence functionality:** [Limit manual time series edits with time fences](/dynamics365/supply-chain/demand-planning/time-fences)
