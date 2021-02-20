---
# required metadata

title: Can't configure security group for site builder during initial deployment
description: This topic provides troubleshooting information for when deploying a new e-Commerce tenant, the AAD security group doesn't appear in the dropdown in the dialog to create the e-commerce components.
author: Reza-Assadi
manager: AnnBe
ms.date: 02/17/2021
ms.topic: Troubleshooting
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.18

---

# Can't configure security group for site builder during initial deployment

[!include [banner](../../includes/banner.md)]

## Description
During the steps to Deploy a new e-commerce tenant, the AAD Security Group doesn't appear in the dropdown in the dialog to create the e-commerce components.

## Resolution

### Provision the e-commerce site with a user in the correct tenant
1.  Go to the Azure portal at:[https://portal.azure.com.](http://portal.azure.com/)

2.  Follow the instructions to [Create a basic group and add members using Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    under the tenant that the LCS project for your e-Commerce site was provisioned for.

3.  Go to the LCS portal at: [http://lcs.dynamics.com](https://lcs.dynamics.com/) and log in with an account that is in the same tenant as the AAD Security Group that you just created that also has access to view the AAD Security
    Group.

4.  Navigate through the setup experience to configure the e-Commerce site. The security group should now be visible in the dialog when provisioning the e-commerce components.

> [!NOTE]
> For the drop down with the security groups to get populated you must hit the '**Enter**' key after typing in the name of the AAD Security Group you created. The search will filter all the AAD Security Groups the user has access to that start with the search text, so you can use a shorter search term to allow a broader search for troubleshooting purposes. 

## Additional Resources
- [Create a basic group and add members using Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
- [Deploy a new e-commerce tenant](../deploy-ecommerce-site.md)
