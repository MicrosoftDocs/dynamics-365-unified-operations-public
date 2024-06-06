---
title: Power Apps portals with finance and operations
description: Learn about how Power Apps portals can be used with finance and operations, including an overview on ananymous access from Power Apps portals.
author: Sunil-Garg
ms.author: sunilg
ms.topic: article
ms.date: 07/13/2020
ms.custom: NotInToc
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-05-31
ms.search.form:
ms.dyn365.ops.version: 10.0.12
---

# Power Apps portals with finance and operations

[!include[banner](../includes/banner.md)]



> [!IMPORTANT]
> This functionality requires version 10.0.12 for finance and operations apps, while service update 189 is required for Dataverse. The release information for Dataverse is published on the [latest version availability page](/business-applications-release-notes/dynamics/released-versions/dynamics-365ce#all-version-availability).

Power Apps portals will enable create, update, and delete (CRUD) operations to finance and operations entities that are available as virtual entities in Dataverse. This article explains the scenarios that are implemented in Power Apps portals for finance and operations apps.

## Anonymous access from Power Apps portals

Collaboration scenarios in business processes such as bidding or onboarding of prospects in finance and operations require that external users participate from the Power Apps portal, even though they aren't users in finance and operations apps. The simplicity of anonymous access is appealing in these types of scenarios because the users, who might not be finance and operations apps users, don't have to sign in. However, they are expected to perform CRUD operations in finance and operations to complete any meaningful tasks in the business processes.

To ensure that only the required entities are enabled for anonymous access, a user in finance and operations must be designated as the user who is used for anonymous access. This designation is configured in the **Anonymous portal access user ID** field on the **Virtual entity** tab on the **System parameters** page (**System administration \> System parameters**). The designated user can then be assigned to duties and security roles to control access to specific data that must be made available to all users who will interact anonymously from the Power Portal.

Note that because this scenario involves anonymous access, the only user context that matters, from a security perspective, is the user who is designated in the **Anonymous portal access user ID** field.

## Authenticated access from Power Apps portals

Fully authenticated user access from Power Apps portals to finance and operations lets users in finance and operations also interact from Power Apps portals. A user who signs in to the Power Apps portal is also a known user in finance and operations who has appropriate security roles based on job requirements. These roles govern the security access to data for the authenticated user in Power Portal. In addition, any finance and operations user that is expected to also use Power Apps portal to access finance and operations data must also belong to the **CDSVirtualEntityAuthenticatedPortalUser** security role. This provides an additional layer of security and also provides a way to know the total users that are authorized to access from Power Apps portals. 

Because Power Apps portals authentication is linked to the Contacts entity in Dataverse, a mapping must be established between the Dataverse contact and the corresponding user in finance and operations. This mapping can be done by adding entries to the **msdyn\_externalportalusermapping** entity. From a security perspective, the scope of virtual entities that are made available to authenticated users must be configured as **Global** in the Power Apps portal.

When authenticated users from a different tenant need to be added to finance and operations as users, you must use the [Create new user](../sysadmin/tasks/create-new-users.md) process in finance and operations. This process adds cross-tenant users as Microsoft Microsoft Entra business-to-business (B2B) guest users.

> [!NOTE]
> Access from the Power Apps Portal will fail if the user (authenticated or anonynous) has been assigned the System administrator role in any finance and operations apps.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]