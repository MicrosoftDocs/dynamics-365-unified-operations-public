---
# required metadata

title: Authentication and authorization
description: This article describes the authentication and authorization models for user synchronization and permissions between finance and operations apps and Microsoft Power Platform. 
author: jaredha
ms.date: 07/26/2022
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.search.region: Global
# ms.search.industry:
ms.author: jaredha
ms.search.validFrom: 2021-10-14
ms.dyn365.ops.version: 10.0.0
---
# Authentication and authorization

[!include[banner](../includes/banner.md)]



Finance and operations apps and Microsoft Power Platform maintain separate user security. Users must have appropriate permissions in each environment to access finance and operations apps resources through Microsoft Power Platform. User setup can be simplified by synchronizing users between the two environments.

## User provisioning

### Creating finance and operations apps users in Microsoft Power Platform

There are three ways to automate the creation of finance and operations apps users in the Microsoft Power Platform environment:

- When a new Microsoft Power Platform environment is created as a linked environment that is linked to a finance and operations apps environment, all active users that are created in the Microsoft 365 admin center and that the **Dynamics 365 Finance** license is assigned to are automatically added as users in the new Microsoft Power Platform environment. For more information about how to create linked environments, see [Enable the Microsoft Power Platform integration](./enable-power-platform-integration.md).
- When a new user is created in the Microsoft 365 admin center, and the **Dynamics 365 Finance** license is assigned, the new user is automatically created as a user in Microsoft Power Platform environments that are linked to a finance and operations apps environment. The process of creating the new user in Microsoft Power Platform can take up to an hour.
- If a user that the **Dynamics 365 Finance** license is assigned to signs in to the Microsoft Power Platform environment before user synchronization occurs, the user record is created when the Microsoft Power Platform environment is first accessed.

The creation of finance and operations apps users in linked Microsoft Power Platform environments can be automated. However, you can also add finance and operations apps users directly in Microsoft Power Platform by following the steps in [Add users to an environment that has a Dataverse database](/power-platform/admin/add-users-to-environment#add-users-to-an-environment-that-has-a-dataverse-database).

### Creating Microsoft Power Platform users in finance and operations apps

Administrators can manually import Microsoft Power Platform users into finance and operations apps from Azure Active Directory (Azure AD). To import users from Azure AD, select **Import users** in finance and operations apps. For more information, see [Import new users from Azure AD](../sysadmin/tasks/create-new-users.md#import-new-users-from-azure-ad).

## Security model

Microsoft Power Platform users who work in Dataverse can interact with finance and operations apps entities through virtual entities. They can also receive business events that are triggered by user actions in finance and operations apps. To interact with virtual entities in Dataverse, a user requires access to the virtual entity metadata. When a transaction is performed in Dataverse, a virtual entity call is made to finance and operations apps. There, the call authorizes the user's request by validating against the user's security role and privileges that are defined in finance and operations apps.

For more information about Dataverse virtual entity interaction and the finance and operations apps security model, see [Architecture](virtual-entities-overview.md#architecture).

### Security roles in Microsoft Power Platform

When users who have the **Dynamics 365 Finance** license are automatically created as users in Microsoft Power Platform, the **finance and operations Basic User** security role is automatically assigned to the Microsoft Power Platform users.

- **Finance and operations Basic User** – This security role allows the user to access and update virtual entities and business events. When a virtual entity or business event is activated in the Dataverse environment, the virtual entity or business event privileges are automatically granted to the security role.

For information about how to manually assign security roles to Microsoft Power Platform users in the Power Platform admin center, see [Assign a security role to a user](/power-platform/admin/assign-security-roles).

### Security roles in finance and operations apps

The security roles that are assigned to a user in finance and operations apps depend on the system access that the user requires to perform their assigned duties and responsibilities. The security roles in finance and operations apps determine the application data that a user has access to. A user can't access data through the Microsoft Power Platform integration if the user's assigned security roles in finance and operations apps don't grant permissions to the data.

The security role for finance and operations apps must be manually added by the system administrator. Different security roles can be assigned to a user in finance and operations apps.

