---
# required metadata

title: Finance and Operations virtual entities FAQ
description: This topic is a list of frequently asked questions about Finance and Operations virtual entities.
author: Sunil-Garg
manager: AnnBe
ms.date: 09/17/2020
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
ms.search.validFrom: 2020-05-31
ms.dyn365.ops.version: 10.0.12
---

# Finance and Operations virtual entities FAQ

[!include[banner](../includes/banner.md)]

> [!IMPORTANT]
> This functionality requires version 10.0.12 for Finance and Operations apps, while service update 189 is required for Common Data Service. The release information for Common Data Service is published on the [latest version availability page](https://docs.microsoft.com/business-applications-release-notes/dynamics/released-versions/dynamics-365ce#all-version-availability).

This topic is a collection of frequently asked questions about Finance and Operations virtual entities. 

### Do Tier 1 Finance and Operations environments or demo topologies work?

Yes, Tier 1 and DEVTEST and DEMO topologies should work.

### What version of Finance and Operations do I need?

10.0.12 is the minimum version that is required.

### Can a solution from an independent software vendor (ISV) take a dependency on virtual entities? What does the application lifecycle management (ALM) look like?

Yes. The virtual entities are all generated in the MicrosoftOperationsERPVE solution, which isAPI-managed In other words, the items in the solution change as you make entities visible or hidden, but the solution is still a managed solution that you can take dependency on. The standard ALM flow just takes a standard reference to a virtual entity from this solution with the **Add existing** option in the ISV solution. Missing dependency of the solution will be checked when the solution is imported and during import, if a specified virtual entity doesn't yet exist, the virtual entity is automatically made visible.

### Which entities from Finance and Operations do users see in the catalog in Common Data Service?

Generally, users see all entities where **IsPublic** is set to **Yes**. These entities are the same entities that are currently visible in Open Data Protocol (OData).

### Do all Microsoft Power Platform users have to be users in Finance and Operations?

Any user of Microsoft Power Platform who tries to access Finance and Operations data through a virtual entity must also exist as a user in Finance and Operations. Therefore, technically, not *all* users have to be users in Finance and Operations. Only those users who access Finance and Operations data through virtual entities must be users in Finance and Operations.

### Where do I find the catalog entity?

In the **Advanced find** window, the entity is named **Available Finance and Operations Entities**.

### Is there a way to specify a company when I perform data operations on a virtual entity?

Yes. Although the company is implicit in Finance and Operations, it's an explicit field on each company-striped entity in Common Data Service. You can use either the **Company Code** field, where the value is a four-character string, or the **Company** field, which is a lookup to cdm\_Company. Both approaches provide the same information.

### Can I change the prefix for the virtual entities?

No. All Finance and Operations virtual entities should be generated in the MicrosoftOperationsERPVE solution, and they should all have the "mserp\_" prefix. This prefix should not be changed. If you have a scenario where you believe the prefix has to be changed, you should share that scenario with Microsoft.

### How can I filter data in an app that is created by using Power Apps, based on the current user or any other dynamic criteria, such as today-10?

You can write a pre-operation plug-in on the RetrieveMultiple message of the entity and change the criteria on the query in it. Alternatively, you can write a post-operation plug-in to filter the results before they are returned.

### Can I pin a model-driven app into Finance and Operations?

No, it isn't currently possible to pin a model-driven app into Finance and Operations.

### How can I show, in the same grid, data from multiple virtual entities that are joined to a physical entity record in Common Data Service?

This approach isn't currently possible in Common Data Service.

### How do I add subcomponents in the new Power Apps experience?

As in the previous Power Apps user interface (UI), you must redo the **Add Existing** operation. After the solution is selected, and Customer Groups has already been added as an entity, follow these steps.

1. Select **Add existing** \> **Entity**.
2. Select customer group entity, and then select **Next**.
3. Under **Components**, select **Select components**.
4. Select the fields, relationships, and forms that you want, and then select **Add**.

### If I want a default value to be entered in a field during pre-create, will an initValue on the data entity work?

Yes. Here is the order of calls:

1. Common Data Service sends a create or update message.
2. All the existing logic on the Finance and Operations entity and backing tables is invoked. This logic includes default value entry that might change values.
3. Common Data Service sends another Retrieve (single) message to get the latest copy of the data, including any fields that default values were entered for.

### Can I debug Finance and Operations when we do a create, read, update, and delete (CRUD) operation from Common Data Service? If so, which process do I have to attach?

Yes, to debug in Finance and Operations, open Visual Studio as an admin. Typically, Finance and Operations apps run under w3wp.exe as a process. However, when you open Visual Studio as an admin, IISExpress.exe is automatically opened, and Finance and Operations is hosted there. You can attach to IISExpress.exe (or to w3wp.exe if not running Visual Studio as an admin). To set breakpoints in the virtual entity code, find the **CDSVirtualEntityAdapter** and **CDSVirtualEntityController** classes. The adapter class is the first class that is called, and it only does serialization/deserialization. It then delegates to the controller class to do the actual queries. Therefore, the controller class is usually the easiest place to put breakpoints.

### Does the form business logic in Finance and Operations get called through virtual entities?

Finance and Operations business logic that resides on forms isn't invoked through virtual entities. Instead, you should expect the same behavior that you get through OData access to the same entities. The expectation is that an entity that is exposed to OData (that is, **IsPublic** is set to **Yes**) has appropriate protections to ensure that data can't be corrupted. If any entity lacks this protection, that situation represents a bug in the entity. If you see differences in entity behavior between OData and virtual entities, that situation represents a bug in the virtual entity feature.

### If I develop a new Finance and Operations entity and want to see it in Common Data Service, do I have to select Refresh entity list in Finance and Operations? Do I have to do anything in Common Data Service?

In theory, no, you don't have to refresh the entity list. At most, you might have to either reset Internet Information Services (IIS) or restart IIS Express, depending on where Application Object Server (AOS) is running. The fact that the list of entities is accurate is cached in SysGlobalObjectCache, which is a per-process cache. Any time that this cache doesn't indicate that the list is accurate, the list is rebuilt. The rebuild process takes about five seconds. Therefore, when you restart your AOS process (w3wp.exe or iisexpress.exe), the list will be accurate the next time that you query it from Common Data Service. Additionally, although recompilation *should* flush the SysGlobalObjectCache cache, it might not. In that case, an AOS restart will flush it.

### Do you have guidance on when to use a virtual entity and when to use dual-write?

Dual-write is only provided for a few key data entities where the data needs to be natively in Common Data Service. Those data entities are not available as virtual entities.

### When adding records using virtual entities is there any way to use number sequences?
Yes, if the Finance and Operations entity can auto generate number sequences, then it will work the same way from the virtual entity.

### Why does the 'search vew' does not work in Power Apps?
If there are no fields added in the quickfind view for the entity, then the search box does nothing. The workaround until this is fixed in UCI is just to add one or more fields of the entity to the quickfind view.


