---
title: Finance and operations virtual entities FAQ
description: Access a list of frequently asked questions about finance and operations virtual entities, including answers to questions relating to versions of environments.
author: Sunil-Garg
ms.author: sunilg
ms.topic: article
ms.date: 08/03/2022
ms.custom: NotInToc
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-05-31
ms.search.form:
ms.dyn365.ops.version: 10.0.12
---

# Finance and operations virtual entities FAQ

[!include[banner](../includes/banner.md)]



> [!IMPORTANT]
> This functionality requires version 10.0.12 for finance and operations apps, while service update 189 is required for Dataverse. The release information for Dataverse is published on the [latest version availability page](/business-applications-release-notes/dynamics/released-versions/dynamics-365ce#all-version-availability).

This article is a collection of frequently asked questions about finance and operations virtual entities. 

### Do Tier 1 finance and operations environments or demo topologies work?

Yes, Tier 1 and DEVTEST and DEMO topologies should work.

### What version of finance and operations do I need?

10.0.12 is the minimum version that is required.

### Can a solution from an independent software vendor (ISV) take a dependency on virtual entities? What does the application lifecycle management (ALM) look like?

Yes. The virtual entities are all generated in the MicrosoftOperationsERPVE solution, which isAPI-managed In other words, the items in the solution change as you make entities visible or hidden, but the solution is still a managed solution that you can take dependency on. The standard ALM flow just takes a standard reference to a virtual entity from this solution with the **Add existing** option in the ISV solution. Missing dependency of the solution will be checked when the solution is imported and during import, if a specified virtual entity doesn't yet exist, the virtual entity is automatically made visible.

### Which entities from finance and operations do users see in the catalog in Dataverse?

Generally, users see all entities where **IsPublic** is set to **Yes**. These entities are the same entities that are currently visible in Open Data Protocol (OData).

### Do all Microsoft Power Platform users have to be users in finance and operations?

Any **interactive user** of Microsoft Power Platform who tries to access finance and operations data through a virtual entity must also exist as a user in finance and operations. Therefore, technically, not *all* users have to be users in finance and operations. Only those users who access finance and operations data through virtual entities must be users in finance and operations.

A **S2S application user** can also be used to call into virtual entities. For this kind of integration, the application user must be set up in **System administration > Setup > Configure Microsoft Entra Applications**. This allows for applications to integrate with finance and operations using virtual entities.

### Where do I find the catalog entity?

In the **Advanced find** window, the entity is named **Available finance and operations Entities**.

### Is there a way to specify a company when I perform data operations on a virtual entity?

Yes. Although the company is implicit in finance and operations, it's an explicit field on each company-striped entity in Dataverse. You can use either the **Company Code** field, where the value is a four-character string, or the **Company** field, which is a lookup to cdm\_Company. Both approaches provide the same information.

### Can I change the prefix for the virtual entities?

No. All finance and operations virtual entities should be generated in the MicrosoftOperationsERPVE solution, and they should all have the "mserp\_" prefix. This prefix should not be changed. If you have a scenario where you believe the prefix has to be changed, you should share that scenario with Microsoft.

### How can I filter data in an app that is created by using Power Apps, based on the current user or any other dynamic criteria, such as today-10?

You can write a pre-operation plug-in on the RetrieveMultiple message of the entity and change the criteria on the query in it. Alternatively, you can write a post-operation plug-in to filter the results before they are returned.

### Can I pin a model-driven app into finance and operations?

No, it isn't currently possible to pin a model-driven app into finance and operations.

### How can I show, in the same grid, data from multiple virtual entities that are joined to a physical entity record in Dataverse?

This approach isn't currently possible in Dataverse.

### How do I add subcomponents in the new Power Apps experience?

As in the previous Power Apps user interface (UI), you must redo the **Add Existing** operation. After the solution is selected, and Customer Group has already been added as an entity, follow these steps.

1. Select **Add existing** \> **Entity**.
2. Select customer group entity, and then select **Next**.
3. Under **Components**, select **Select components**.
4. Select the fields, relationships, and forms that you want, and then select **Add**.

### If I want a default value to be entered in a field during pre-create, will an initValue on the data entity work?

Yes. Here is the order of calls:

1. Dataverse sends a create or update message.
2. All the existing logic on the finance and operations entity and backing tables is invoked. This logic includes default value entry that might change values.
3. Dataverse sends another Retrieve (single) message to get the latest copy of the data, including any fields that default values were entered for.

### Can I debug finance and operations when we do a create, read, update, and delete (CRUD) operation from Dataverse? If so, which process do I have to attach?

Yes, to debug in finance and operations, open Visual Studio as an admin. Typically, finance and operations apps run under w3wp.exe as a process. However, when you open Visual Studio as an admin, IISExpress.exe is automatically opened, and finance and operations is hosted there. You can attach to IISExpress.exe (or to w3wp.exe if not running Visual Studio as an admin). To set breakpoints in the virtual entity code, find the **CDSVirtualEntityAdapter** and **CDSVirtualEntityController** classes. The adapter class is the first class that is called, and it only does serialization/deserialization. It then delegates to the controller class to do the actual queries. Therefore, the controller class is usually the easiest place to put breakpoints.

### Does the form business logic in finance and operations get called through virtual entities?

Finance and operations business logic that resides on forms isn't invoked through virtual entities. Instead, you should expect the same behavior that you get through OData access to the same entities. The expectation is that an entity that is exposed to OData (that is, **IsPublic** is set to **Yes**) has appropriate protections to ensure that data can't be corrupted. If any entity lacks this protection, that situation represents a bug in the entity. If you see differences in entity behavior between OData and virtual entities, that situation represents a bug in the virtual entity feature.

### If I develop a new finance and operations entity and want to see it in Dataverse, do I have to select Refresh entity list in finance and operations? Do I have to do anything in Dataverse?

In theory, no, you don't have to refresh the entity list. At most, you might have to either reset Internet Information Services (IIS) or restart IIS Express, depending on where Application Object Server (AOS) is running. The fact that the list of entities is accurate is cached in SysGlobalObjectCache, which is a per-process cache. Anytime that this cache doesn't indicate that the list is accurate, the list is rebuilt. The rebuild process takes about five seconds. Therefore, when you restart your AOS process (w3wp.exe or iisexpress.exe), the list will be accurate the next time that you query it from Dataverse. Additionally, although recompilation *should* flush the SysGlobalObjectCache cache, it might not. In that case, an AOS restart will flush it.

### Is there guidance on when to use a virtual entity and when to use dual-write?

Guidance on when to use a virtual entity and when to use dual-write is covered in [Integration between finance and operations apps and third-party services](../data-entities/integration-overview.md).

### When adding records using virtual entities is there any way to use number sequences?
Yes, if the finance and operations entity can auto generate number sequences, then it will work the same way from the virtual entity.

### Why does 'search view' not work in Power Apps?
If there are no fields added in the quick find view for the entity, then the search box does nothing. The workaround is to add one or more fields of the entity to the quick find view.

### The virtual entity performance is slow when a virtual entity has relationships to other entities. Is there guidance on how to avoid these issues?
There could be several reasons why performance is slow when a virtual entity has relationships to other entities. This section will be updated as new patterns are identified. The following  is  currently known patterns, which can be used as guidance.

When virtual entities have relationships to other entities, the virtual entity framework needs to query the related entities if the field select list includes the foreign key values for the related entities. By default, queries against the entities return all fields unless the caller requests a specific set of fields. The best practice is to specify a narrow select list. This can help to prevent slow performance.

An example of this issue is explained in [Optimize Dataverse virtual table queries](../../../human-resources/hr-developer-optimize-virtual-table-queries.md).

### Can I configure virtual entities to connect other Power Platform environments to the finance and operations environment even if the Power Platform integration is enabled?

While some features of the Microsoft Power Platform integration, like the [synchronization of business events and data events with Dataverse](../business-events/business-events-flow.md), will only work between the finance and operations apps and Power Platform environments linked through the Microsoft Power Platform integration, it is still possible to manually configure virtual entities between multiple Power Platform environments and the finance and operations environment. 

When the Microsoft Power Platform integration is enabled, the finance and operations environment is linked to a single Power Platform environment. This becomes a one-to-one environment relationship for the integration. When this is enabled, the virtual entities are automatically configured between the two environments. This means that the manual virtual entity configuration defined in the [Configure Dataverse virtual entities](admin-reference.md) documentation is not required. If any manual virtual entity configuration was done prior to enabling the Microsoft Power Platform integration between the two environments, the manual configuration will be ignored after enabling the integration, and the automatic configuration will be used to connect the two environments.

Although the automatic virtual entity configuration will be used for the Power Platform environment linked to the finance and operations environment through the Microsoft Power Platform integration, virtual entities can be manually configured in additional Power Platform environments to enable virtual entities for the finance and operations environment with more than one Power Platform environment.

### Can I use Dataverse virtual entities as a data source with the Data Integrator?

No. Virtual entities are not supported as a source for data integration with the [Data Integrator](/power-platform/admin/data-integrator). Technical limitations prevent the Data Integrator from getting the deltas in the source data to push data to the destination environment.

### I'm getting an error that paging is not supported. How do I work around this?

When running a query against a virtual entity you may get an error response with the message, "Paging is not supported for queries with temporary tables." This is by design. The error will be returned if the query includes any temporary tables. If this error is returned, you will need to determine which temporary tables are included in the query, and then modify the query to exclude the temporary table.
Disabled configuration keys may also cause this error. The default virtual entities provided in the Dynamics 365 ERP Virtual Entities solution do not include temporary tables when all configurations are enabled. However, when a configuration key is not enabled for the backing table of an entity, the physical table is replaced with a temporary table so the system doesn't need to be recompiled for schema changes. This results in a temporary table included in the virtual entity query. In these scenarios the solution is to enable the associated configuration key to resolve the error.

For additional information about the impact of configuration keys on data entities, see [Configuration keys and data entities](../data-entities/config-key-entities.md).

### I'm getting an error that the call was rejected by finance and operations apps as not authorized. How do I work around this?

When running a query against a virtual entity you may get an error response with the message, "A token was obtained to call Finance and Operations, but the call was rejected by Finance and Operations as not authorized. Verify that the Microsoft Entra application value is specified in the Microsoft Entra application for in Finance and Operations, and that the associated user account has privileges to call the CDSVirtualEntity web service."

This error can be the result of the default integration applications being removed from the environment. Verify that the two following applications are listed in the **Microsoft Entra applications** page in the finance and operations apps environment. These applications are added to the environment by default. Dataverse virtual entities for finance and operations apps are unable to gain authorization to the finance and operations environment if these applications are removed from the list.

| Client ID | Name | User ID |
| --------- | ---- | ------- |
| 61a0518c-121a-421a-9ad6-f0955a88be43 | PowerPlatformApplication | PowerPlatformApp |
| f1752846-f0df-4766-96f5-c109adf67d7f | PowerPlatRuntimeApp | PowerPlatformApp |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]