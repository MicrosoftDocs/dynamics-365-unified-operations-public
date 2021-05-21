---
# required metadata

title: Restrict access to a storefront during testing or development
description: This topic explains how to restrict access to a Microsoft Dynamics 365 Commerce storefront while internal testing or development is occurring.
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
ms.author: rassadi
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.18

---

# Restrict access to a storefront during testing or development

[!include [banner](../../includes/banner.md)]

This topic explains how to restrict access to a Microsoft Dynamics 365 Commerce storefront while internal testing or development is occurring.

## Description

During internal testing or active development, you might want to restrict access to your site to prevent external users from accessing the published storefront pages.

## Resolution

### Set up Azure AD B2C by using standard user flows

For information about how to configure Azure Active Directory B2C (Azure AD B2C) for your e-commerce site, see [Set up a B2C tenant in Commerce](../set-up-b2c-tenant.md).

### Restrict user access to storefront pages and block the creation of new users

To restrict user access to storefront pages in Commerce site builder, follow these steps.

1. Go to your site.
1. Select **Pages**, and then select the page to restrict user access for.
1. Select the module or fragment slot, and then select **Edit**.
1. In the properties pane, select **Requires sign-in?**, and then select **Finish editing**.
1. Select **Publish**.

To block the creation of new users in Azure AD, follow these steps.

1. Go to the [Azure portal](https://portal.azure.com/).
1. Select the Azure AD B2C application that you created for your site access.
1. In the left navigation, select **User flows**.
1. At the top of the **User Flows** page, select **New user flow**.
1. On the **Select a user flow type** page, select **Preview**.
1. In the middle of the page, select **Sign in v2**. Then follow the steps in [Set up a B2C tenant in Commerce](../set-up-b2c-tenant.md) to configure the flow as your site's standard user flow for Azure AD B2C during testing or development.

## Additional resources

[Set up a B2C tenant in Commerce](../set-up-b2c-tenant.md)

[Set up custom pages for user sign-ins](../custom-pages-user-logins.md)
