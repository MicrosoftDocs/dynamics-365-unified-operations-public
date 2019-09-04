---
# required metadata

title: Deploy a new e-Commerce site
description: This topic describes how to deploy a new e-Commerce site by using Microsoft Dynamics 365 Commerce.
author: psimolin
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Deploy a new e-Commerce site

[!include [banner](includes/banner.md)]

[!include [banner](includes/preview-banner.md)]

This topic describes how to deploy a new e-Commerce site by using Microsoft Dynamics 365 Commerce.

## Overview
	
Microsoft Dynamics Lifecycle Services (LCS) is a cloud-based collaborative workspace that partners and customers can use to manage their projects and environments, view the latest information about Microsoft Dynamics products and features, and create, track, and browse support incidents. E-Commerce management features are integrated into LCS.

To learn more about LCS, see the [Lifecycle Services User Guide](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/lifecycle-services/lcs-user-guide).
	
## Get started

Before you can initialize e-Commerce, you must initialize a project, an environment, and a Retail Cloud Scale Unit (RCSU). To do the initialization in LCS, you must have permissions for either the Project Owner or Environment manager role. The production and sandbox environment topologies are supported.

For more information about environments, see [Environment planning](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/imp-lifecycle/environment-planning). For more information about RCSU, see [Initialize Retail Cloud Scale Unit](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/deployment/initialize-retail-channels).

## Initialize e-Commerce

Use this procedure to initialize the e-Commerce feature in an existing environment.

Before you begin, make sure that you have the following **required** information:

- The RCSU that will be used
- The Microsoft Azure Active Directory (Azure AD) security group that will be used for system admins
- The domains that will be associated with the environment

In addition, you can collect the following **optional** information:

- Azure AD business-to-consumer (B2C) information:

	- Tenant Name
	- Client ID
	- Login Custom Domain
	- Reply URL
	- SignUp SignIn Policy ID
	- Reset password Policy ID
	- Edit Profile Policy ID

    > [!NOTE]
    > This information can be added later, through a service request.

- The security group that will be used for moderation of ratings and reviews

After you've collected the required information, follow these steps to initialize e-Commerce.

1. Sign in to [LCS](https://lcs.dynamics.com).
1. Open the project that contains the environment where you want to initialize e-Commerce.
1. In the **Environments** section, select the environment.
1. Under **Environment features**, select the **Retail manage** link.
1. On the **e-Commerce** tab, select **Setup**. A dialog box appears, where you must enter the information that is required for provisioning.
1. Fill in the required information, and then go to the next page.
1. On the next page, fill in the required information, and then submit the form. You're returned to the **e-Commerce** tab, where you should see that initialization has been started.
1. To view the initialization status, either **Refresh** or return to the **e-Commerce** tab later.
	
When e-Commerce is initialized from LCS, the system provisions several components that are required for e-Commerce and associates them with the environment. After provisioning is completed, the **e-Commerce** tab on the **Retail management** page is updated to reflect the provisioning. The page shows the latest customization deployments and the status of any other ongoing deployments. It also includes links to the e-Commerce site and the e-Commerce site management tool (the authoring tool).

## Access the authoring environment

To access the authoring environment, go to the **e-Commerce** tab on the **Retail management** page. There, you will find links to your e-Commerce site and the site management tool.
