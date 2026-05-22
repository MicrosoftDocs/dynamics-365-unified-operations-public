---
title: Category pricing rules to create trade agreements
description: Learn how to create sales price trade agreements using a category pricing rule in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/06/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-06-30
ms.search.form: DefaultDashboard, RetailDiscountPricingWorkspace, RetailPricingDiscountCategoryPriceRule, RetailCategoryPriceRule, EcoResCategorySingleLookup, RetailCategoryPriceWizard, PriceDiscAdm, PriceDiscAdmTable
ms.custom: 
  - bap-template
---
# Category pricing rules to create trade agreements

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to create sales price trade agreements by using a category pricing rule in Microsoft Dynamics 365 Commerce.

The following procedure demonstrates how to create sales price trade agreements by using a category pricing rule. The demo data company used to create this task is USRT. This task is intended for the Commerce merchandising manager role.

To create sales price trade agreements by using a category pricing rule, follow these steps:

1. Select **Pricing and discount management**.
1. Select **New**.
1. Select **Category price rule**.
1. In the list, select the row.
1. In the **Account code** field, select an option. Use a **Group** type account code to set up sales price trade agreements that are specific for Channels, Loyalty programs, Catalogs, and Affiliations.  
1. In the **Account selection** field, enter or select a value.
1. In the **Category** field, enter or select a value.
1. In the **Amount/Percent** field, enter a number.
1. In the **Rounding version** field, enter or select a value.
1. Select **Generate trade agreements**.
1. Select **Next**.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. In the **Find next** field, select **Yes**.
1. Select **Next**.
1. Select **Finish**. This step creates a trade agreement journal and opens it for your review.  
1. In the list, find and select the desired record. The trade agreement journals created from the Category pricing rules aren't posted. You can  review and edit the prices generated before posting them.  
1. Select **Edit**.
1. In the **Amount in currency** field, enter a number.
1. Select **Post**.
1. Select **OK**.
1. Close the page.
1. Select the **Category price rules** tab. Channel-specific category pricing rules appear in the list.  

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
