---
title: Convert a Demand planning environment from sandbox to production
description: Learn how to convert your Demand planning environment from sandbox to production, including steps, considerations, and best practices.
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

It's possible to convert a Demand planning environment from sandbox to production. You might want to do this, for example, when using a sandbox to set up models and checking integrations before deciding to use them with production data.

## Conversion process

The process for converting a Demand planning sandbox environment to production is the same as for any other Power Platform-based application environment. To do so, follow the instructions provided in [Change environment type](/power-platform/admin/switch-environment).

## Special considerations

While the process for environment conversion is the same for every Power Platform-based application, there are several things to consider when doing so for Demand planning, as described in the following subsections.

### Remove sandbox connections

When you change an environment from sandbox to production, your changed environment won't be able to connect to its sandbox sources of data anymore (including the previous Dynamics 365 Supply Chain Management instance or Power Query tables). This makes sense from a security standpoint because it prevents accidental leakage of production data, but it means that some of your configurations, such as import or export profiles, will stop working as expected. Therefore, you should delete all existing import and export profiles before you convert your environment to production and recreate them once the conversion is complete, this time pointing to production sources of data.

To delete import and export profiles, follow these steps:

1. Go to **Data management** \> **Import** or **Data management** \> **Export**.
2. Select the profile you wish to delete.
3. Select **Delete**.

For more information on creating new profiles, see the following articles:

- Import profiles: [Import data into Demand planning](/dynamics365/supply-chain/demand-planning/import-data)
- Export profiles: [Export and download data](/dynamics365/supply-chain/demand-planning/export-data)

### Consider removing test data

When you convert a Demand planning environment to production, you'll probably also start using production data. To avoid mixing test and production data, consider going through tables and time series and deleting those that contain test data.

To delete tables and time series, follow these steps:

1. Go to **Data management** \> **Tables and data** or **Planning data** \> **All**.
2. Select the table/time series you wish to delete.
3. Select **Delete**.

> [!NOTE]
> The system might sometimes block you from deleting certain tables or time series (for example, if a time series is used as an input in a forecast or calculation profile). Read the error messages that the system shows to find out how to solve the issue (for example, by deleting dependant records first).

### Review user access roles

Because your Demand planning environment now uses production data and generates production forecasts, you should review who can access Demand planning and what kind of data they can view or edit. Refer to the following articles for details:

- Security roles and row-level security: [Security roles and row-level security in Demand planning](/dynamics365/supply-chain/demand-planning/users-access)
- Time fence functionality: [Limit time series edits with time fences](/dynamics365/supply-chain/demand-planning/time-fences)