---
# required metadata

title: Sales update history cleanup job failure or performance issues
description: The Sales history cleanup job would fail or take very long if there is large amount of sales update data. In this case, the users should enable the Sales history cleanup performance improvement feature.
author: myvakalo
ms.date: 29/09/2021
ms.topic: troubleshooting
ms.prod: D365 for Finance and Operations
ms.technology: 

---

# Sales update history cleanup job failure or performance issues 

## Symptoms 

The *Sales update history cleanup* periodic cleanup job fails or has performance issues.  

 

## Cause 

This is due to high volume sales updates which creates large amount of sales update data. The cleanup job attempts to clean all this data in one transaction. As a result, the job might not perform well or fail. 

 

## Resolution 

The performance issue of the earlier *Sales update history cleanup* job has been improved and a new version is available from application version 10.0.19 onwards. It is the [*Sales history cleanup performance improvements*](../../sales-marketing/sales-update-history-cleanup-performance-improvements.md) feature and can be found under Feature management. 

Below are the exact steps needed to be taken for the feature to be properly enabled, depending on your environment version. 

### On 10.0.18 or earlier versions: 

The feature is not available. It is recommended to upgrade on a later application version.  

### On 10.0.19-10.0.20 versions: 

The *SalesParmCleanupStoredProcedureBuilderFlight* flight has to be enabled before the *Sales history cleanup performance improvements* feature is enabled from Feature management. For enabling the flight, please contact Microsoft support. 

### On 10.0.21 or later versions: 

The feature “Sales history cleanup performance improvements” can be enabled directly from feature management. 

 

After enabling the feature, the *Sales and marketing > Period tasks > Cleanup > Sales update history cleanup* job will run as it did before but with better performance and for a maximum of 2 hours. This means it might need to be run mutiple times to clean all the data for a specific retention timeframe.   
