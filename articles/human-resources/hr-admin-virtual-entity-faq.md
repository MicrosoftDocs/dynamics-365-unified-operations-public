---
# required metadata

title: Human Resources virtual entities FAQ
description: This topic is a list of frequently asked questions about Human Resources virtual entities.
author: jaredha
manager: tfehr
ms.date: 12/15/2020
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
ms.search.validFrom: 2020-12-15
ms.dyn365.ops.version: 10.0.12
---

# Human Resources virtual entities FAQ

[!include[banner](../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic is a collection of frequently asked questions about virtual entities in Dynamics 365 Human Resources. 

### Can a solution from an independent software vendor (ISV) take a dependency on virtual entities? What does the application lifecycle management (ALM) look like?

Yes. The virtual entities are all generated in the Dynamics 365 HR Virtual Entities solution, which is API-managed. The items in the solution change as you make entities visible or hidden. However, the solution is still a managed solution that you can take dependency on. The schema and contract for each entity is maintained. The standard ALM flow just takes a standard reference to a virtual entity from this solution with the ISV solution's **Add existing** option. Missing dependency of the solution will be checked when the solution is imported. During import, if a specified virtual entity doesn't yet exist, the virtual entity is automatically made visible.

### Which entities from Human Resources do users see in the catalog in Common Data Service?

Generally, users see all entities where **IsPublic** is set to **Yes**. These entities are the same entities that are currently visible in Open Data Protocol (OData).

### Do all Microsoft Power Platform users have to be users in Human Resources?

Any user of Microsoft Power Platform who tries to access Human Resources data through a virtual entity must also exist as a user in Human Resources. So not *all* users must be users in Human Resources. Only those users who access Human Resources data through virtual entities must be users in Human Resources.

### Where do I find the catalog entity?

The entity catalog is listed on the **Virtual entities** tab of the **Common Data Service (CDS) integration** page in the Human Resources application. All available entities are listed after setup and configuration is completed. For more information, see [Configure Common Data Service virtual entities](./hr-admin-integration-common-data-service-virtual-entities).

### Is there a way to specify a company when I perform data operations on a virtual entity?

Yes. Although the company is implicit in Human Resources, it's an explicit field on each company-striped entity in Common Data Service. You can use either the **Company Code** field, where the value is a four-character string, or the **Company** field, which is a lookup to cdm\_Company. Both approaches provide the same information.

If you're accessing the entity through the CDS Web API, the company is identified by the **Data Area ID** property (mshr\_dataareaid). Each company-specific entity with this property has a navigation property to the cdm\_Company entity.

### Can I change the prefix for the virtual entities?

No. All Human Resources virtual entities should be generated in the Dynamics 365 HR Virtual Entities solution and have the "mshr\_" prefix. Don't change this prefix. If you have a scenario where you believe the prefix has to be changed, you should share that scenario with Microsoft.

### How can I filter data in a Power Apps app, based on the current user or any other dynamic criteria, such as today-10?

You can write a pre-operation plug-in on the RetrieveMultiple message of the entity and change the criteria on the query in it. Alternatively, you can write a post-operation plug-in to filter the results before they're returned.

### How can I show, in the same grid, data from multiple virtual entities that are joined to a physical entity record in Common Data Service?

This approach isn't currently possible in Common Data Service.

### If I want a default value to be entered in a field during pre-create, will an initValue on the data entity work?

Yes. Here's the order of calls:

1. Common Data Service sends a create or update message.
2. All the existing logic on the Human Resources entity and backing tables is invoked. This logic includes default value entry that might change values.
3. Common Data Service sends another Retrieve (single) message to get the latest copy of the data, including any fields that default values were entered for.

### Does the form business logic in Human Resources get called through virtual entities?

Human Resources business logic on forms isn't invoked through virtual entities. Instead, expect the same behavior that you get through OData access to the same entities. An entity exposed to OData (that is, **IsPublic** is set to **Yes**) should have appropriate protections to ensure data can't be corrupted. If any entity lacks this protection, that situation represents a bug in the entity. If you see differences in entity behavior between OData and virtual entities, that situation represents a bug in the virtual entity feature.

### When adding records using virtual entities is there any way to use number sequences?

Yes, if the Human Resources entity can auto generate number sequences, then it will work the same way from the virtual entity.

### Why doesn't search view work in Power Apps?

If there are no fields added in the quick find view for the entity, then the search box does nothing. The workaround is to add one or more fields of the entity to the quick find view.


