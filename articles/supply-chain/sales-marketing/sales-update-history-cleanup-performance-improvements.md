---
# required metadata

title: Sales history cleanup performance improvements
description: This topic desrcibes the Sales history cleanup performance improvements feature.
author: myvakalo
ms.date: 29/09/2021
ms.topic: article
ms.prod: D365 for Finance and Operations
ms.technology: 

---

# Sales history cleanup performance improvements

The *Sales update history cleanup* periodic batch job can take a long time if run infrequently on environments with high volume sales updates. In such situations, to reduce duration and improve reliability, the *Sales history cleanup performance improvements* feature has been introduced.  

Specifically, the feature improves the existing cleanup job in the following ways: 

- Decomposes clean-up into batches (batch size can be overridden by customizations) 
- Runs for a maximum of 2 hours (duration can be overridden by customizations) 
- Where possible, database capabilities will be leveraged to minimise locking contention and avoid joining transactional tables during cleanup. 

After enabling the feature, the *Sales and marketing > Period tasks > Cleanup > Sales update history cleanup* job **will run as it did before but with better performance** and for a maximum of 2 hours. This means it might need to be run mutiple times to clean all the data for a specific retention timeframe.   

## Turn on the sales history cleanup performance improvements feature

The feature has been introduced on 10.0.19 version. Before you can use this feature it must be turned on in your system from feature management.  
Admins can see the feature in the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace listed in the following way: 

- **Module:** *Sales and marketing*
- **Feature name:** *(Preview) Sales history cleanup performance improvements*



> [!IMPORTANT]
> Based on the release version of your environment, follow the instructions below to enable the feature properly: 
> #### On 10.0.19-10.0.20 versions:
> The SalesParmCleanupStoredProcedureBuilderFlight flight must be enabled prior feature enablement. To enable the flight, please contact Microsoft support. 
> #### On 10.0.21 or later versions:
> The feature can be enabled directly from feature management. 
