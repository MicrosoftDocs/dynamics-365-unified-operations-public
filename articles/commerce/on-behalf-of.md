---

# required metadata

title: Enable On Behalf Of capabilities for B2B e-commerce sites
description: This article describes how to create enable On Behalf Of capabilities for Microsoft Dynamics 365 Commerce business-to-business (B2B) sites.
author: mariash529
ms.date: 02/27/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: mashneer
ms.search.validFrom: 2023-02-28
---

# Enable on behalf of capabilities for B2B e-commerce sites

[!include [banner](includes/banner.md)]

This article describes a new capability of B2B account managers to sign in to the B2B e-commerce website and perform operations on behalf of B2B buyers.

> [!NOTE]
> This article applies to Dynamics 365 Commerce version 10.0.33 and later releases.

## Overview

Retailer representatives (typically, account managers) can sign in to the B2B e-commerce website and select a B2B buyer organization and a buyer that they want to work on behalf of. The account manager can then view the same products, prices, promotions, and discount experience as the buyer and can add items to a cart and place orders on behalf of the buyer. 

## Prerequisites
To enable this feature, Azure Active Directory B2B application needs to be [created](obo-create-aad-application.md). In addition, a B2B sign-in page in **site builder** needs to be [configured](obo-add-pages-site-builder.md). Finally, Dynamics 365 environment should be [configured](obo-configure-hq.md) accordingly. 

## Experience
  
Account manager should sign-in into B2B e-Commerce site by clicking **Sign-in**, and then clicking a button **Employee sign-in**:

:::image type="content" source="media/obo-sign-in-experience.png" alt-text="Sign-in screen for business partner user has a button for Employee Sign-in":::

On the next screen, the account manager should select the business buyer organization they intend to work on behalf of, and then a buyer, they intend to work on behalf of.

:::image type="content" source="media/obo-select-business-partners.png" alt-text="Account Manager selects a business partner organization":::

Once these selections are made, the account manager is now representing the buyer they have selected and has full access to their account information, pricing, catalog information and discounts. The account manager can now put the items in the cart and create an order, utilizing full e-Commerce experience. The completed orders will be easily distinguishable  from the regular orders since they will be prefixed with the account manager name. The account manager can create a template for the buyer to use later. It is recommended to create a distinctive name for the template that includes the account manager name and a purpose of the template. 

> [!NOTE]
> The following experiences differ in on behalf of experience.
> 1.	The only form of payment that is provided is **On Account** payment method.  
> 1.	An account manager has access to view the buyer’s invoices but is not able to pay invoices. 
> 1.	An account manager can create a new **order template** for the buyer. The order template will not have an additional identifier that the template has been created by the  account manager. 
> 1.	[Catalog](catalogs-b2b-sites.md) feature is not supported in the first release of on behalf of feature, and must be turned off to use this functionality. 

