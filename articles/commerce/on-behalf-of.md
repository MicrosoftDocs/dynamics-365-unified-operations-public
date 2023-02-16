---

# required metadata

title: Enable on behalf of (OBO) functionality for B2B e-commerce sites
description: This article describes how to enable on behalf of (OBO) capabilities for Microsoft Dynamics 365 Commerce business-to-business (B2B) sites.
author: mariash529
ms.date: 03/03/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chriffin
ms.search.region: Global
ms.author: mashneer
ms.search.validFrom: 2023-02-28
---

# Enable on behalf of functionality for B2B e-commerce sites

[!include [banner](includes/banner.md)]

This article describes how to enable on behalf of (OBO) functionality for Microsoft Dynamics 365 Commerce business-to-business (B2B) sites.

This article describes a new capability of B2B account managers to sign in to the B2B e-commerce website and perform operations on behalf of B2B buyers.

> [!NOTE]
> On behalf of (OBO) functionality is available in Dynamics 365 Commerce version 10.0.33 and later.

On behalf of (OBO) functionality allows retailer representatives such account managers to sign in to a B2B e-commerce website and select a B2B buyer organization and a buyer that they want to work on behalf of. The account manager can then view the same products, prices, promotions, and discount experiences as the buyer and can add items to a cart and place orders on behalf of the buyer. 

## Prerequisites

To enable the on behalf of feature, you must fulfill the following prerequisites.

- You must create an Azure Active Directory (Azure AD) B2B application. For instructions, see [Create and configure an Azure Active Directory application for account manager sign-in](obo-create-aad-application.md)
-You must create and configure a B2B sign-in page in Commerce site builder. For instructions, see [Create pages in site builder for on behalf of functionality](obo-add-pages-site-builder.md). 
- You must set up and configure on behalf of functionality for your environment in Commerce headquarters. For more information, see [Set up on behalf of functionality in Commerce headquarters](obo-configure-hq.md). 

## Sign in to a B2B site using on behalf of functionality

Once the prerequisites have been met, you are ready to sign in to a B2B site using on behalf of functionality.

To sign in to a B2B site using on behalf of functionality, follow these steps.
  
1. On the B2B site, select **Sign-in**.
1. Select **Employee sign-in**

    :::image type="content" source="media/obo-sign-in-experience.png" alt-text="Sign-in screen for business partner user has a button for Employee Sign-in":::

1. On the next screen, select the business buyer organization you want to work on behalf of.
1. Select a buyer whome you want to work on behalf of.

    :::image type="content" source="media/obo-select-business-partners.png" alt-text="Account Manager selects a business partner organization":::

Once these selections are made, you (the account manager) are now representing the buyer you selected, and have full access to their account information, pricing, catalog information, and discounts. You can now add items to the cart and create an order. Completed orders are easily distinguishable from regular orders because they are prefixed with the account manager name. 

You can also create a template for the buyer to use later. It is recommended that you create a distinctive name for the template that includes the account manager's name, and the purpose of the template. 

> [!NOTE]
> The following on behalf of experiences differ from a regular B2B site sign in experience.
> - The only form of payment that is provided is **On Account** payment method.  
> - Account managers have access to view a buyer's invoices, but aren't able to pay invoices. 
> - Account managers can create a new order template for the buyer. The order template will not have an additional identifier that the template has been created by the  account manager. 
> - Currently, the [Create Commerce catalogs for B2B sites](catalogs-b2b-sites.md) feature isn't supported with the on behalf of feature, and must be turned off to use the on behalf of functionality. 

