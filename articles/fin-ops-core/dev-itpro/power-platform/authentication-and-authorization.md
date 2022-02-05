---
# required metadata

title: Authentication and authorization
description: This topic describes the authentication and authorization models for user synchronization and permissions between Finance and Operations apps and Microsoft Power Platform. 
author: jaredha
ms.date: 10/18/2021
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.search.region: Global
# ms.search.industry:
ms.author: jaredha
ms.search.validFrom: 2021-10-14
ms.dyn365.ops.version: 10.0.0
---
# Authentication and authorization

[!include[banner](../includes/banner.md)]



Finance and Operations apps and Microsoft Power Platform maintain separate user security. Users must have appropriate permissions in each environment to access Finance and Operations apps resources through Microsoft Power Platform. User setup can be simplified by synchronizing users between the two environments.

## User provisioning

### Creating Finance and Operations apps users in Microsoft Power Platform

There are three ways to automate the creation of Finance and Operations apps users in the Microsoft Power Platform environment:

- When a new Microsoft Power Platform environment is created as a linked environment that is linked to a Finance and Operations apps environment, all active users that are created in the Microsoft 365 admin center and that the **Dynamics 365 Finance** license is assigned to are automatically added as users in the new Microsoft Power Platform environment. For more information about how to create linked environments, see [Enable the Microsoft Power Platform integration](./enable-power-platform-integration.md).
- When a new user is created in the Microsoft 365 admin center, and the **Dynamics 365 Finance** license is assigned, the new user is automatically created as a user in Microsoft Power Platform environments that are linked to a Finance and Operations apps environment. The process of creating the new user in Microsoft Power Platform can take up to an hour.
- If a user that the **Dynamics 365 Finance** license is assigned to signs in to the Microsoft Power Platform environment before user synchronization occurs, the user record is created when the Microsoft Power Platform environment is first accessed.

The creation of Finance and Operations apps users in linked Microsoft Power Platform environments can be automated. However, you can also add Finance and Operations apps users directly in Microsoft Power Platform by following the steps in [Add users to an environment that has a Dataverse database](/power-platform/admin/add-users-to-environment#add-users-to-an-environment-that-has-a-dataverse-database).

### Creating Microsoft Power Platform users in Finance and Operations apps

Administrators can manually import Microsoft Power Platform users into Finance and Operations apps from Azure Active Directory (Azure AD). To import users from Azure AD, select **Import users** in Finance and Operations apps. For more information, see [Import new users from Azure AD](../sysadmin/tasks/create-new-users.md#import-new-users-from-azure-ad).

## Security model

Microsoft Power Platform users who work in Dataverse can interact with Finance and Operations apps entities through virtual entities. They can also receive business events that are triggered by user actions in Finance and Operations apps. To interact with virtual entities in Dataverse, a user requires access to the virtual entity metadata. When a transaction is performed in Dataverse, a virtual entity call is made to Finance and Operations apps. There, the call authorizes the user's request by validating against the user's security role and privileges that are defined in Finance and Operations apps.

For more information about Dataverse virtual entity interaction and the Finance and Operations apps security model, see [Architecture](virtual-entities-overview.md#architecture).

### Security roles in Microsoft Power Platform

When users who have the **Dynamics 365 Finance** license are automatically created as users in Microsoft Power Platform, both the **Finance and Operations Basic User** security role and the **Environment Maker** security role are automatically assigned to the Microsoft Power Platform users.

- **Finance and Operations Basic User** – This security role allows the user to access and update virtual entities and business events. When a virtual entity or business event is activated in the Dataverse environment, the virtual entity or business event privileges are automatically granted to the security role.
- **Environment Maker** – This security role allows the user to create apps in Power Apps and flows in Power Automate.

For information about how to manually assign security roles to Microsoft Power Platform users in the Power Platform admin center, see [Assign a security role to a user](/power-platform/admin/assign-security-roles).

### Security roles in Finance and Operations apps

The security roles that are assigned to a user in Finance and Operations apps depend on the system access that the user requires to perform their assigned duties and responsibilities. The security roles in Finance and Operations apps determine the application data that a user has access to. A user can't access data through the Microsoft Power Platform integration if the user's assigned security roles in Finance and Operations apps don't grant permissions to the data.

The security role for Finance and Operations apps must be manually added by the system administrator. Different security roles can be assigned to a user in Finance and Operations apps.
