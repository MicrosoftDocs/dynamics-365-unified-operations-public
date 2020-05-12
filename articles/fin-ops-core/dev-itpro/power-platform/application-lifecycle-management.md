---
# required metadata

title: Application lifecycle management
description: Description goes here.
author: Sunil-Garg
manager: AnnBe
ms.date: 05/20/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: sunilg
ms.search.validFrom: 2020-10-31
ms.dyn365.ops.version: 10.0.0
---

# Application lifecycle management

[!include[banner](../includes/banner.md)]

## Solution management

Virtual entities for Finance and Operations don’t exist in the Common Data Service until they are created. When virtual entities are created, they must be created inside a solution. A solution called MicrosoftOperationsERPVE is used for this purpose which will contain all the generated virtual entities from an instance of Finance and Operations.

MicrosoftOperationsERPVE is a [managed solution](https://docs.microsoft.com/powerapps/developer/common-data-service/introduction-solutions). By definition, a managed solution cannot be modified once it has been generated. MicrosoftOperationsERPVE is, however, a managed solution with privileges to update the components (virtual entities) in itself, which allows new virtual entities to be added to the solution as they are created and existing virtual entities to be updated, as needed. This privilege to modify the managed solution is only available to the platform itself. Users cannot directly make changes to this solution.

Customer, partner, and ISV solutions can take a dependency on the MicrosoftOperationsERPVE solution since it is a managed solution. This allows for a consistent application lifecycle management for solutions that use and depend on the virtual entities for Finance and Operations. When a solution that depends on MicrosoftOperationsERPVE is exported, place holders for the virtual entities that are used in the solution are placed in the exported solution. When the solution is imported in another Common Data Service environment, the solution import process will also generate the dependent Finance and Operations virtual entities in the MicrosoftOperationsERPVE solution for the Finance and Operations instance connected to the Common Data Service environment. It is therefore expected for MicrosoftOperationsERPVE to exist before such a solution is imported. If MicrosoftOperationsERPVE does not exist during import of a solution that depends on it, then an error is displayed. Similarly, if a dependent entity is not available in the Finance and Operations instance, the virtual entity for such an entity will not be generated. Entities that are available will have their virtual entity generated.

Other solutions that are a pre-requisite for Finance and Operations virtual entities to work and are also expected to be available in the Common Data Service environment are described below.

-   **MicrosoftOperationsERPCatalog** - This solution provides a catalog to show the available entities in a Finance and Operations instance and provides the connection to set up configuration. This is discussed subsequently.

-   **MicrosoftOperationsVESupport** - This provides the virtual entity provider for Finance and Operations apps. The provider knows how to talk to Finance and Operations apps and Common Data Service and is explained in a subsequent section.

-   **Dynamics365Company** - This adds the “Company” entity, which is referenced by all Finance and Operations entities with a PrimaryCompanyContext metadata value.

All solutions are required in an environment for virtual entities to work with Finance and Operations apps. These solutions are packaged together for ease of portability across environments.

## Managing entities from multiple environments

The MicrosoftOperationsVESupport solution consists of msdyn_financeandoperationsvirtualentity entity. This entity represents the
virtual entity data source for Finance and Operations which is the connection set up. Each record in this entity will represent a connection to a Finance and Operations instance.

A catalog is used to list the entities in an instance of Finance and Operations that are available to be virtualized in Common Data Service (all OData enabled entities in Finance and Operations). The catalog is part of the default solution MicrosoftOperationsERPCatalog and is applicable to an instance of Finance and Operations. It must be taken into account that, a CDS environment must only point to one and only one Finance and Operations instance at any given time and a Finance and Operations environment must point to one and only one Common Data Service environment. This means, there should only be one record in the msdyn_financeandoperationsvirtualentity entity.

The mserp_financeandoperationsentity which represents the catalog can be queried to list the entities in an instance of Finance and Operations. This entity is a virtual entity and hence, the catalog is never persisted in Common Data Service.

The catalog entity name has a prefix of mserp which identifies the entities in the catalog as the Finance and Operations entity. This same prefix is also used as the prefix to the system names of the virtual entities generated for Finance and Operations in MicrosoftOperationsERPVE solution. This helps to disambiguate Finance and Operations virtual entities from other entities for the Maker. The prefix name cannot be changed as it is set in the managed solution.

### Managing entities from multiple ISV solutions

One or more ISV solutions will take a dependency on the MicrosoftOperationsERPVE solution to use virtual entities for Finance and Operations. Since custom entities in Finance and Operations will use the same catalog like any other out of the box entities in Finance and Operations, the virtual entities for such custom Finance and Operations entities will also be generated in the MicrosoftOperationsERPVE solution.

The established guidelines and application lifecycle management for entity development in Finance and Operations will ensure there are no entity name conflicts across ISV solutions. As a result, this will also ensure there are no such conflicts that can arise when virtual entities are generated in CDS for custom Finance and Operations entities from across multiple ISV solutions. All
virtual entities for Finance and Operations entities, including custom entities, will have the mserp prefix as described earlier.

### Managing Finance and Operation instance in CDS for virtual entities

One instance of Finance and Operations must be linked to a Common Data Service environment for virtual entities. The connection set up information required is captured in a virtual entity data source for Finance and Operations which is included in the MicrosoftOperationsERPCatalog. The steps to set this up is described in subsequent section.
