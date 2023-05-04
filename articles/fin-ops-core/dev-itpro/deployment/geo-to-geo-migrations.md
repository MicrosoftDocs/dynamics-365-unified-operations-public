---
title: Geo-to-geo migrations
description: This article provides an overview of how to move between geographies.
author: matapg007
ms.author: matgupta
ms.reviewer: johnmichalak
ms.service: dynamics-365-finance
ms.topic: how-to
ms.date: 04/30/2023
ms.custom:
---
##  Geo to geo migration overview

To support data residency, Microsoft Dynamics 365 finance and operations apps and LCS are generally available in specific geographies. Customers can migrate their workload from one geography to another. This article provides and overview of the process and the considerations.

Moving between geographies involve two separate processes:

1. [Lifecycle Services (LCS) project migration](../lifecycle-services/project-migration-manager.md) - this feature lets you move your Lifecycle Services project data from one geography to another geography that meets your requirements.
2. [Finance and operations apps environment migration](environment-migration-process.md) - this feature lets you move your finance and operations environments that are in a single tenant from one geography (or geo) to another. No changes to the user interface or version occur as part of the move.

Start planning the migration by assessing whether you want to migrate only environments, only LCS project or both.

##  General considerations

Organizations looking to migrate environments and data from one geography to another need to consider various aspects mentioned below before actual migration.

### Feature parity

Make sure you review the [availability of features in the selected target geography](deployment-options-geo.md#feature-availability-in-local-geographies) before deciding on which geography to deploy into. If certain features are not available in target geo, associated functionality will not work in target geo after migration so plan migration activity accordingly.

### Sovereign data resident geographies

Migrations into or out of a sovereign cloud environment (for example, US Government Community Cloud [GCC] and China) aren't supported.

## LCS project migration considerations

- Migration can take up to two hours when LCS project and environments will be unavailable. 
- There are some limitations to this functionality in terms of all the data that is automatically migrated, learn more about [limitations](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/project-migration-manager#data-that-can-be-transferred-between-instances). 

## Environment migration considerations

- Overall migration activity will require at least 48 hours of downtime. Overall time will vary depending on connectivity between two geos along with database and storage account size.
- If Dataverse environment is linked then it will need additional 24 hours of downtime.
- Finance and operations apps add-ins and micro-services: Add-ins configurations are not migrated as part of migration process. You will have to uninstall the add-ins before the migration and then reinstall them once migration completes. (e.g. dual-write needs to be reconfigured in target geo)

When deploying environments from LCS the available regions listed will display if the target region is Data resident or not. 
Data resident geographies indicate both the LCS data and the environment data will be stored within the same discrete geography.
  - Migration between two data resident local geographies is supported (e.g. migration from US to UAE or from EU to Norway is supported)
  - Migrating from one data resident geo to another will change -environment URL/endpoint as mentioned here (e.g. migrating from US to UAE will change URL from <https://NAME.operations.dynamics.com/> to <https://NAME.operations.uae.dynamics.com/>) 

**Integration impact and updates with other services**
- Finance and operations apps add-ins and micro-services: Add-ins configurations are not migrated as part of migration process. You will have to uninstall the add-ins before the migration and then reinstall them once migration completes. (e.g. dual-write needs to be reconfigured in target geo)
- Commerce isn't available in all target geographies. If you have Commerce components enabled, your migration won't be scheduled if you're migrating to one of the target geographies where Commerce isn't available.

Non-data resident geographies indicate the LCS data and the environment data will be stored in different geographies.
  - Migration between two non-data resident geos is supported (e.g. migration from US to UK or US to Canada is supported)
  - Migrating between commercial non-data resident geos will not change environment URL (e.g. (e.g. Moving from US to UK will keep URL same as <https://NAME.operations.dynamics.com/>)
