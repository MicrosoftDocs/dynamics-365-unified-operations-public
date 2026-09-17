---
title: Automated Entity store refresh
description: Learn how to enable automated Entity store refresh and troubleshoot stale or missing data in Entity store-based reports.
author: MilindaV2
ms.author: twheeloc
ms.topic: how-to
ms.date: 09/17/2026
ms.reviewer: twheeloc
ms.search.form: AutomatedEntityStoreRefresh
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 861cfa94-c6f3-4c84-89ac-22c78bf6b7a4
---

# Automated entity store refresh

[!INCLUDE [banner](../includes/banner.md)]

## Overview

The system automates and manages the entity store refresh. Administrators don't need to schedule or monitor the entity store refresh by using the system batch schedules. The refresh operation works based on anticipated latency. This functionality is enabled in Platform update 23. As an administrator, you need to opt in to use this feature.   

## Enable automated refresh

Complete the following steps to enable automated Entity store refresh.

1. Go to **System administration** > **Set up** > **Entity store**. On the **Entity store** page, a message indicates that you can switch to the **Automated Entity store refresh** option. This option is managed by the system. An admin doesn't have to schedule or monitor the Entity store refresh.

1. Select **Switch now**.

  > [!IMPORTANT]
  > This action isn't reversible. After you switch to the **Automated Entity store refresh** option, you can't revert to the old user interface (UI) experience.

1. Select **Yes** to continue.

You now see the new experience.

:::image type="content" source="./media/entity-store-data-lake-3.JPG" alt-text="Screenshot of new UI experience.":::

After the new experience is turned on, you can define the refresh for each aggregate measurement. The following refresh options are available:

- Every hour
- Twice a day
- Once a day
- Once a week

An admin can also refresh any aggregate measurement on demand by selecting the **Refresh** button. Additional options will be added in future platform updates. These options include options for real-time refresh.

> [!IMPORTANT]
> When you enable automated refresh, the system can disable the refresh of aggregate measurements. You must revisit aggregate measurements and validate that appropriate refresh intervals are applied.

## Troubleshoot stale or missing report data

An analytical workspace or Entity store-based Power BI report might show outdated data or omit data for recent dates if the required date dimension doesn't cover the reporting period or the related aggregate measurement hasn't been refreshed.

> [!NOTE]
> Entity store-based reports reflect data after the related aggregate measurement is processed. Refreshing the report itself doesn't update the data in Entity store.

### Verify the date dimension

If the report omits transactions from a recent or future year, verify that the date dimension includes those dates.

1. Go to **Organization administration** > **Setup** > **Calendars** > **Date dimensions**.
1. Select the date dimension that the report uses. Standard analytical content commonly uses the dimension named **Date**.
1. Verify that the **End date** includes the latest date that the report must show. If needed, extend the end date.
1. Close the page. The system populates the updated date dimension.

After the date dimension is updated, refresh the affected aggregate measurement.

### Verify and run the aggregate measurement refresh

1. Go to **System administration** > **Setup** > **Entity store**.
1. Select the aggregate measurement that supplies data to the report.
1. Verify that **Automatic refresh enabled** is selected and that **Recurrence** is appropriate for the required data freshness.
1. To update the measurement immediately, select **Refresh**. The system schedules the measurement for a full reset.
1. Go to **System administration** > **Inquiries** > **Batch jobs**, and search for the **Full reset** job. Verify that the job is in an executable state, such as **Ready**, **Waiting**, **Scheduled**, or **Executing**.
1. After the measurement is processed, reopen or refresh the report and verify the data.

If reports remain blank after Entity store maintenance, follow the steps in [Resolve problems after Entity store maintenance](entity-store-maintenance.md). If the full reset job is absent or fails, or if the issue continues after you complete those steps, contact Microsoft Support.

## Related information

- [Power BI integration with Entity store](power-bi-integration-entity-store.md)
- [Resolve problems after Entity store maintenance](entity-store-maintenance.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
