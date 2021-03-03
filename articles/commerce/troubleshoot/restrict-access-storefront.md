---
# required metadata

title: Restrict access to storefront during testing or development
description: This topic describes how to restrict access to a Dynamics 365 Commerce storefront when internal testing or development is in process. 
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
ms.author: rassadi
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.18

---

# Restrict access to storefront during testing or development

[!include [banner](../../includes/banner.md)]

This topic describes how to restrict access to a Dynamics 365 Commerce storefront when internal testing or development is in process.

## Description

During internal testing or active development, you might want to restrict access to your site to prevent external users from accessing the published storefront pages.

## Resolution

### Set up AAD B2C using standard user flows

For steps on how to configure Azure Active Directory (Azure AD) business-to-consumer (B2C) for your e-commerce site, see [Set up a B2C tenant in Commerce](../set-up-b2c-tenant.md).

### Restrict user access to storefront pages and block creation of new users 

To restrict user access to storefront pages in Commerce site builder, follow these steps.

1. Go to your site.
1. Select **Pages**, and then select the page for which you want to restrict user access.
1. Select the module or fragment slot, and then select **Edit**. 
1. Select **Requires sign-in?** in the properties pane, and then select **Finish editing**.
1. Select **Publish**.

To block creation of new users in Azure AD, follow these steps.

1. Go to the Azure portal. 
1. Select the Azure AD B2C application that you created for your site access.
1. Select **User flows** in the left navigation pane.
1. At the top of the **User Flows** page, select **+ New user flow**.
1. On the **Select a user flow type** page, select **Preview**.
1. Select **Sign in v2** in the middle of the page. Then follow the steps in [Set up a B2C tenant in Commerce](https://docs.microsoft.com/dynamics365/commerce/set-up-b2c-tenant) to configure it as your standard user flow for Azure AD B2C for your site during testing/development.

## Additional resources

[Set up a B2C tenant in Commerce](../set-up-b2c-tenant.md)

[Set up custom pages for user sign-ins](../custom-pages-user-logins.md)
