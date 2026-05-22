---
title: Authentication and authorization
description: Learn about the authentication and authorization models for user synchronization and permissions between finance and operations apps and Microsoft Power Platform. 
author: jaredha
ms.author: johnmichalak
ms.topic: article
ms.date: 01/21/2026
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-10-14
ms.search.form:
ms.dyn365.ops.version: 10.0.0
---
# Authentication and authorization

[!include[banner](../includes/banner.md)]

Finance and operations apps and Microsoft Power Platform maintain separate user security. Users must have appropriate permissions in each environment to access finance and operations apps resources through Microsoft Power Platform. You can simplify user setup by synchronizing users between the two environments.

## User provisioning

### Creating finance and operations apps users in Microsoft Power Platform

Automate the creation of finance and operations apps users in the Microsoft Power Platform environment in three ways:

- When you create a new Microsoft Power Platform environment as a linked environment that links to a finance and operations apps environment, all active users that you create in the Microsoft 365 admin center and assign the **Dynamics 365 Finance** license to are automatically added as users in the new Microsoft Power Platform environment. For more information about how to create linked environments, see [Enable the Microsoft Power Platform integration](./enable-power-platform-integration.md).
- When you create a new user in the Microsoft 365 admin center and assign the **Dynamics 365 Finance** license, you automatically create the new user as a user in Microsoft Power Platform environments that are linked to a finance and operations apps environment. The process of creating the new user in Microsoft Power Platform can take up to an hour.
- If a user that you assign the **Dynamics 365 Finance** license to signs in to the Microsoft Power Platform environment before user synchronization occurs, the user record is created when the Microsoft Power Platform environment is first accessed.

You can automate the creation of finance and operations apps users in linked Microsoft Power Platform environments. However, you can also add finance and operations apps users directly in Microsoft Power Platform by following the steps in [Add users to an environment that has a Dataverse database](/power-platform/admin/add-users-to-environment#add-users-to-an-environment-that-has-a-dataverse-database).

### Creating Microsoft Power Platform users in finance and operations apps

Administrators can manually import Microsoft Power Platform users into finance and operations apps from Microsoft Entra ID. To import users from Microsoft Entra ID, select **Import users** in finance and operations apps. For more information, see [Import new users from Microsoft Entra ID](../sysadmin/tasks/create-new-users.md#import-new-users-from-azure-ad).

## Security model

Microsoft Power Platform users who work in Dataverse can interact with finance and operations apps entities through virtual entities. They can also receive business events that user actions in finance and operations apps trigger. To interact with virtual entities in Dataverse, a user requires access to the virtual entity metadata. When a transaction is performed in Dataverse, a virtual entity call is made to finance and operations apps. There, the call authorizes the user's request by validating against the user's security role and privileges that are defined in finance and operations apps.

For more information about Dataverse virtual entity interaction and the finance and operations apps security model, see [Architecture](virtual-entities-overview.md#architecture).

### Security roles in Microsoft Power Platform

When users with the **Dynamics 365 Finance** license are automatically created as users in Microsoft Power Platform, the **finance and operations Basic User** security role is automatically assigned to the Microsoft Power Platform users.

- **Finance and operations Basic User** – This security role grants access to and the ability to update virtual entities and business events. When you activate a virtual entity or business event in the Dataverse environment, the virtual entity or business event privileges are automatically granted to the security role.

For information about how to manually assign security roles to Microsoft Power Platform users in the Power Platform admin center, see [Assign a security role to a user](/power-platform/admin/assign-security-roles).

### Security roles in finance and operations apps

The security roles that you assign to a user in finance and operations apps depend on the system access that the user needs to perform their assigned duties and responsibilities. The security roles in finance and operations apps determine the application data that a user can access. A user can't access data through the Microsoft Power Platform integration if the user's assigned security roles in finance and operations apps don't grant permissions to the data.

The system administrator must manually add the security role for finance and operations apps. You can assign different security roles to a user in finance and operations apps.
