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

# Geo migrations overview

Microsoft Dynamics 365 finance and operations apps are available in multiple local geographies. Customers in these local geographies can migrate their workload from one geography to another. This article provides and overview of the process and the considerations.

Moving between geographies involve two separate processes:

1. [Lifecycle Services (LCS) project migration](../lifecycle-services/project-migration-manager.md)
2. [Finance and operations apps environment migration](environment-migration-process.md)

## Considerations

Organizations looking to migrate environments and data from one geography to another need to consider various aspects mentioned below before actual migration.

### Geo to geo migration between various geographies

To support data residency, Microsoft Dynamics 365 finance and operations apps and LCS are generally available in specific geographies. When deploying environments from LCS the available regions listed will display if the target region is Data resident or not.

- Data resident geographies indicate both the LCS data and the environment data will be stored within the same discrete geography.
  - Migration between two data resident local geographies is supported (e.g. migration from US to UAE or from EU to Norway is supported)
  - Migrating from one data resident geo to another will change -environment URL/endpoint as mentioned here (e.g. migrating from US to UAE will change URL from <https://NAME.operations.dynamics.com/> to <https://NAME.operations.uae.dynamics.com/>)
- Non-data resident geographies indicate the LCS data and the environment data will be stored in different geographies.
  - Migration between two non-data resident geos is supported (e.g. migration from US to UK or US to Canada is supported)
  - Migrating between commercial non-data resident geos will not change environment URL (e.g. (e.g. Moving from US to UK will keep URL same as <https://NAME.operations.dynamics.com/>)

Make sure you [review the availability of features in the selected target geography](deployment-options-geo.md) before deciding on which geography to deploy into.

### Sovereign data resident geographies

- Migrations into or out of a sovereign cloud environment (for example, US Government Community Cloud [GCC] and China) aren't supported.Review availability of Business applications  features in target geography
- If certain features are not available in target geo, associated functionality will not work in target geo after migration so plan migration activity accordingly.

### Integration impact and updates with other services

- 3rd party integrations: If the migration crosses data resident geo then F&O environment endpoint will change. Any 3rd party integrations that make use of the endpoint will require change.
- F&O add-ins and micro-services: Add-ins configurations are not migrated as part of migration process. You will have to uninstall the add-ins before the migration and then reinstall them once migration completes. (e.g. dual-write needs to be reconfigured in target geo)
- Commerce integration: Due to change in URL for F&O environment, you need to update POS integration after completion of production migration.

### Environment migration from one geo to another will have downtime

- Overall migration activity will require at least 48 hrs of downtime.
- Overall time will vary depending on connectivity between two geos along with database and storage account size.
- If Dataverse environment is linked then it will need additional 24 hrs of downtime.
- We will adhere to the terms of the Microsoft Online Services Service Level Agreement for all migrations.
- You can't cancel the in-progress migration request. After initial migration is completed, you can create another support request to inverse the migration.
- If migration fails during the specified time, you will be notified in support ticket and you need to submit another request at later time.
