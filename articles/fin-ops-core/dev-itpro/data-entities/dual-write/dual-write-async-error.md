---
title: Set up and manage errors in dual-write async in Dynamics 365 finance and operations apps
description: Learn about how to set up and manage errors in dual-write async in Dynamics 365 finance and operations apps.
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.date: 09/26/2024
ms.custom:
ms.reviewer: twheeloc
---

# Set up and manage errors in dual-write async in Dynamics 365 finance and operations apps

[!include [banner](../../includes/banner.md)]

This article describes how to set up and manage errors in dual-write async in Dynamics 365 finance and operations apps.

>[Important!]
>This feature is currently in public preview and not meant to be used in production environments.

Centralized error handling and troubleshooting: As with all data sync processes there is always a need to manage and troubleshoot failures encountered during data sync. Dual-write async provides an easy-to-use 
self-service dashboard for any data synchronization failures. 
 - The synch errors tab provides details of the errors if applicable.
 - Filter by datetime, entity and data source.
 - Ability to retry or dismiss the error conditions based on the filter conditions. Note that the retry-dismiss functionality will work only when the integration job for Dual-write synch is “active”.

## Retry
This will allow users to retry the selected records based on the filter conditions provided.  

### Dismiss 
This allows users to remove the records from the error queue forever. Once dismissed the records are no longer available for reporting or retry.  

### Limits 
There are some limits that are imposed for requests an admin can create either for retry or for dismiss.  
 - Number of requests: After a request is submitted by the user the actual reconciliation takes place in background. The time for reconciliation depends on the data movement volume and complexity of the process.
However, the user is allowed to pick a different set of records for newer requests. These requests are queued in order and executed in order of request creation. There can be a maximum of 5 requests that can be
queued for an integration job.
 - Number of records per request: Each request can process a maximum of 10,000 records. This is to avoid extremely long reconciliations which eventually may lead to longer lead times for processing other requests.  
