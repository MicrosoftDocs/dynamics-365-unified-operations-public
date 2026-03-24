---
title: Batch business events
description: Learn about batch business events and how to use them, including a table that outlines the modules for various business events.
author: matapg007
ms.author: snagamalla
ms.topic: how-to
ms.date: 03/05/2026
# ms.custom: NotInTOC
ms.reviewer: johnmichalak
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
| Batch job started | This event fires when a batch job is marked as running. | Batch |
| Batch job finished | This event fires when a batch job completes. | Batch |
| Batch job failed | This event fires when a batch job fails. | Batch |
| Batch job cancelled | This event fires when a batch job is canceled. | Batch |

## Usage

### Batch job started and batch job finished

Use the **batch job started** and **batch job finished** events to monitor and identify long-running batch jobs. Use these events to notify stakeholders if a job takes longer than expected. By default, the application turns off these events.

### Batch job failed

Use the **batch job failed** event to monitor specific batch jobs for failure and to notify stakeholders in real time. By default, the application turns on this event.

## Configure batch business events

1. Go to **System administration** > **Inquiries** > **Batch jobs**.
1. On the **Business events** tab, update the settings to raise batch business events.

The events include the following payload.

| Field name | Field label |
|------------|-------------|
| JobId | Batch job ID |
| JobDescription | Batch job description |
| JobStatus | Batch job status |
| JobOwnerEmailId | Batch job owner email ID |
| JobExecutedByEmailId | Batch job executed by email ID |
| AdminEmailId | Admin user email ID |
| JobEndUtcDateTime | Job end UTC date and time |
| BusinessEventId | Business event ID |
| ControlNumber | Business event control number |
| Event Id | Business event instance ID |
| EventTime | Business event instance ID |
| MajorVersion | Major version |
| MinorVersion | Minor version |

> [!NOTE]
> Activate batch job business events for all legal entities because you can configure batch job tasks to run in different legal entities.

To get the current catalog and schema of business events, go to **System administration** > **Setup** > **Business events**.
