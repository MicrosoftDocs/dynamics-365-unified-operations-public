---
title: Virtual entities overview
description: Learn about virtual entities for finance and operations apps, including an overview on architectures for finance and operations apps.
author: RamaKrishnamoorthy
ms.author: johnmichalak
ms.topic: overview
ms.date: 01/21/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-05-31
---

# Virtual entities overview

[!include[banner](../includes/banner.md)]

> [!IMPORTANT]
> This functionality requires version 10.0.12 of finance and operations apps, and service update 189 of Microsoft Dataverse. The release information for Dataverse is published on the [latest version availability page](/business-applications-release-notes/dynamics/released-versions/dynamics-365ce#all-version-availability).

## Virtual entities for finance and operations apps

Finance and operations apps act as a virtual data source in Dataverse. They enable full create, read, update, and delete (CRUD) operations from Dataverse and Microsoft Power Platform. By definition, the data for virtual entities doesn't reside in Dataverse. Instead, it continues to reside in the app where it belongs. Before you can perform CRUD operations on finance and operations entities from Dataverse, you must make the entities available as virtual entities in Dataverse. After you make the entities available, you can perform CRUD operations from Dataverse and Microsoft Power Platform on data that resides in finance and operations apps.

All Open Data Protocol (OData) entities in finance and operations apps are available as virtual entities in Dataverse, and therefore also in Microsoft Power Platform. Makers can now use data directly from finance and operations apps to build experiences in customer engagement apps. These experiences offer full CRUD capability and don't require copying to Dataverse. You can use Power Apps portals to build external-facing websites that enable collaboration scenarios for business processes in finance and operations apps.

## Architecture

Virtual entities are a Dataverse concept that is useful beyond finance and operations apps. The following illustration shows how the finance and operations provider for virtual entities is implemented. The provider implements six primary methods. The first five methods are the standard CRUD operations: **Create**, **Update**, **Delete**, **Retrieve**, and **RetrieveMultiple**. The last method, **PerformAction**, is used to call OData actions, as described later in this article. Calls to the finance and operations virtual entity data provider (shown as "virtual entities plug-in" in the illustration) causes a Secure Sockets Layer (SSL)/Transport Layer Security (TLS) 1.2 secure web call to the CDSVirtualEntityService web API endpoint of finance and operations apps. This web service then converts the queries into calls to the associated physical entities in finance and operations apps, and invokes CRUD or OData operations on those entities. Because a finance and operations entity is directly invoked in all operations, any business logic on the entity or its backing tables is also invoked.

:::image type="content" source="media/image1.png" alt-text="Screenshot of Architecture of virtual entities for finance and operations apps.":::

During calls, two points of translation convert Dataverse to finance and operations apps. The first point of translation occurs in the VE Plugin, which translates concepts such as entity physical names into finance and operations entity names. It also converts some well-known concepts, such as Company references. The web service call still uses the EntityCollection, Entity, and QueryExpression objects to express the operations that are performed, by using the translated entity names and concepts from the VE Plugin. Finally, the CDSVirtualEntityAdapterService web API in finance and operations apps completes the translation from QueryExpression to QueryBuildDataSource and other internal finance and operations language constructs.

All calls between Dataverse and finance and operations apps as part of virtual entities are service-to-service (S2S) calls. They use the Microsoft Entra application that you specify in the configuration. The user of this application should have access **only** to the CDSVirtualEntityAdapterService web API and the catalog entity, CDSVirtualEntityListEntity. These privileges are included in the out-of-box security role that is named CDSVirtualEntityApplication. During the S2S calls, Dataverse provides the identity of the user in Dataverse who is invoking the action. The CDSVirtualEntityAdapterService web API looks up the associated user in finance and operations apps and runs the query in the context of that user. Therefore, the S2S call doesn't need explicit access to all the finance and operations entities. Instead, it can rely on the privileges of the user who is invoking the action to determine data access.

> [!NOTE]
> For optimal latency in virtual entity calls, always use finance and operations apps and Dataverse that are co-located in the same Azure region. When finance and operations apps and Dataverse are co-located, the virtual entity overhead is expected to be less than 30 milliseconds (ms) per call.

Power Apps Portal can also access virtual entities. Because Power Apps Portal authorization is based on contact records, a mapping between contact records and finance and operations users is maintained in the dyn\_externalportalusermapping table in Dataverse. Only highly privileged users in Dataverse who have the rights to control the security access that portal users have to finance and operations virtual entities should be able to edit this table. Any finance and operations user who is set up for Power Apps portal access must have the CDSVirtualEntityAuthorizedPortalUser security role assigned, and can't have the system administrator or security administrator role assigned. Regardless of the Power Apps portal security setting that is applied to virtual entities, the resulting query to finance and operations apps always runs as the associated finance and operations user, and is subject to that user's entity and row security settings. Anonymous portal access is also supported. For information about this type of access and how it can be done, see [Power Apps Portal reference](power-portal-reference.md).

## Authorization
Because finance and operations apps and Microsoft Power Platform maintain separate user security, it's important to use the appropriate user context with the correct permissions when operating over a virtual entity record in Dataverse. For more information, see [Authentication and authorization](authentication-and-authorization.md).

This separation means that when you create an organization context in a Dataverse plugin that reads a finance and operations virtual entity, you associate the organization context with the appropriate application or end user that has permissions to the virtual entity in finance and operations. The Dataverse SYSTEM user doesn't have access to all entities in finance and operations, nor do the out of the box service-to-service applications. Failure to use a proper user or app-user context might result in errors with messages like `Unable to determine the user in CDS`.
