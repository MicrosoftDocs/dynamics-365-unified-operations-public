---
# required metadata

title: Restrict access to storefront during testing or development
description: This topic provides how to restrict access to a Dynamics 365 Commerce storefront when internal testing or development is in process. 
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
ms.author: rassadi
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.18

---

# Restrict access to storefront during testing or development

[!include [banner](../../includes/banner.md)]

## Description
During internal testing or active development, you might want to restrict access to your site to prevent external users from accessing the published storefront pages.

## Resolution

### Setup AAD B2C using standard user flows
Follow the steps described in the [Set up a B2C tenant in Commerce](https://docs.microsoft.com/dynamics365/commerce/set-up-b2c-tenant) article to configure Azure Active Directory (AAD) B2C for your e-commerce site.

### Restrict user access to storefront pages and block creation of new users
1. Open site builder.

1. Select the appropriate site on the **Sites** page.

1. Select **Pages** on the left-hand navigation panel.

1. Select the page you want to restrict on the **Pages** page.

1. Select the primary page fragment on the left page fragment tree, and then select **Edit** on on the top-right corner of the page. 

1. Select **Requires sign-in?**, and then select **Finiah editing**.

1. Go to the Azure portal. 

1. Select the AAD B2C application that you created for your site access.

1. Select **User flows** in the left navigation panel.

1. Select **+ New user flow** on the top of the **User Flows** page.

1. Select the **Preview** tab on the **Select a user flow type** page.

1. Select **Sign in v2** in the middle of the page. Follow the steps in the [Set up a B2C tenant in Commerce](https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-b2c-tenant)
    article to configure it as your standard user flow for AAD B2C for your site during testing/development.



