---
title: Batch processing of alerts
description: Learn about batch processing of alerts, including overviews on setting up and processing for change-based events and due-date events.
author: sericks007
ms.author: sericks
ms.topic: article
ms.date: 08/24/2021
ms.custom:
ms.reviewer: johnmichalak
audience: Application user
ms.search.region: Global
ms.search.validFrom: 2018-3-30
ms.search.form:
ms.dyn365.ops.version: Platform update 15
---

# Batch processing of alerts

[!include [banner](../includes/banner.md)]

Alerts are processed by the batch processing functionality. You must set up batch processing before the process and deliver alerts.

Batch processing functionality supports two types of events:

- Events triggered by change-based events. These events are also referred to as create/delete and update events.
- Events triggered by due dates.

You can set up batch processes for each type of event.

## Batch processing for change-based events

The system reads all change-based events that have occurred since batch processing was last run. Change-based events include updates to fields, the deletion of records, and the creation of records. These events are compared with the conditions that you set up in alert rules. When an event matches the conditions in a rule, the batch process generates an alert.

### Frequency for change-based events

For change-based events, you can set up a batch job that triggers the processing of an event soon after the system logs the event. If you set up the batch job to recur more often, users receive their alerts sooner after changes occur. However, a high frequency for batch processing might adversely affect system performance.

On the other hand, a batch job that recurs less often, and that you schedule for times when the system load is low, might help improve system performance. However, a low frequency for batch processing might not meet the users' demands for timely alerts.

Therefore, when you set up the frequency of batch processing for change-based events, consider the balance between the timeliness of alerts and the performance of the whole system. These considerations become more relevant as the number of users who create alert rules increases. The frequency doesn't affect the number of events that the system processes. However, if more users create rules, the process runs more checks. This type of data exchange might affect system performance.

#### The risks of low batch frequency

If you set up a low frequency for batch processing for change-based events, data that is relevant to the conditions in alert rules might change before processing. Therefore, you might lose alerts.

For example, you create an alert to trigger when the event is **customer contact changes** and the condition is **customer = BB**. In other words, when the customer contact for customer BB changes, the process logs the event. However, the batch processing system is set up so that batch processing occurs less often than data entry. If the customer name changes from **BB** to **AA** before the event is processed, the data in the database no longer matches the condition in the rule, **customer = BB**. Therefore, when the event is finally processed, no alert is generated.

### Set up processing for change-based alerts

1. Go to **System administration** &gt; **Periodic tasks** &gt; **Alerts** &gt; **Change based alerts**.
2. In the **Change based alerts** dialog box, enter the appropriate information.

## Batch processing for due-date events

The system detects all events that are caused by due dates, and these events are compared with the conditions that are set up in alert rules. The batch process generates an alert when an event matches the conditions in a rule.

### Frequency for due-date events

For due-date events, you might want to set up batch jobs that are run during the night or at specific times of the day, to balance the system load. We recommend that you set up the batch job so that it's run at least one time per day. If alerts should be sent as early as possible, set up the batch processing to occur immediately after the system date changes. If you want to generate alerts for due-date events that occur after a batch job has already processed alerts, you can run the batch job again on the same day.

For example, a batch job has been run on a particular day. You then create a purchase order that has a due date that should trigger an alert on that same day. To receive the alert on that day, you must run the batch job again after the purchase order is created. However, if you don't run the batch job again on that day, the next day's batch job detects any due-date events that weren't processed on previous days.

> [!NOTE]
> Even when the batch process is run more than one time per day, alerts aren't duplicated for the same due-date event and conditions. Alerts are generated only for dates that have become due because of changes that occurred in the system after the last batch job was run.

### Batch processing window

The processing of alert rules in a company can be stopped for several reasons. These reasons include vacations, system errors, or other issues that prevent the batch jobs from being run for some time.

To prevent due-date alerts from becoming obsolete because the batch job hasn't been run for several days, you can set up a batch processing window. A batch processing window can be used to prevent a batch job from being run for a specified number of days.

If you set up a batch processing window, an alert is sent when the alert rule is processed, even if the alert exceeds the time limit that is defined in the due-date criteria. An alert continues to be sent for as long as the period that is defined by this time limit plus the batch processing window isn't exceeded. However, when the period exceeds the value defined by the time limit plus the batch processing window, an alert is no longer sent.

### Set up processing for due-date alerts

1. Go to **System administration** &gt; **Periodic tasks** &gt; **Alerts** &gt; **Due date alerts**.
2. In the **Due date alerts** dialog box, enter the appropriate information.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
