---
# required metadata

title: Authentication and authorization
description: This topic describes the authentication and authorization models for user synchronization and permissions between Dynamics 365 Finance and Operations apps and Power Platform. 
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

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

Dynamics 365 Finance and Operations apps and Microsoft Power Platform maintain separate user security. Users must have appropriate permissions in each environment to access Finance and Operations apps resources through Power Platform. User setup can be simplified by synchronizing users between the two environments.

## User provisioning

### Creating Finance and Operations users in Power Platform

There are three ways to automate creating Finance and Operations apps users in the Power Platform environment.

- The first method occurs when a linked environment is initially created. When a new Power Platform environment is created as a linked environment to a Finance and Operations environment, all active users created in the Microsoft 365 admin center who are assigned the **Dynamics 365 Finance** license are automatically added as users in the new Power Platform environment. For more information on creating linked environments, see [Enabling the Microsoft Power Platform integration](./enable-power-platform-integration.md).
- The second method occurs when a new user is added in the Microsoft 365 admin center. When a new user is created and assigned the **Dynamics 365 Finance** license, the new user is automatically created as a user in Power Platform environments that are linked to a Finance and Operations environment. The process of creating the new user in Power Platform can take up to an hour.
- If a user assigned the **Dynamics 365 Finance** license signs into the Power Platform environment before the user synchronization, the user record is created when the Power Platform environment is first accessed.

Although there are methods to automate creating Finance and Operations apps users in linked Power Platform environments, you can add Finance and Operations apps users directly in Power Platform. To do this, complete the steps outlined in the topic, [Add users to an environment that has a Dataverse database](/power-platform/admin/add-users-to-environment#add-users-to-an-environment-that-has-a-dataverse-database).

### Creating Power Platform users in Finance and Operations apps

Administrators can manually import Power Platform users into Finance and Operations apps from Azure Active Directory. To do this, select **Import users** in Finance and Operations apps. For more information, see [Import new users from Azure AD](../sysadmin/tasks/create-new-users.md#import-new-users-from-azure-ad).

## Security model

Power Platform users working in Dataverse can interact with Finance and Operations apps entities through virtual entities and receive business events triggered by user actions in Finance and Operations apps. To interact with virtual entities in Dataverse, the user access to the virtual entity metadata. When a transaction is performed in Dataverse, a virtual entity call is made to the Finance and Operations apps where it authorizes the user's request, validating against the user's security role and privileges defined in Finance and Operations apps.

For more information on the Dataverse virtual entity interaction and the security model with Finance and Operations apps, see the [Architecture](virtual-entities-overview.md#Architecture) section of the virtual entities overview documentation.

### Security roles in Power Platform

When users with the **Dynamics 365 Finance** license are automatically created as users in Power Platform, the Power Platform user is automatically assigned both the **Finance and Operations Basic User** and **Environment Maker** security roles.

- The **Finance and Operations Basic User** security role allows the user to access and update virtual entities and business events. When a virtual entity or business event is activated in the Dataverse environment, the virtual entity or business event privileges are automatically granted to the security role.
- The **Environment Maker** security role allows the user to create Power Apps and flows in Power Automate.

For information on manually assigning security roles to Power Platform users in the Power Platform admin center, see [Assign a security role to a user](/power-platform/admin/assign-security-roles).

### Security roles in Finance and Operations apps

The security roles assigned to a user in Finance and Operations apps depend on the system access the user requires to perform their assigned duties and responsibilities. The security roles in Finance and Operations apps determine the application data to which the user has access. A user can't access data through the Power Platform integration if the user's assigned security roles in Finance and Operations apps don't grant permissions to the data.

The security role for Finance and Operations apps must be added manually by the system administrator. Different security roles can be assigned to the user in Finance and Operations apps.
