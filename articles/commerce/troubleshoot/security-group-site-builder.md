---
# required metadata

title: Can't configure a security group for Commerce site builder during initial deployment
description: This topic provides troubleshooting guidance that can help when the Microsoft Azure Active Directory (Azure AD) security group for Commerce site builder doesn't appear as an option when you create e-commerce components in Microsoft Dynamics Lifecycle Services (LCS) during initial deployment of a new e-commerce tenant.
author: Reza-Assadi
ms.date: 03/11/2021
ms.topic: Troubleshooting
ms.prod: 
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

# Can't configure a security group for Commerce site builder during initial deployment

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance that can help when the Microsoft Azure Active Directory (Azure AD) security group for Commerce site builder doesn't appear as an option when you create e-commerce components in Microsoft Dynamics Lifecycle Services (LCS) during initial deployment of a new e-commerce tenant.

## Description

When you create the e-commerce components as part of the process of deploying a new e-commerce tenant that includes the Commerce site builder component, the Azure AD security group doesn't appear as an option in the dialog box.

## Resolution

### Provision the e-commerce site with a user in the correct tenant

1. Go to the [Azure portal](https://portal.azure.com/).
1. Under the tenant that the LCS project for your e-commerce site was provisioned for, follow the instructions in [Create a basic group and add members using Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal).
1. Go to [LCS](https://lcs.dynamics.com/), and sign in by using an account that shares the same tenant as the Azure AD security group that you just created. The account must have access to view the Azure AD security group.
1. Complete the setup steps to configure the e-commerce site. When you provision the e-commerce components, the security group should now appear as an option in the dialog box.

> [!NOTE]
> To ensure that the field in the dialog box is filled with the list of security groups, you must select **Enter** after you enter the name of the Azure AD security group that you created. The search results will list all the Azure AD security groups that start with the search text, and that the user has access to. You can use a shorter search term to allow for broader search results.

## Additional resources

[Create a basic group and add members using Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)

[Deploy a new e-commerce tenant](../deploy-ecommerce-site.md)