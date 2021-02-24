---
# required metadata

title: Sign in link redirects back to e-commerce site
description: This topic provides troubleshooting guidance for when a sign-in link redirects back to the e-commerce site instead of the sign-in page. 
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

# "Sign in" link redirects back to e-commerce site

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance for when a sign-in link redirects back to the e-commerce site instead of the sign-in page.

## Description

After configuring a new Azure Active Directory (Azure AD) business-to-consumer (B2C) tenant in Dynamics 365 Commerce site builder, selecting **Sign in** redirects user back to the main e-commerce landing page without navigating to the sign-in page.

## Resolution

### Ensure that the "Reply" URL is configured correctly in the AAD B2C application 

To ensure that the "Reply" URL is configured correctly in the AAD B2C application, follow these steps.

1. Go to the Azure portal at https://portal.azure.com](https://portal.azure.com/).
1. Select the AAD B2C application that you created for your site access.
1. Select the application you created during the AAD B2C setup.
1. Under the list for **Reply URL**, confirm that you have entries for both the site domain and the e-commerce-generated URLs, as shown in the following example image.

![AAD B2C Reply URL](media/aad-b2c-reply-url.jpg)

> [!NOTE]
>  Both the site domain and the e-commerce-generated URLs must follow a valid URL format without leading or trailing slashes.

## Additional resources

[Register a web application in Azure Active Directory B2C](https://docs.microsoft.com/en-us/azure/active-directory-b2c/tutorial-register-applications?tabs=app-reg-ga#register-a-web-application)

[Set up a B2C tenant in Commerce](../set-up-b2c-tenant.md)

