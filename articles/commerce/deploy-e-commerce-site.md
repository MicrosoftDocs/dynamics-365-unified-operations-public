---
# required metadata

title: Deploy a new e-Commerce site
description: This topic explains how to deploy a new e-Commerce site in Microsoft Dynamics 365 for Commerce.
author: psimolin
manager: AnnBe
ms.date: 09/06/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Enduser
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: psimolin
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.5

---

# Deploy a new e-Commerce site

[!include [banner](includes/banner.md)]

[!include [banner](includes/preview-banner.md)]

## Overview of Microsoft Dynamics Lifecycle Services
	
Microsoft Dynamics Lifecycle Services (LCS) is a cloud-based collaborative workspace that partners and customers can use to manage their projects and environments, view the latest information about Microsoft Dynamics products and features, and create, track, and browse support incidents. e-Commerce management features are integrated into LCS.

To learn more about LCS, see the [Lifecycle Services user guide](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/lifecycle-services/lcs-user-guide).
	
## Getting started

Before you can initialize the e-Commerce feature, a project, environment, and Retail Cloud Scale Unit (RCSU) must be deployed. To do the initialization in LCS, you must have permissions for either the **Project Owner** role or the **Environment Admin** role. The production and sandbox environment topologies are supported.

For more information about environments, see [Environment planning](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/imp-lifecycle/environment-planning). For more information about RCSU, see [Initialize retail Cloud Scale Unit](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/deployment/initialize-retail-channels).

## Initialize e-Commerce

Use this procedure to initialize the e-Commerce feature in an existing environment.

Before you begin, make sure that you have all the required information:

- Optional: Microsoft Azure Active Directory (Azure AD) B2C information:

	- Client ID
	- Reply URL
	- SignUp SignIn Policy ID
	- Login Custom Domain
	- Tenant Name
	- Edit Profile Policy ID
	- Reset password Policy ID

    > [!NOTE]
    > This information can be added later, through a service request.

- The RCSU that will be used
- The Azure AD security group that will be used for system admins
- Optional: The security group that will be used for moderation of ratings and reviews
- The domains that will be associated with the environment

After you've collected this information, follow these steps to initialize e-Commerce.

1. Sign in to [LCS](https://lcs.dynamics.com).
2. Go to the project that contains the environment where you want to initialize e-Commerce.
3. In the **Environments** section, select the environment.
4. Under **Environment features**, select the **Retail manage** link.
5. On the **e-Commerce** tab, notice that the e-Commerce components aren't yet initialized, and that **Initialize e-Commerce** is the only action that is available.
6. Select **Initialize e-Commerce**. A dialog box appears, where you must enter the information that is required for provisioning.
7. Fill in the required information, and then go to the next page.
8. On the next page, fill in the required information, and then submit the form.

    You're returned to the **e-Commerce** tab, where you should see that initialization has been started.

9. To see the initialization status, either refresh the page or return to the **e-Commerce** tab later.
	
When e-Commerce is initialized from LCS, the system provisions several components that are required for e-Commerce and associates them with the environment. After provisioning is completed, the **e-Commerce** tab in the **Retail management** page is updated to reflect the provisioning. The page shows the latest customization deployments and the status of any other ongoing deployments. It also includes links to the e-Commerce site and the e-Commerce site management tool (the authoring tool).

## Access your authoring environment

You can find links to your e-Commerce site and the site management tool on the **e-Commerce** tab in the **Retail management** view.
