---
# required metadata

title: Can't configure security group for Commerce site builder during initial deployment
description: This topic provides troubleshooting guidance for when the Azure Active Directory security group doesn't appear as a drop-down list option in the dialog box to create e-commerce components when deploying a new e-commerce tenant.
author: Reza-Assadi
manager: AnnBe
ms.date: 02/24/2021
ms.topic: Troubleshooting
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.18

---

# Can't configure security group for Commerce site builder during initial deployment

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance for when the Azure Active Directory (Azure AD) security group doesn't appear as a drop-down list option in the dialog box to create e-commerce components when deploying a new e-commerce tenant.

## Description

When implementing the steps to deploy a new e-commerce tenant including the site builder component, the Azure AD Security Group doesn't appear as a dialog box drop-down list option to create the e-commerce components.

## Resolution

### Provision the e-commerce site with a user in the correct tenant

1. Go to the Azure portal at:[https://portal.azure.com.](https://portal.azure.com/).
1. Follow the instructions to [Create a basic group and add members using Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) under the tenant that the Microsoft Dynamics Lifecycle Services (LCS) project for your e-commerce site was provisioned for.
1. Go to the LCS portal at [http://lcs.dynamics.com](https://lcs.dynamics.com/) and sign in with an account that shares the same tenant as the AAD security group that you just created. The account must have access to view the AAD security group.
1. Navigate through the setup steps to configure the e-commerce site. The security group should now be visible in the dialog box when provisioning the e-commerce components.

> [!NOTE]
> For the dialog box drop-down list to be populated with security groups, you must select **Enter** after entering the name of the AAD security group you created. The search results will list all the AAD security groups the user has access to that start with the search text, and you can use a shorter search term to allow for broader search results. 

## Additional resources

[Create a basic group and add members using Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)

[Deploy a new e-commerce tenant](../deploy-ecommerce-site.md)
