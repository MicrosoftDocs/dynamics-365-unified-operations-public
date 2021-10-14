---
# required metadata

title: Authentication and authorization
description: This topic describes the authentication and authorization models for user sync and permissions between Finance and Operations apps and Power Platform. 
author: jaredha
ms.date: 10/14/2021
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

Finance and Operations and Power Platform maintain separate user security, and users must have appropriate permissions in each to access Finance and Operations resources through Power Platform. User setup can be simplified by synchronizing users between the two environments.

## User provisioning

### Creating Finance and Operations users in Power Platform

There are three methods in which creating Finance and Operations users in the Power Platform environment can be automated:

1. The first method occurs during initial creation of a linked environment. When a new Power Platform environment is created as a linked environment to a Finance and Operations environment, all active users created in the Microsoft 365 admin center who are assigned the **Dynamics 365 Finance** license are automatically added as users in the new Power Platform environment. See [Enabling the Microsoft Power Platform integration](./enable-power-platform-integration.md) for more information on creating linked environments. 
2. The second method occurs when a new user is added in the Microsoft 365 admin center. When a new user is created and assigned the **Dynamics 365 Finance** license, the new user is automatically created as a user in Power Platform environments linked to a Finance and Operations environment. It can take up to an hour for the new user to be created in Power Platform. 
3. If a user who is assigned the **Dynamics 365 Finance** license signs into the Power Platform environment prior to the user synchronization, then the user record is created when first accessing the Power Platform environment.

Although there are methods to automate the creation of Finance and Operations users in linked Power Platform environments, you still have the option to add Finance and Operations users directly in Power Platform. This can be done by following the steps outlined in the [Add users to an environment that has a Dataverse database](https://docs.microsoft.com/power-platform/admin/add-users-to-environment#add-users-to-an-environment-that-has-a-dataverse-database) topic of the Power Platform documentation.

### Creating Power Platform users in Finance and Operations

Administrators can manually import Power Platform users into Finance and Operations from Azure Active Directory. This can be done with the **Import users** action in Finance and Operations. See [Import new users from Azure AD](../sysadmin/tasks/create-new-users#import-new-users-from-azure-ad) for more information.

## Security model

Power Platform users working in Dataverse can interact with Finance and Operations entities through virtual entities and receive business events triggered by user actions in Finance and Operations. To interact with virtual entities in Dataverse, the user must have privileges to the virtual entity metadata. When a transaction is performed in Dataverse, a virtual entity call is made to Finance and Operations where it authorizes the user's request, validating against the user's security role and privileges defined in Finance and Operations.

For more information on the Dataverse virtual entity interaction and security model with Finance and Operations, see the [Architecture](./virtual-entities-overview) section of the virtual entities overview documentation.

### Security roles in Power Platform

When users with the **Dynamics 365 Finance** license are automatically created as users in Power Platform, the Power Platform user is automatically assigned both the **Finance and Operations Basic User** and **Environment Maker** security roles.

- The **Finance and Operations Basic User** security role allows the user to access and update virtual entities and business events. Whenever a virtual entity or business event is activated in the Dataverse environment the virtual entity or business event privileges are automatically granted to the security role.
- The **Environment Maker** security role allows the user to create Power Apps and flows in Power Automate. 

For information on manually assigning security roles to Power Platform users in the Power Platform admin center, see [Assign a security role to a user](https://docs.microsoft.com/power-platform/admin/assign-security-roles).

### Security roles in Finance and Operations

The security roles assigned to a user in Finance and Operations will depend on the system access the user requires to perform his or her assigned duties and responsibilities. The security roles in Finance and Operations will determine the application data to which the user has access. A user will not be able to access data through the Power Platform integration if the user's assigned security roles in Finance and Operations do not grant permissions to the data.

The security role for Finance and Operatins must be added manually by the system administrator. Different security roles can be assigned to the user in Finance and 


