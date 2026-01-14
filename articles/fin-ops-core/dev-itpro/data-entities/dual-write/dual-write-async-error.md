---
title: Manage errors in dual-write async in finance and operations apps (preview)
description: Learn how to set up error handling and manage errors in dual-write async in Microsoft Dynamics 365 finance and operations apps.
author: pnghub
ms.author: twheeloc
ms.topic: article
ms.date: 01/14/2026
ms.reviewer: twheeloc
ms.custom:
  - sfi-image-nochange
---

# Manage errors in dual-write async in finance and operations apps (preview)

[This article is prerelease documentation and is subject to change.]

[!include [banner](../../includes/banner.md)]

This article explains how to set up error handling and manage errors in dual-write async in Microsoft Dynamics 365 finance and operations apps.

> [!IMPORTANT]
> This feature is a preview feature. Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release, so that customers can get early access and provide feedback.

## Centralized error handling and troubleshooting

For all data synchronization processes, you must be able to manage and troubleshoot any failures that occur during data synchronization. Dual-write async provides an easy-to-use self-service dashboard that provides centralized error handling and troubleshooting for data synchronization failures.

- The **Synch errors** tab provides details of the errors, as applicable.
- You can filter by date and time, entity, and data source.
- You can retry or dismiss the error conditions, based on the filter criteria. The retry and dismiss functionality works only when the integration job for dual-write synchronization is active.

    - **Retry** – You can retry selected records, based on the specified filter criteria.
    - **Dismiss** – You can permanently remove records from the error queue. After records are dismissed, they're no longer available for reporting or retries.
 
  :::image type="content" source="./media/image-error.png" alt-text="Screenshot of sync errors." lightbox="./media/image-error.png":::

## Limits

The retry and dismiss functionality has limits on the requests that you can create.

- **Number of requests** – After you submit a request, reconciliation happens in the background. The time that reconciliation takes depends on the volume of data movement and the complexity of the process. However, you can select a different set of records for newer requests. The system queues those requests and runs them in the order of request creation. You can queue up to five requests for an integration job.
- **Number of records per request** – Each request can process up to 10,000 records. This limit helps prevent long reconciliations that lead to longer lead times for processing other requests.

### Sync errors details
 - Users can look up their data by using the unique key and company reference in finance and operations or Dataverse. The unique key refers to the source side record.
 - Error codes come from internal exceptions or messages that help with troubleshooting.
 - **Created On** shows when the error record was created, not the actual record creation.  

### Known issues 

 - Updates to unmapped fields in finance and operations and Dataverse trigger the Async process. This process leads to phantom updates or unknown failures that the error table logs. The product team is working on a fix for this problem. It is available as part of quality updates. If an influx of error records is logged where data updates aren't expected, it could be due to updates from unmapped fields. Dismiss or retry the records from the **Sync errors** table.
 - The error retry and dismiss screen might take time to display if a large subset of data is retried. This behavior is expected as the process queues records for a background process. The blocking UX call provides feedback at the end of the process.


