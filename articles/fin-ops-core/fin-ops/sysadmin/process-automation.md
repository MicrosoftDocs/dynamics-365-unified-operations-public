---
title: Process automation
description: Learn about how process automation allows simple scheduling of processes that will be run by the batch server.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 03/10/2026
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-06-30
ms.search.form: ProcessScheduleSeries
ms.dyn365.ops.version: AX 10.0.11
---

# Process automation

[!include[banner](../../../finance/includes/banner.md)]

Process automation makes it easy to schedule processes that the batch server runs. The updated calendar view of the scheduled work lets end users view and take action on scheduled and completed work.

## Administration

You can find the central administration page for all process automations in the System Administration module under the **Setup** menu. This page lists all automated processes (series) that are set up in the system. You can also add new process automations directly from this page. After you set up a series, you can manage each series from this list. You can choose to edit the entire series, delete it, view all occurrences in a list view, or disable the series if you want to pause the scheduled work.

Use the **Background processes** tab on this page to administer any background processes that are running in your environment. Select **Edit** to make schedule changes for any background process. These changes can include a sleep time period that causes the process to pause running for a specified period each day. Select **View most recent results** to view the execution results for each background process.

When you disable a process in feature management, it doesn't show in the list. Also, the process automation scheduling engine doesn't schedule any occurrences or background processes for a disabled feature. When you re-enable the feature, the process automation scheduling engine runs any scheduled occurrences or background processes that are in the past immediately. The process automation scheduling engine relies on the system batch job, **Process automation polling system job**, to run. Don't alter or tamper with this job. If this batch job isn't running, or it's in an error state, select **Initialize process automation** to reset the batch job. This reset ensures that the system initializes any new automations introduced in a more recent version of the application.

## Calendar view

One of the key benefits of process automation is the ability to see the scheduled work in a simple calendar view.  This view allows you to see work for a week at a time. You see this view on the right side of the **Process automation** page. It populates with the scheduled work for the selected series.

:::image type="content" source="../../dev-itpro/sysadmin/media/CalendarView2.png" alt-text="Screenshot of the process automation calendar view.":::

## Occurrence changes

You can modify each occurrence without impacting other occurrences defined by the series that originated them. You can edit occurrences of scheduled work from the calendar view by selecting the **View/Edit** button and selecting **Occurrence**. This page provides access to all the settings originally shown in the series setup wizard and provides the ability to make a one-off change for the selected occurrence. You can also turn off an occurrence of scheduled work by selecting the **Disable** button from the calendar view.

## Developer documentation

By using the process automation framework, developers can extend the process automation framework. The [Process automation framework](../../dev-itpro/process-automation/process-automation-framework.md) documentation provides information about how you can create custom processes that you require to be run by the batch server scheduled by using the process automation wizard and appear in the calendar view automatically.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
