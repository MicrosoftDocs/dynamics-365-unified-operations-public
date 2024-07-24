---
title: Application lifecycle management for solutions that use virtual entities
description: Learn about the application lifecycle for solutions that use virtual entities for finance and operations, including an overview on solution management.
author: Sunil-Garg
ms.author: sunilg
ms.topic: article
ms.date: 07/13/2020
ms.custom: NotInToc
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-10-31
ms.search.form:
ms.dyn365.ops.version: 10.0.0
---

# Application lifecycle management for solutions that use virtual entities

[!include[banner](../includes/banner.md)]



> [!IMPORTANT]
> This functionality requires version 10.0.12 for finance and operations apps, while service update 189 is required for Dataverse. The release information for Dataverse is published on the [latest version availability page](/business-applications-release-notes/dynamics/released-versions/dynamics-365ce#all-version-availability).

The application lifecycle for an end-to-end solution using finance and operations virtual entities will encompass both finance and operations as well as Dataverse. This article explains this in detail.

## Solution management

Virtual entities for finance and operations don't exist in Dataverse until they are created. Virtual entities must be created inside a solution. The MicrosoftOperationsERPVE (Dynamics 365 ERP Virtual Entities) solution is used for this purpose. This solution will contain all the virtual entities that are created from an instance of finance and operations.

MicrosoftOperationsERPVE is a [managed solution](/powerapps/developer/common-data-service/introduction-solutions). By definition, a managed solution can't be modified after it has been generated. However, MicrosoftOperationsERPVE is a managed solution that grants privileges to update the components (that is, virtual entities) that are inside it. Therefore, new virtual entities can be added to the solution as they are created, and existing virtual entities can be updated as required. Nevertheless, the privileges to modify the managed solution are available only to the platform itself. Users can't make changes directly to the solution.

Because MicrosoftOperationsERPVE is a managed solution, solutions from customers, partners, and independent software vendors (ISVs) can take a dependency on it. This capability allows for consistent application lifecycle management (ALM) for solutions that use and depend on the virtual entities for finance and operations.

When a solution that depends on MicrosoftOperationsERPVE is exported, placeholders for the virtual entities that are used in the solution are added in the exported solution. When that solution is imported into another Dataverse environment, the import process also generates the dependent finance and operations virtual entities in the MicrosoftOperationsERPVE solution for the finance and operations instance that is connected to the Dataverse environment. Therefore, MicrosoftOperationsERPVE must already exist before a solution that depends on it is imported. Otherwise, an error message is shown. Additionally, if a dependent entity isn't available in the finance and operations instance, the virtual entity for that entity won't be generated. Virtual entities are generated only for entities that are available.

> [!NOTE]
> If a virtual entity already exists in Dataverse and a solution is being imported that now references new fields in the virtual entity which does not exist in Dataverse, a manual refresh must be performed on the virtual entity to get the latest metadata from finance and operations.

The following list describes other solutions that finance and operations virtual entities require to work, and that must be available in the Dataverse environment:

- **MicrosoftOperationsERPCatalog (Microsoft Operations ERP Catalog)** – This solution provides a catalog of the available entities in a finance and operations instance. It also provides the connection that is used to set up a configuration. For more information, see the later sections of this article.
- **MicrosoftOperationsVESupport (Dynamics Operations Virtual Entity Support)** – This solution provides the virtual entity provider for finance and operations apps. The provider can communicate with finance and operations apps and Dataverse. For more information, see the next section.
- **Dynamics365Company (Dynamics 365 Company)** – This solution adds the Company entity, which is referenced by all finance and operations entities that have a **PrimaryCompanyContext** metadata value.

All these solutions must be present in an environment. Otherwise, virtual entities won't work with finance and operations apps. These solutions are packaged together to allow for easier portability across environments.

## Managing entities from multiple environments

The MicrosoftOperationsVESupport solution consists of the **msdyn\_financeandoperationsvirtualentity** entity. This entity represents the virtual entity data source for finance and operations that captures connection setup information. Each record in this entity represents a connection to a finance and operations instance.

A catalog is used to list all the entities in a finance and operations instance that are available for virtualization in Dataverse (in other words, all the entities in finance and operations that are enabled for Open Data Protocol \[OData\]). The catalog is part of the default MicrosoftOperationsERPCatalog solution and is applicable to a finance and operations instance.

Note that each Dataverse environment must point to only one finance and operations instance at any time, and each finance and operations environment must point to only one Dataverse environment. Therefore, there should be only one record in the **msdyn\_financeandoperationsvirtualentity** entity.

The **mserp\_financeandoperationsentity** entity that represents the catalog can be queried to list the entities in a finance and operations instance. Because this entity is a virtual entity, the catalog is never persisted in Dataverse.

Notice that the name of the catalog entity has the "mserp\_" prefix. This prefix identifies the entities in the catalog as finance and operations entities. The same prefix is also added to the system names of the virtual entities that are generated for finance and operations in the MicrosoftOperationsERPVE solution. Therefore, the maker can distinguish finance and operations virtual entities from other entities. The prefix is set in the managed solution and can't be changed.

### Managing entities from multiple ISV solutions

One or more ISV solutions will take a dependency on the MicrosoftOperationsERPVE solution to use virtual entities for finance and operations. Because custom entities in finance and operations use the same catalog as out-of-box entities in finance and operations, the virtual entities for custom finance and operations entities will also be generated in the MicrosoftOperationsERPVE solution.

The established guidelines and ALM for entity development in finance and operations ensure that there are no conflicting entity names across ISV solutions. Therefore, no conflicts of this type can occur when virtual entities are generated in Dataverse for custom finance and operations entities from multiple ISV solutions. All virtual entities for finance and operations entities, including custom entities, will have the "mserp\_" prefix that was mentioned earlier.

### Managing a Finance and Operation instance in a Dataverse environment for virtual entities

One finance and operations instance must be linked to a Dataverse environment for virtual entities. The connection setup information that is required is captured in a virtual entity data source for finance and operations. This data source is included in the MicrosoftOperationsERPCatalog solution.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
