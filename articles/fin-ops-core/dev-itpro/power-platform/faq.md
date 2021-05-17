---
# required metadata

title: Finance and Operations virtual entities FAQ
description: This topic is a list of frequently asked questions about Finance and Operations virtual entities.
author: Sunil-Garg
ms.date: 03/31/2021
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: sunilg
ms.search.validFrom: 2020-05-31
ms.dyn365.ops.version: 10.0.12
---

# Finance and Operations virtual entities FAQ

[!include[banner](../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

> [!IMPORTANT]
> This functionality requires version 10.0.12 for Finance and Operations apps, while service update 189 is required for Dataverse. The release information for Dataverse is published on the [latest version availability page](/business-applications-release-notes/dynamics/released-versions/dynamics-365ce#all-version-availability).

This topic is a collection of frequently asked questions about Finance and Operations virtual entities. 

### Do Tier 1 Finance and Operations environments or demo topologies work?

Yes, Tier 1 and DEVTEST and DEMO topologies should work.

### What version of Finance and Operations do I need?

10.0.12 is the minimum version that is required.

### Can a solution from an independent software vendor (ISV) take a dependency on virtual entities? What does the application lifecycle management (ALM) look like?

Yes. The virtual entities are all generated in the MicrosoftOperationsERPVE solution, which isAPI-managed In other words, the items in the solution change as you make entities visible or hidden, but the solution is still a managed solution that you can take dependency on. The standard ALM flow just takes a standard reference to a virtual entity from this solution with the **Add existing** option in the ISV solution. Missing dependency of the solution will be checked when the solution is imported and during import, if a specified virtual entity doesn't yet exist, the virtual entity is automatically made visible.

### Which entities from Finance and Operations do users see in the catalog in Dataverse?

Generally, users see all entities where **IsPublic** is set to **Yes**. These entities are the same entities that are currently visible in Open Data Protocol (OData).

### Do all Microsoft Power Platform users have to be users in Finance and Operations?

Any **interactive user** of Microsoft Power Platform who tries to access Finance and Operations data through a virtual entity must also exist as a user in Finance and Operations. Therefore, technically, not *all* users have to be users in Finance and Operations. Only those users who access Finance and Operations data through virtual entities must be users in Finance and Operations.

A **S2S application user** can also be used to call into virtual entities. For this kind of integration, the application user must be set up in **System administration > Setup > Configure Azure Active Directory Applications**. This allows for applications to integrate with Finance and Operations using virtual entities.

### Where do I find the catalog entity?

In the **Advanced find** window, the entity is named **Available Finance and Operations Entities**.

### Is there a way to specify a company when I perform data operations on a virtual entity?

Yes. Although the company is implicit in Finance and Operations, it's an explicit field on each company-striped entity in Dataverse. You can use either the **Company Code** field, where the value is a four-character string, or the **Company** field, which is a lookup to cdm\_Company. Both approaches provide the same information.

### Can I change the prefix for the virtual entities?

No. All Finance and Operations virtual entities should be generated in the MicrosoftOperationsERPVE solution, and they should all have the "mserp\_" prefix. This prefix should not be changed. If you have a scenario where you believe the prefix has to be changed, you should share that scenario with Microsoft.

### How can I filter data in an app that is created by using Power Apps, based on the current user or any other dynamic criteria, such as today-10?

You can write a pre-operation plug-in on the RetrieveMultiple message of the entity and change the criteria on the query in it. Alternatively, you can write a post-operation plug-in to filter the results before they are returned.

### Can I pin a model-driven app into Finance and Operations?

No, it isn't currently possible to pin a model-driven app into Finance and Operations.

### How can I show, in the same grid, data from multiple virtual entities that are joined to a physical entity record in Dataverse?

This approach isn't currently possible in Dataverse.

### How do I add subcomponents in the new Power Apps experience?

As in the previous Power Apps user interface (UI), you must redo the **Add Existing** operation. After the solution is selected, and Customer Groups has already been added as an entity, follow these steps.

1. Select **Add existing** \> **Entity**.
2. Select customer group entity, and then select **Next**.
3. Under **Components**, select **Select components**.
4. Select the fields, relationships, and forms that you want, and then select **Add**.

### If I want a default value to be entered in a field during pre-create, will an initValue on the data entity work?

Yes. Here is the order of calls:

1. Dataverse sends a create or update message.
2. All the existing logic on the Finance and Operations entity and backing tables is invoked. This logic includes default value entry that might change values.
3. Dataverse sends another Retrieve (single) message to get the latest copy of the data, including any fields that default values were entered for.

### Can I debug Finance and Operations when we do a create, read, update, and delete (CRUD) operation from Dataverse? If so, which process do I have to attach?

Yes, to debug in Finance and Operations, open Visual Studio as an admin. Typically, Finance and Operations apps run under w3wp.exe as a process. However, when you open Visual Studio as an admin, IISExpress.exe is automatically opened, and Finance and Operations is hosted there. You can attach to IISExpress.exe (or to w3wp.exe if not running Visual Studio as an admin). To set breakpoints in the virtual entity code, find the **CDSVirtualEntityAdapter** and **CDSVirtualEntityController** classes. The adapter class is the first class that is called, and it only does serialization/deserialization. It then delegates to the controller class to do the actual queries. Therefore, the controller class is usually the easiest place to put breakpoints.

### Does the form business logic in Finance and Operations get called through virtual entities?

Finance and Operations business logic that resides on forms isn't invoked through virtual entities. Instead, you should expect the same behavior that you get through OData access to the same entities. The expectation is that an entity that is exposed to OData (that is, **IsPublic** is set to **Yes**) has appropriate protections to ensure that data can't be corrupted. If any entity lacks this protection, that situation represents a bug in the entity. If you see differences in entity behavior between OData and virtual entities, that situation represents a bug in the virtual entity feature.

### If I develop a new Finance and Operations entity and want to see it in Dataverse, do I have to select Refresh entity list in Finance and Operations? Do I have to do anything in Dataverse?

In theory, no, you don't have to refresh the entity list. At most, you might have to either reset Internet Information Services (IIS) or restart IIS Express, depending on where Application Object Server (AOS) is running. The fact that the list of entities is accurate is cached in SysGlobalObjectCache, which is a per-process cache. Any time that this cache doesn't indicate that the list is accurate, the list is rebuilt. The rebuild process takes about five seconds. Therefore, when you restart your AOS process (w3wp.exe or iisexpress.exe), the list will be accurate the next time that you query it from Dataverse. Additionally, although recompilation *should* flush the SysGlobalObjectCache cache, it might not. In that case, an AOS restart will flush it.

### Is there guidance on when to use a virtual entity and when to use dual-write?

Guidance on when to use a virtual entity and when to use dual-write is covered in [Integration between Finance and Operations apps and third-party services](../data-entities/integration-overview.md).

### When adding records using virtual entities is there any way to use number sequences?
Yes, if the Finance and Operations entity can auto generate number sequences, then it will work the same way from the virtual entity.

### Why does 'search view' not work in Power Apps?
If there are no fields added in the quick find view for the entity, then the search box does nothing. The workaround is to add one or more fields of the entity to the quick find view.

### The virtual entity performance is slow when a virtual entity has relationships to other entities. Is there guidance on how to avoid these issues?
There could be several reasons why performance is slow when a virtual entity has relationships to other entities. This section will be updated as new patterns are identified. The following  is  currently known patterns, which can be used as a guidance.

When virtual entities have relationships to other entities, the virtual entity framework needs to query the related entities if the field select list includes the foreign key values for the related entities. By default, queries against the entities return all fields unless the caller requests a specific set of fields. The best practice is to specify a narrow select list. This can help to prevent slow performance.

An example of this issue is explained in [Optimize Dataverse virtual table queries](../../../human-resources/hr-developer-optimize-virtual-table-queries.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
