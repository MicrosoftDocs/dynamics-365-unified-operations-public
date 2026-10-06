---
title: Demand planning data is moving to Dataverse storage
description: Microsoft will soon migrate all Demand planning environments from using Azure Data Explorer to Dataverse SQL for data storage. During migration, a brief period of downtime will occur to ensure that your data is migrated safely.
author: AndersEvenGirke
ms.author: aevengir
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/06/2026
ms.custom:
  - bap-template
---

# Demand planning data is moving to Dataverse storage

Microsoft will soon migrate data storage for all Demand planning environments from Azure Data Explorer to Dataverse SQL. During the migration, a brief period of downtime is required to ensure that your data is migrated safely.

## What is changing

In previous versions of Demand planning, table and time series data were stored in managed Azure Data Explorer (ADX). We are migrating table data to Dataverse Managed Data Lake and time series data to Dataverse SQL Storage.

## Why this is changing

This migration adds support for the extended querying capabilities being made available in newer versions of Demand planning and prepares the app to support additional improvements in the future. The change also aligns the app's storage technology with the Dataverse platform used across Microsoft Dynamics 365 and the Power Platform. The new solution provides a more integrated and maintainable foundation for Demand planning data.

## When and how migration occurs

Migrations of individual environments are scheduled to roll out between October 2026 and February 2027. Migration only occurs once per environment. To minimize disruption, migration is scheduled to occur outside of regular business hours, during the standard maintenance window for Power Apps.

During the final stages of the migration, your Demand planning app is locked to ensure that nothing changes during final transfer and validation. This process might take anywhere from five minutes up to one or two hours depending on the number of time series created in the last few days before the migration.

Microsoft migrates preview environments first, followed by sandbox environments, and finally production environments.

## How you are notified

During the two to three weeks before your environment is scheduled to be migrated, the Demand planning app displays a notification banner that announces the exact date when your migration will occur.

## How to prepare for migration

Review the data currently stored in the app and remove all data that you no longer need. By cleaning up your Demand planning data, you can reduce the amount of time required for the migration and, more importantly, reduce the amount of storage that the app consumes in Dataverse after migration. Remove obsolete import tables, delete entire time series that you no longer use, and remove outdated versions of the time series you do use. Demand planning's built-in data cleanup utility can help. Learn more in [Clean up time series data](clean-up-time-series-data.md).

Each Supply Chain Management premium license includes a 50 GB storage entitlement. The system provides more storage as needed at extra cost. Therefore, cleaning up your data before migration can help reduce storage costs for your organization.

## During migration

Migration runs within the defined service window and during geographic dark hours. During migration, the application doesn't allow you to update existing time series or create new ones.

## After migration

When migration finishes, the banner is removed, and the application returns to normal operation.

After migration, confirm that the Demand planning app and its relevant data are working as expected. Going forward, regularly review stored time series and remove obsolete series and outdated versions. Routine cleanup keeps the data set manageable, reduces unnecessary storage costs, and can make future maintenance activities more efficient. Demand planning's built-in data cleanup utility can help. Learn more in [Clean up time series data](clean-up-time-series-data.md).
