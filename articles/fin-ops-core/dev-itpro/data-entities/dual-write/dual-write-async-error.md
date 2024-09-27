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

## Centralized error handling and troubleshooting 
With all data sync processes, there's a need to manage and troubleshoot failures encountered during data sync. Dual-write async provides an easy-to-use self-service dashboard for any data synchronization failures. 
 - The synch errors tab provides details of the errors if applicable.
 - Filter by datetime, entity and data source.
 - Ability to retry or dismiss the error conditions based on the filter conditions. The retry and dismiss functionality only works when the integration job for Dual-write synch is active.
      - Retry - Allows users to retry the selected records based on the filter conditions provided.  
      - Dismiss - Allows users to remove the records from the error queue forever. After dismissed, records are no longer available for reporting or retry.  

### Limits 
There are limits for requests that can be created for retry or for dismiss.  
 - Number of requests - After a request is submitted by the user, the reconciliation takes place in background. The time for reconciliation depends on the data movement volume and complexity of the process.
However, the user can pick a different set of records for newer requests. These requests are queued and executed in order of request creation. A maximum of five requests can be queued for an integration job.
 - Number of records per request - Each request can process a maximum of 10,000 records. This avoids long reconciliations that can lead to longer lead times for processing other requests.  
