---
# required metadata

title: Power Portal reference
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
ms.search.validFrom: 2020-05-31
ms.dyn365.ops.version: 10.0.12
---

# Power Portal reference

[!include[banner](../includes/banner.md)]

Anonymous access
----------------

Collaboration scenarios in business processes like bidding or onboarding prospects in Finance and Operations will require external users to participate from the Power Portal without having to be a user in Finance and Operations. Anonymous access is appealing to scenarios like the above where the simplicity is all about not having the user log in at all since, they may not be users in Finance and Operations. However, such users are expected to perform CRUD operations in Finance and Operations to perform any meaningful tasks in the
business process.

To ensure only entities that are required for such anonymous access are enabled for anonymous access, in Finance and Operations, a user must be designated to be used for such anonymous access. This is configured in **System administration \> System parameters \> Virtual entity \> Anonymous portal access user ID**. This user can then be assigned to a duties and a security roles to control access to
specific data that must be made available to all users that will be interacting anonymously from the Power Portal. It must be noted that, since this is an anonymous access scenario, the only user context that matters from a security perspective is the designated user in the anonymous portal access user ID setting.

Authenticated access
--------------------

Fully-authenticated user access from the Power Portal to Finance and Operations allows for users in Finance and Operations to also interact from Power Portal. The user signing into the Portal is also a known user in Finance and Operations with appropriate security role(s). The existing roles from the business process in Finance and Operations will govern the security access for such authenticated
users in Power Portal. Since, Power Portal authentication is tied to contacts entity in Common Data Service, there must be a mapping established between the Common Data Service contact and the corresponding user in Finance and Operations. This mapping can be done by adding entries to the msdyn_externalportalusermapping entity. Virtual entities that are made available to authenticated users must be configured as Global scope from a security perspective in the Portal.

When authenticated users from a different tenant must be added as users to Finance and Operations, the [existing new user
process](../sysadmin/tasks/create-new-users.md) in Finance and Operations to add cross tenant users as AAD B2B guest users must be followed.
