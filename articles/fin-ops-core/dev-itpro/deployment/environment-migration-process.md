---
title: Finance and operations apps environment migration
description: This article describes how to move your environment from one geography to another.
author: matapg007
ms.author: matgupta
ms.reviewer: johnmichalak
ms.service: dynamics-365-finance
ms.topic: how-to
ms.date: 05/05/2023
ms.custom:
---

# Finance and operations apps environment migration

[!INCLUDE[banner](../includes/preview-banner.md)]

> [!NOTE]
> Contact support for more information if you need to move endpoints before this feature is generally available. 

Microsoft continues to open data centers for business service in both existing regions and new regions. The Geo migration feature lets you move your finance and operations apps environments that are in a single tenant from one geography (or geo) to another. No changes to the user interface (UI) or version occur as part of the move.

Microsoft 365 and Dynamics 365 are separate services. If you move your finance and operations apps environments, your Microsoft 365 service isn't moved. Your finance and operations apps environments continue to appear alongside the Microsoft 365 environment in your tenant.

When a finance and operations apps environment is deployed in a geography, multiple Azure resources are associated with it. As part of the migration process, these resources are also moved from the source geography to the target geography.

## Considerations

Organizations that want to migrate environments from one geography to another must consider the following aspects before actual migration.

### Supported scenarios

- Sandbox and production environments can be migrated between geographies.
- Migration of cloud-hosted environments isn't supported.
- Migrations into or out of a sovereign cloud environment (for example, US Government Community Cloud \[GCC\] and China) aren't supported.

### Feature parity

Be sure to review the [availability of features in the selected target geography](deployment-options-geo.md#feature-availability-across-geographies) before you decide which geography to deploy in. If any features aren't available in the target geography, associated functionality won't work in that geography after migration. Therefore, plan the migration activity accordingly.

### Integration impact and updates with other services

- **Third party integrations:** If the migration crosses data resident geographies, the finance and operations apps environment endpoint changes. In this case, any third-party integrations that use the endpoint require change. For more information, see [Supported geographies and endpoints](deployment-options-geo.md#supported-geographies-and-endpoints).
- **Finance and operations apps add-ins and micro-services:** Add-in configurations aren't migrated as part of migration process. You must uninstall the add-ins before the migration and then reinstall them after the migration is completed. (For example, dual-write must be reconfigured in the target geography.)

### Timeline of actions and downtime

- We recommend that you migrate sandbox environments first and validate them before you trigger a production migration.
- Environment migrations aren't self-service operations and require a customer-initiated support ticket.
- Create your support request for migration at least 10 days before you want the environment to be migrated.
- The overall migration activity requires up to 48 hours of downtime. The overall time varies, depending on connectivity between the two geographies, and on the database and storage account size.
- If there's a linked Dataverse environment, it required another 24 hours of downtime.

### Geo migration between Lifecycle Services endpoints

The regions that are available for deploying environments show **Data resident** if the target region is the same region where Lifecycle Services stores data. For more information about how you can make finance and operations apps environments remain data resident with Lifecycle Services, see [Data residency](deployment-options-geo.md#data-residency).

Some supported geographies have different endpoint URLs. Movement between geographies can change the environment endpoint URL. For example, a move from the United States to Europe changes the environment endpoint (from NAME.operations.dynamics.com to NAME.operations._eu_.dynamics.com). A change in the environment endpoint affects any integrated service that takes a dependency on the correct endpoint URL. To learn what geographies change the URL, see the [list of available geographies and endpoints](deployment-options-geo.md#supported-geographies-and-endpoints).

## Environment migration process

We recommend that you migrate and sandbox environments first and validate them before you trigger a production migration.

After sandbox migration and validation are successfully completed, the project team can plan the time for production environment migration and follow these steps, starting with step 2. 

| Step | Responsible party | Description | Additional comments |
|------|-------------------|-------------|---------------------|
| 1 | Customer/Partner | Refresh the sandbox environment with production data. | Optional step if you're migrating a sandbox environment. |
| 2 | Customer/Partner | Submit a support request to migrate a specific environment. | Create your support request for migration at least 10 days before you want the environment to be migrated. The following information is required in the ticket: customer name, Azure Active Directory (Azure AD) tenant ID, environment ID, Lifecycle Services project ID that's associated with the environment, source geography, target geography, and preferred date and time. |
| 3 | Microsoft | Review the geo-to-geo migration request, and approve it. | |
| 4 | Customer/Partner | Before the start of the downtime, uninstall any microservices or add-ins. | |
| 5 | Microsoft | Perform the migration. | <p>Any associated Dataverse environments are migrated during same time frame.</p><p>Premigration work begins 12 hours before the scheduled downtime. During premigration, the environment remains available for use. However, the environment is put into an **Infrastructure Maintenance** state, so that no lifecycle management operations can be performed.</p></p>During the migration, finance and operations apps and Dataverse environments are unlinked. Both environments are migrated and then relinked after the migration is completed. |
| 6 | Microsoft | Confirm with the customer/partner that the migration was completed. | |
| 7 | Customer/Partner | Validate functionality in the migrated environment in the target geography. | Consider potential feature parity differences. |
| 8 | Customer/Partner | Reconfigure any add-ins, Commerce/point of sale (POS), third-party integrations, and so on. | Consider changes to endpoint URLs. |
