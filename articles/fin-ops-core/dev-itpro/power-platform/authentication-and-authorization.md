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

### Creating Finance and Operations Users in Power Platform

There are three methods in which creating Finance and Operations users in the Power Platform environment can be automated:

1. The first method occurs during initial creation of a linked environment. When a new Power Platform environment is created as a linked environment to a Finance and Operations environment, all active users created in the Microsoft 365 admin center who are assigned the **Dynamics 365 Finance** license are automatically added as users in the new Power Platform environment. See [Enabling the Microsoft Power Platform integration](./enable-power-platform-integration.md) for more information on creating linked environments. 
2. The second method occurs when a new user is added in the Microsoft 365 admin center. When a new user is created and assigned the **Dynamics 365 Finance** license, the new user is automatically created as a user in Power Platform environments linked to a Finance and Operations environment. It can take up to an hour for the new user to be created in Power Platform. 
3. If a user who is assigned the **Dynamics 365 Finance** license signs into the Power Platform environment prior to the user synchronization, then the user record is created when first accessing the Power Platform environment.

Although there are methods to automate the creation of Finance and Operations users in linked Power Platform environments, you still have the option to add Finance and Operations users directly in Power Platform. This can be done by following the steps outlined in the [Add users to an environment that has a Dataverse database](https://docs.microsoft.com/power-platform/admin/add-users-to-environment#add-users-to-an-environment-that-has-a-dataverse-database) topic of the Power Platform documentation.

### Creating Power Platform users in Finance and Operations

Administrators can manually import Power Platform users into Finance and Operations from Azure Active Directory. This can be done with the **Import users** action in Finance and Operations. See [Import new users from Azure AD](../sysadmin/tasks/create-new-users#import-new-users-from-azure-ad) for more information.
