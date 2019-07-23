---
# required metadata

title: Deploy a new e-Commerce site
description: This topic covers the tasks associated with deploying a new e-Commerce site in Dynamics 365 for Commerce. 
author: stuharg
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
ms.author: shajain
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.5

---

# Deploy a new e-Commerce site

[!include [banner](includes/banner.md)]

[!include [banner](includes/preview-banner.md)]


## Overview of Microsoft Dynamics Lifecycle Services (LCS)
	
Lifecycle Services (LCS) is a cloud-based collaborative workspace which allows partners and customers to manage their projects and environments, view latest information on Dynamics products and features, and create, track and browse support incidents. e-Commerce management features are integrated in the LCS portal.

To learn more about Lifecycle Services, please see the [Lifecycle Services user guide](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/lifecycle-services/lcs-user-guide).
	
## Getting started

Before you can initialize e-Commerce, you need to have a project, environment, and Retail Cloud Scale Unit (RCSU) deployed. To perform  the initialization in the LCS portal, you need to have either Project Owner or Environment Admin role permissions. The environment topologies that are supported are production and sandbox.

For more information on environments, please see [Environment planning](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/imp-lifecycle/environment-planning).

For more information on RCSU, please see [Initialize retail Cloud Scale Unit](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/initialize-retail-channels).

## Initialize e-Commerce

This procedure walks through the initialization of the e-Commerce feature in an existing environment.

Before you proceed with the initialization, please make sure you have all the required information available:

- AAD B2C information (optional, can be added later with service request).
	- Client ID
	- Reply URL
	- SignUp SignIn Policy ID
	- Login Custom Domain
	- Tenant Name
	- Edit Profile Policy ID
	- Reset password Policy ID
- RCSU to be used.
- AAD security group to be used for system admins.
- Ratings and reviews moderation security group (optional).
- Domains to be associated with the environment.

When you have collected the above information, proceed with the following steps to initialize e-Commerce.

1. Log in to the [LCS portal](https://lcs.dynamics.com).
2. Navigate to the project that contains the environment on which you are planning to initialize e-Commerce.
3. Under **Environments**, click the the environment you want to use.
4. Under **Environment features**, click the **Retail manage** link.
5. On the **e-Commerce** tab, you should see that the e-Commerce components are not initialized yet and the only action available is to initialize e-Commerce.
6. Click **Initialize e-Commerce**. A pane will open on which you need to enter the information required for provisioning. 
7. Fill in the required information and proceed to the next page.
8. Fill in the required information on the new page and submit the form.
9. You will be returned to the **e-Commerce** view where you can see that the initialization started.
10. You can refresh the page or return to this view later to see the initialization status.
	
When e-Commerce is initialized from the LCS portal, the system provisions several components required for e-Commerce and associates them with the environment. After provisioning is done, the **e-Commerce** tab in the **Retail management** view will be updated to reflect the provisioning. The view shows the latest customization deployments and the status of any other ongoing deployments. The view also includes links to the e-Commerce site and the e-Commerce site management tool (the authoring tool).

## Access your authoring environment

You can find links to your e-Commerce site and the site management tool from the **e-Commerce** view in the **Retail management** view.

