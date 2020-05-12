---
# required metadata

title: Admin reference
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

# Admin reference

[!include[banner](../includes/banner.md)]

How to set up virtual entities for Finance and Operations
---------------------------------------------------------

## Getting the solution

## Authentication & Authorization

After the solutions are imported in the CDS environment, both environments must be set up to connect to each other. CDS will call Finance and Operations using Service-to-Service (S2S) authentication, based upon an Azure Active Directory (AAD) application. This new AAD application represents the single instance of the CDS environment. If you have multiple pairs of CDS and Finance and Operations environments, separate AAD applications for each pair must be created to ensure connections are established between the correct pair of F&O and CDS environments. The below procedure shows the creation of the AAD application.

1.  Navigate to <https://portal.azure.com> \> Azure Active Directory \> App registrations

2.  Click New Registration

    1.  Name = \<unique name\>

    2.  Account type = “Any Azure AD directory” (single or multi-tenant)

    3.  Redirect URI = (Leave blank)

    4.  Click register

    5.  Make note of the “Application (client) ID” value, you will need it later.

3.  Create a symmetric key for the application

    1.  Click Certificates & secrets in the newly created application

    2.  Click New client secret

    3.  Provide a description and an expiration date

    4.  Click Save. A key will be created and displayed. Copy this value for later use.

The AAD application created above will be used by CDS to call Finance and Operations. As such, it must be trusted by F&O and associated with a user account with the appropriate rights in F&O. A special service user must be created in Finance and Operations with rights *only* to the virtual entity functionality, and no other rights. After completing this step, any application with the secret of the AAD application create above, will be able to call this Finance and Operations environment and access the Virtual Entity functionality.
The next steps walks through this process in F&O.

1.  In Finance and Operations, navigate to System Administration \> Users \> Users

2.  Select “New” to add a new user

    1.  User ID = “cdsintegration” (or a different value)

    2.  User name = “cds integration” (or a different value)

    3.  Provider = (leave at its default value)

    4.  Email = “cdsintegration” (or a different value, does *not* need to be a valid email account)

    5.  Assign the security role “CDS virtual entity application” to this user

    6.  Remove all other roles including “System user”

3.  Navigate to System Administration \> Setup \> Azure Active Directory applications to register CDS

    1.  Add a new row

    2.  Client ID = The “Application (client) ID” created above

    3.  Name = “CDS Integration” (or a different name)

    4.  User ID = The user ID created above

The next step in the process is to tell CDS, which F&O instance to connect to. The following steps walks through this part of the process.

1.  In CDS, navigate to Advanced Settings \> Administration \> Virtual Entity Data Sources

2.  Select the data source named “Finance and Operations”

3.  Fill in the information from the steps above

    1.  Target URL = (The URL at which you can access Finance and Operations)

    2.  OAuth URL = https://login.windows.net/

    3.  Tenant ID = (Your tenant, such as “contoso.com”)

    4.  AAD Application ID = The “Application (client) ID” created above

    5.  AAD Application Secret = The secret generated above

    6.  AAD Resource = 00000015-0000-0000-c000-000000000000 (this is the AAD application representing Finance and Operations, and should always be this same value)

    7.  Save the changes

## Enabling virtual entities

Due to the large number of OData enabled entities available in Finance and Operations, by default, the entities are not available as virtual entities in CDS. The steps outlines below allows for enabling entities to be virtual as needed.

1. In CDS, go to advanced find

2. Look for “Available Finance and Operations Entities” and click results

![Catalog](../media/fovecatalog.png)

3. Locate and open the entity you wish to enable

4. Set visible = Yes and save. This will generate the virtual entity and cause it to appear in all appropriate menus such as the advanced find dialog.

![Enable VE](../media/foveenable.png)

## Refreshing virtual entity metadata

The virtual entity metadata can be force-refreshed when it is expected for the entity metadata in F&O to have changed. This can be done by selecting Refresh = Yes and saving. This will sync the latest entity definition from Finance and Operations to CDS and update the virtual entity.

Referencing Virtual Entities
----------------------------

The Virtual Entities are all generated in the MicrosoftOperationsERPVE solution which is "API Managed". That means the items in the solution change as you make entities visible/hidden, but it is still a "managed" solution that you can take dependency upon. The standard ALM flow would be to just take a standard reference to a Virtual Entity from this solution with the "add existing" option
in the ISV solution. It will then show as a missing dependency of the solution and be checked at solution import time. During import if a specified Virtual Entity does not yet exist, it would automatically be made visible without needing additional work.

To consume virtual entities:

1.  Create a separate solution as usual in CDS which will contain the consuming logic.

2.  Select Entities \> Add Existing and select the virtual entity you wish to reference from the list.

3.  When prompted to select assets to add, select any forms, views, or other elements you wish to customize, then select finish.

From the development tooling, existing elements such as forms may be modified for the virtual entity. Additionally, new forms, views, and other elements may also be added.

![Solution](../media/fovesolution.png)

When the resulting solution is exported, it will contain hard dependencies upon the virtual entity generated in the MicrosoftOperationsERPVE solution.
