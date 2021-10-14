---
# required metadata

title: Finance and Operations and Dataverse admin reference
description: This topic covers set up and configuration of virtual entities for Finance and Operations.
author: Sunil-Garg
ms.date: 07/13/2020
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: sunilg
ms.search.validFrom: 2020-05-31
ms.dyn365.ops.version: 10.0.12
---

# Configure Dataverse virtual entities

[!include[banner](../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic provides step-by-step guidance for configuring virtual entities for Finance and Operations apps in Dataverse. 

> [!NOTE]
> The configuration steps outlined in this topic are required only for Finance and Operations environments that are not linked to a Power Platform environment. For Finance and Operations environments that are linked to a Power Platform environment, the virtual entity configuration outlined in this topic is done automatically as part of the linking process. These steps are required to enable virtual entities only for Finance and Operations environments that are not linked to a Power Platform environment. See [Enabling the Microsoft Power Platform integration](enable-power-platform-integration.md) for information on linking Finance and Operations to a Power Platform environment.

## Getting the virtual entity solution
The Dataverse solution for Finance and Operations virtual entities must be installed from Microsoft AppSource virtual entity solution. For more information, see [Finance and Operations virtual entity](https://appsource.microsoft.com/product/dynamics-crm/mscrm.finance_and_operations_virtual_entity).

Ensure the following solutions are installed in Dataverse.

- **Dynamics365Company** - This adds the **Company** entity, which is referenced by all Finance and Operations entities with a PrimaryCompanyContext metadata value.

- **MicrosoftOperationsVESupport** - This provides the core support for the Finance and Operations virtual entity feature.

- **MicrosoftOperationsERPCatalog** - This provides a list of available Finance and Operations entities through the mserp_financeandoperationsentity virtual entity.

- **MicrosoftOperationsERPVE** - This is the API-managed solution, which will contain the generated virtual entities as they are made visible.

When updates are available for the virtual entity solution, they can be manually applied in the Power Platform admin center. See [Manage Dynamics 365 apps] in the Power Platform documentation for more information on manually installing and updating the virtual entity solution. For Finance and Operations environments that are linked to a Power Platform environment, available updates to the virtual entity solution are applied automatically.

## Authentication and authorization

After the solutions are imported in the Dataverse environment, both environments must be set up to connect to each other. Dataverse will call Finance and Operations using Service-to-Service (S2S) authentication, based on an Azure Active Directory (AAD) application. This new AAD application represents the single instance of the Dataverse environment. If you have multiple pairs of Dataverse and Finance and Operations environments, separate AAD applications for each pair must be created to ensure connections are established between the correct pair of Finance and Operations and Power Platform environments. 

### Register the app in the Microsoft Azure portal

The following procedure shows the creation of the AAD application.

> [!IMPORTANT]
> The AAD application must be created on the same tenant as Finance and Operations.

1.  Go to <https://portal.azure.com> **\> Azure Active Directory \> App registrations**.

2.  Select **New Registration**. Enter the following information:

    - **Name** - Enter a unique name.

    - **Account type** - Enter **Any Azure AD directory** (single or multi-tenant).

    - **Redirect URI** - Leave blank.

    - Select **Register**.

    - Make note of the **Application (client) ID** value. You will need it later.

3.  Create a symmetric key for the application.

    - Select **Certificates & secrets** in the newly created application.

    - Select **New client secret**.

    - Provide a description and an expiration date.

    - Select **Save**. A key will be created and displayed. Copy this value for later use.

### Grant app permissions in Finance and Operations

The AAD application created above will be used by Dataverse to call Finance and Operations apps. As such, it must be trusted by Finance and Operations and associated with a user account with the appropriate rights in Finance and Operations. A special service user must be created in Finance and Operations with rights *only* to the virtual entity functionality, and no other rights. After completing this step, any application with the secret of the AAD application create above will be able to call this Finance and Operations environment and access the virtual entity functionality.

1.  In Finance and Operations, go to **System Administration \> Users \> Users**.

2.  Select **New** to add a new user. Enter the following information:

    - **User ID** - Enter **dataverseintegration** (or a different value).

    - **User name** - Enter **dataverse integration** (or a different value).

    - **Provider** - Set to **NonAAD**.

    - **Email** - Enter **dataverseintegration** (or a different value, does *not* need to be a valid email account).

    - Assign the security role **CDS virtual entity application** to this user.

    - Remove all other roles including **System user**.

3.  Go to **System Administration \> Setup \> Azure Active Directory applications** to register Dataverse. 

    - Add a new row.

    - **Client ID** - The **Application (client) ID** created above

    - **Name** - Enter **Dataverse Integration** (or a different name).

    - **User ID** - The user ID created above.

## Configure the virtual entity data source

The next step in the process is to provide Dataverse with the Finance and Operations instance to connect to. The following steps walk through this part of the process.

1.  In Dataverse, go to **Advanced Settings \> Administration \> Virtual Entity Data Sources**.

2.  Select the data source named “Finance and Operations”.

3.  Fill in the information from the steps above.

    - **Target URL** - The URL at which you can access Finance and Operations.

    - **OAuth URL** - https://login.windows.net/

    - **Tenant ID** - Your tenant, such as “contoso.com”.

    - **AAD Application ID** - The **Application (client) ID** created above.

    - **AAD Application Secret** - The secret generated above.

    - **AAD Resource** - Enter 00000015-0000-0000-c000-000000000000 (this is the AAD application representing Finance and Operations, and should always be this same value).

4.  Save the changes.

When the virtual entity configuration is completed, you can then enable the virtual entities in Dataverse. See [Enable Dataverse virtual entities](enable-virtual-entities.md) for more information.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
