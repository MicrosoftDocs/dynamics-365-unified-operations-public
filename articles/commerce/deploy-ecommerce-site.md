---
# required metadata

title: Deploy a new e-commerce tenant
description: This topic describes how to deploy a new Dynamics 365 Commerce e-commerce site by using Microsoft Dynamics Lifecycle Services (LCS).
author: psimolin
ms.date: 07/02/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Deploy a new e-commerce tenant

[!include [banner](includes/banner.md)]

This topic describes how to deploy a new Dynamics 365 Commerce e-commerce site by using Microsoft Dynamics Lifecycle Services (LCS).

Microsoft Dynamics Lifecycle Services (LCS) is a cloud-based collaborative workspace that partners and customers can use to manage their projects and environments, view the latest information about Microsoft Dynamics products and features, and create, track, and browse support incidents. E-commerce management features are integrated into LCS.

To learn more about LCS, see the [Lifecycle Services User Guide](/dynamics365/unified-operations/dev-itpro/lifecycle-services/lcs-user-guide).
	
## Get started

Before you can initialize e-commerce, you must initialize a project, an environment, and a Retail Cloud Scale Unit (RCSU). To do the initialization in LCS, you must have permissions for either the Project Owner or Environment manager role. The production and sandbox environment topologies are supported.

For more information about environments, see [Environment planning](/dynamics365/unified-operations/fin-and-ops/imp-lifecycle/environment-planning). For more information about RCSU, see [Initialize Retail Cloud Scale Unit](/dynamics365/unified-operations/dev-itpro/deployment/initialize-retail-channels).

## Initialize e-commerce

Use this procedure to initialize the e-commerce feature in an existing environment.

Before you begin, make sure that you have the following required information:

- The RCSU that will be used.
- The Microsoft Azure Active Directory security group that will be used for e-commerce system admins.
- The Microsoft Azure Active Directory security group that will be used for ratings and reviews moderators.
- The domains that will be associated with the environment.

In addition, you can collect the following optional information:

- Azure AD business-to-consumer (B2C) information:

	- Tenant Name.
	- Client ID.
	- Login Custom Domain.
	- Reply URL.
	- SignUp SignIn Policy ID.
	- Reset password Policy ID.
	- Edit Profile Policy ID.

> [!NOTE]
> This information can be added later, through a service request.

After you've collected the required information, follow these steps to initialize e-commerce.

1. Sign in to [LCS](https://lcs.dynamics.com).
1. Open the project that contains the environment where you want to initialize e-commerce.
1. In the **Environments** section, select the environment.
1. Under **Environment features**, select the **Retail manage** link.
1. On the **e-Commerce** tab, select **Setup**. A dialog box appears, where you must enter the information that is required for provisioning.
1. Fill in the required information, and then go to the next page.
1. On the next page, fill in the required information, and then submit the form. You're returned to the **e-Commerce** tab, where you should see that initialization has been started.
1. To view the initialization status, either **Refresh** or return to the **e-Commerce** tab later.
	
When e-commerce is initialized from LCS, the system provisions several components that are required for e-commerce and associates them with the environment. After provisioning is complete, the **e-Commerce** tab on the **Retail management** page is updated to reflect the provisioning. The page shows the latest customization deployments and the status of any other ongoing deployments. It also includes links to the e-commerce site and the Commerce site builder where sites are authored.

## Access Commerce site builder

To access Commerce site builder, go to the **e-Commerce** tab on the **Retail management** page in LCS and select the **e-Commerce site management tool** link. The site builder landing page displays a tenant-level view. From this page, you can:

- Modify tenant-level settings.
- Navigate to any site you have created, and have permission to view. 
- Access Reviews features such as moderation and reporting.
- Create a new site. For more information about how to create a new site, see [Create an e-commerce site](create-ecommerce-site.md) . 

## Additional resources

[Configure your domain name](configure-your-domain-name.md)

[Create an e-commerce site](create-ecommerce-site.md)

[Associate a Dynamics 365 Commerce site with an online channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Upload URL redirects in bulk](upload-bulk-redirects.md)

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]