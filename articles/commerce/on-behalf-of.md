---

# required metadata

title: Enable on behalf of (OBO) functionality
description: This article describes how to enable on behalf of (OBO) functionality for Microsoft Dynamics 365 Commerce business-to-business (B2B) sites.
author: mariash529
ms.date: 03/03/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chriffin
ms.search.region: Global
ms.author: mashneer
ms.search.validFrom: 2023-02-28
---

# Enable on behalf of (OBO) functionality

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes how to enable on behalf of (OBO) functionality for Microsoft Dynamics 365 Commerce business-to-business (B2B) sites.

> [!NOTE]
> OBO functionality is available in Dynamics 365 Commerce version 10.0.33 and later.

OBO functionality enables a retailer representative such an account manager to sign in to a B2B e-commerce website and select a B2B buyer organization and a buyer that they want to work on behalf of. The representative can then view the same products, prices, promotions, and discount experiences as the buyer, and can add items to a cart and place orders on behalf of the buyer. Activity license is required for each representative. 

## Prerequisites

To enable the OBO functionality, you must complete the following prerequisites:

- Create an Azure Active Directory (Azure AD) B2B application. For instructions, see [Create and configure an Azure AD application for account manager sign-in](obo-create-aad-application.md).
- Modify the B2B site's sign-in page in Commerce site builder so that it includes an employee sign-in button. For instructions, see [Create and modify pages for on behalf of (OBO) functionality](obo-add-pages-site-builder.md).
- Set up and configure OBO functionality for your environment in Commerce headquarters. For more information, see [Set up on behalf of (OBO) functionality](obo-configure-hq.md).

## Sign in to a B2B site by using OBO functionality

After the prerequisites have been met, you're ready to sign in to a B2B site by using OBO functionality.

To sign in to a B2B site by using OBO functionality, follow these steps.

1. On the B2B site, select **Sign-in**.
1. Select **Employee sign-in**.

    ![Example of the Employee sign-in button on the Sign-in page for a business partner user.](media/obo-sign-in-experience.png)

1. On the next page, select the business buyer organization that you want to work on behalf of.

    ![Example of the Select a Business Partner Organization page.](media/obo-select-business-partners-org2.png) 

1. On the next page, select the buyer that you want to work on behalf of.
    
    ![Example of the Select a Business Partner User page.](media/obo-select-business-partners-users3.png).

After this procedure is completed, you (as the account manager) now represent the buyer that you selected, and have full access to their account information, pricing, catalog information, and discounts. You can add items to the cart and create an order. Completed orders are easily distinguished from regular orders, because they're prefixed with the account manager's name.

You can also create a template for the buyer to use later. We recommend that you give the template a distinctive name that includes the account manager's name and the purpose of the template.

> [!NOTE]
> The OBO experience differs from the regular B2B site experience in the following ways:
>
> - The only method of payment that's provided is **On Account**.
> - Account managers have access to view a buyer's invoices, but they can't pay invoices.
> - Account managers can create a new order template for the buyer. The order template won't have an additional identifier to indicate that the template was created by the account manager.
> - The [Create Commerce catalogs for B2B sites](catalogs-b2b-sites.md) feature is supported with Catalogs starting 10.0.35 release. 
> - Any custom extensions that affect customer hierarchies or sales groups might have to be modified to support OBO functionality. Any extensions that retrieve values directly from the user context on an e-commerce site might also have to be modified.

## Additional resources

[Create and configure an Azure AD application for account manager sign-in](obo-create-aad-application.md)

[Create and modify pages for on behalf of (OBO) functionality](obo-add-pages-site-builder.md)

[Set up on behalf of (OBO) functionality](obo-configure-hq.md)
