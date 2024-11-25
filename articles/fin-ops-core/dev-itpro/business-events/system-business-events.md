---
title: Batch business events
description: Learn about batch business events and how to use them, including a table that outlines the modules for various business events.
author: matapg007
ms.author: matgupta
ms.topic: article
ms.date: 02/25/2021
# ms.custom: NotInTOC
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-03-31
# ms.search.form:
ms.dyn365.ops.version: 10.0.17
---

# Batch business events

[!include[banner](../includes/banner.md)]

The batch platform emits the following system business events.

| Business event | Description | Module |
|----------------|-------------|--------|
| Batch job started | This event is fired when a batch job is marked as running. | Batch |
| Batch job finished | This event is fired when a batch job is completed. | Batch |
| Batch job failed | This event is fired when a batch job fails. | Batch |
| Batch job cancelled | This event is fired when a batch job is canceled. | Batch |

## Usage

### Batch job started and batch job finished

The **batch job started** and **batch job finished** events can be used to monitor and identify long-running batch jobs. They can also be used to notify stakeholders if a job takes longer than expected. By default, these events are turned off in the application.

### Batch job failed

The **batch job failed** event can be used to monitor specific batch jobs for failure, and to notify stakeholders in real time. By default, this event is turned on in the application.

## Configure batch business events

1. Go to **System administration \> Inquiries \> Batch jobs**.
2. On the **Business events** tab, update the settings to raise batch business events.

The events have the following payload.

| Field name | Field label |
|------------|-------------|
| JobId | Batch job ID |
| JobDescription | Batch job description |
| JobStatus | Batch job status |
| JobOwnerEmailId | Batch job owner email ID |
| JobExecutedByEmailId | Batch job executed by email ID |
| AdminEmailId | Admin user email ID |
| JobEndUtcDateTime | Job end UTC date time |
| BusinessEventId | Business event ID |
| ControlNumber | Business event control number |
| Event Id | Business event instance ID |
| EventTime | Business event instance ID |
| MajorVersion | Major version |
| MinorVersion | Minor version |

To get the current catalog and schema of business events, go to **System administration \> Setup \> Business events**.
