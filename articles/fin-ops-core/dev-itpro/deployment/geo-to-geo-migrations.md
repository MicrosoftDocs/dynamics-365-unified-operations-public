---
title: Geo-to-geo migrations
description: This article describes hot to move your environment from one geography to another.
author: matapg007
ms.author: matgupta
ms.reviewer: johnmichalak
ms.service: dynamics-365-finance
ms.topic: how-to
ms.date: 10/19/2022
ms.custom:
---

# Geo-to-geo migrations

Microsoft Dynamics 365 Finance, Dynamics 365 Supply Chain Management and Dynamics 365 Commerce apps are available in multiple local geographies. Customers in these local geographies can migrate their workload from one geography to another. This guide will help customers to facilitate the overall migration process.

LCS Project migration and F&O Environment migration are two separate independent processes.

## F&O Geo to Geo migration considerations

Organizations looking to migrate environments and data from one geography to another need to consider various aspects mentioned below before actual migration.
- Geo to geo migration between various geographies
  - Data resident geographies 
    - To support data residency, Microsoft Dynamics 365 finance and operations apps are generally available in specific geographies as outlined here
    - Migration between two data resident local geographies is supported (e.g. migration from US to UAE or from EU to Norway is supported)
    - Migrating from one data resident geo to another will change -environment URL/endpoint as mentioned here (e.g. migrating from US to UAE will change URL from https://<EnvironmentName>.operations.dynamics.com/ to https://<EnvironmentName>.operations.uae.dynamics.com/)
  - Non-data resident geographies
    - Geographies other than above mentioned geos
    - Migration between two non-data resident geos is supported (e.g. migration from US to UK or US to Canada is supported)
    - Migrating between commercial non-data resident geos will not change environment URL (e.g. (e.g. Moving from US to UK will keep URL same as https://<EnvironmentName>.operations.dynamics.com/)
  - Sovereign data resident geographies 
- Migrations into or out of a sovereign cloud environment (for example, US Government Community Cloud [GCC] and China) aren't supported.Review availability of Business applications  features in target geography
  - Microsoft strives to maintain functional parity between our commercially available services across geographies. We continue to evaluate these services and capabilities for inclusion and updates in future releases. Use the below documents to get an overview of features and their availability in the geographies you are planning to use.
    - Microsoft Business Application Feature Availability - Americas
    - Microsoft Business Application Feature Availability - EMEA
    - Microsoft Business Application Feature Availability - APAC
  - If certain features are not available in target geo, associated functionality will not work in target geo after migration so plan migration activity accordingly. 
- Integration impact and updates with other services
  - 3rd party integrations
    - If the migration crosses data resident geo then F&O environment endpoint will change. Any 3rd party integrations that make use of the endpoint will require change.
  - F&O add-ins and micro-services
    - Add-ins configurations are not migrated as part of migration process. You will have to uninstall the add-ins before the migration and then reinstall them once migration completes. (e.g. dual-write needs to be reconfigured in target geo)
  - Commerce integration
    - Due to change in URL for F&O environment, you need to update POS integration after completion of production migration.
- Environment migration from one geo to another will have downtime
  - Overall migration activity will require at least 48 hrs of downtime. 
  - Overall time will vary depending on connectivity between two geos along with database and storage account size. 
  - If Dataverse environment is linked then it will need additional 24 hrs of downtime.
  - We will adhere to the terms of the Microsoft Online Services Service Level Agreement for all migrations.
  - You can't cancel the in-progress migration request. After initial migration is completed, you can create another support request to inverse the migration. 
  - If migration fails during the specified time, you will be notified in support ticket and you need to submit another request at later time.
