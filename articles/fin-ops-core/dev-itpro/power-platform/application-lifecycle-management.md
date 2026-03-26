---
title: Application lifecycle management for solutions that use virtual entities
description: Learn about the application lifecycle for solutions that use virtual entities for finance and operations, including an overview on solution management.
author: Sunil-Garg
ms.author: sunilg
ms.topic: article
ms.date: 03/16/2026
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

The application lifecycle for an end-to-end solution that uses finance and operations virtual entities includes both finance and operations and Dataverse. This article explains this application lifecycle.

## Solution management

Virtual entities for finance and operations don't exist in Dataverse until you create them. You must create virtual entities inside a solution. Use the MicrosoftOperationsERPVE (Dynamics 365 ERP Virtual Entities) solution for this purpose. This solution contains all the virtual entities that you create from an instance of finance and operations.

MicrosoftOperationsERPVE is a [managed solution](/powerapps/developer/common-data-service/introduction-solutions). By definition, you can't modify a managed solution after it's generated. However, MicrosoftOperationsERPVE is a managed solution that grants privileges to update the components (that is, virtual entities) that are inside it. Therefore, you can add new virtual entities to the solution and update existing virtual entities. However, only the platform has the privileges to modify the managed solution. Users can't make changes directly to the solution.

Because MicrosoftOperationsERPVE is a managed solution, solutions from customers, partners, and independent software vendors (ISVs) can take a dependency on it. This capability allows for consistent application lifecycle management (ALM) for solutions that use and depend on the virtual entities for finance and operations.

When you export a solution that depends on MicrosoftOperationsERPVE, you add placeholders for the virtual entities that the solution uses. When you import the solution into another Dataverse environment, the import process also generates the dependent finance and operations virtual entities in the MicrosoftOperationsERPVE solution for the finance and operations instance that connects to the Dataverse environment. Therefore, MicrosoftOperationsERPVE must already exist before you import a solution that depends on it. Otherwise, an error message is shown. Additionally, if a dependent entity isn't available in the finance and operations instance, the virtual entity for that entity isn't generated. Virtual entities are generated only for entities that are available.

> [!NOTE]
> If a virtual entity already exists in Dataverse and you import a solution that now references new fields in the virtual entity which don't exist in Dataverse, you must manually refresh the virtual entity to get the latest metadata from finance and operations.

The following list describes other solutions that finance and operations virtual entities require to work, and that must be available in the Dataverse environment:

- **MicrosoftOperationsERPCatalog (Microsoft Operations ERP Catalog)** – This solution provides a catalog of the available entities in a finance and operations instance. It also provides the connection that is used to set up a configuration. For more information, see the later sections of this article.
- **MicrosoftOperationsVESupport (Dynamics Operations Virtual Entity Support)** – This solution provides the virtual entity provider for finance and operations apps. The provider can communicate with finance and operations apps and Dataverse. For more information, see the next section.
- **Dynamics365Company (Dynamics 365 Company)** – This solution adds the Company entity, which all finance and operations entities with a **PrimaryCompanyContext** metadata value reference.

All these solutions must be present in an environment. Otherwise, virtual entities don't work with finance and operations apps. These solutions are packaged together to make it easier to port them across environments.

## Managing entities from multiple environments

The MicrosoftOperationsVESupport solution includes the **msdyn\_financeandoperationsvirtualentity** entity. This entity represents the virtual entity data source for finance and operations that captures connection setup information. Each record in this entity represents a connection to a finance and operations instance.

A catalog lists all the entities in a finance and operations instance that are available for virtualization in Dataverse (in other words, all the entities in finance and operations that are enabled for Open Data Protocol \[OData\]). The catalog is part of the default MicrosoftOperationsERPCatalog solution and applies to a finance and operations instance.

Each Dataverse environment must point to only one finance and operations instance at any time, and each finance and operations environment must point to only one Dataverse environment. Therefore, there should be only one record in the **msdyn\_financeandoperationsvirtualentity** entity.

You can query the **mserp\_financeandoperationsentity** entity that represents the catalog to list the entities in a finance and operations instance. Because this entity is a virtual entity, the catalog is never persisted in Dataverse.

The name of the catalog entity has the "mserp\_" prefix. This prefix identifies the entities in the catalog as finance and operations entities. The same prefix is also added to the system names of the virtual entities that are generated for finance and operations in the MicrosoftOperationsERPVE solution. Therefore, makers can distinguish finance and operations virtual entities from other entities. The prefix is set in the managed solution and can't be changed.

### Managing entities from multiple ISV solutions

One or more ISV solutions take a dependency on the MicrosoftOperationsERPVE solution to use virtual entities for finance and operations. Because custom entities in finance and operations use the same catalog as out-of-box entities in finance and operations, the MicrosoftOperationsERPVE solution also generates the virtual entities for custom finance and operations entities.

The established guidelines and ALM for entity development in finance and operations ensure that there are no conflicting entity names across ISV solutions. Therefore, these guidelines and ALM prevent conflicts when you generate virtual entities in Dataverse for custom finance and operations entities from multiple ISV solutions. All virtual entities for finance and operations entities, including custom entities, use the "mserp\_" prefix that was mentioned earlier.

### Managing a finance and operations instance in a Dataverse environment for virtual entities

You must link one finance and operations instance to a Dataverse environment for virtual entities. The virtual entity data source for finance and operations captures the connection setup information that you need. The MicrosoftOperationsERPCatalog solution includes this data source.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
