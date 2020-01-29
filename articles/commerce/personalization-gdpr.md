---
# required metadata

title: Opt out of personalized recommendations
description: This topic explains how to enable customers to opt out of receiving personalized recommendations in Microsoft Dynamics 365 Commerce. 
author: bebeale
manager: AnnBe
ms.date: 01/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail, eCommerce
ms.author: bebeale
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# Opt-out of personalized recommendations

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic explains how to enable customers to opt out of receiving personalized recommendations in Microsoft Dynamics 365 Commerce. 

## Overview

During account creation, new customers are automatically opted in to receiving personalized recommendations. Dynamics 365 Commerce provides the ability to allow users to opt out of receiving personalized recommendations and restrict the processing of their personal data. This means that authenticated users who opt out of receiving personalized recommendations will stop seeing personalized lists immediately. Additionally, all personal data collected for personalization will be removed from personalized recommendations models. 

For more information about personalized product recommendations, see [Enable personalized recommendations](personalized-recommendations.md).

## Ways for retailers to implement an opt-out experience

Retailers have three ways to implement an opt-out experience.

### On behalf of the user

From within **Account Management** in Commerce back office, retailers have the ability to opt out on behalf of the user.

1. From the back office home page, search for **all customers**.
1. Search for a customer, and then select the **Retail Tab**.

    ![Account management](./media/Disablepersonalizationpart1.png)

1. Under **Privacy**, for **Disable personalization** select **Yes**.

    ![Privacy settings](./media/Disablepersonalizationpart2.png)

1. Select **Save** and close the form.

### Module opt-out experience

Retailers can enable authenticated users to opt out of personalized recommendations by themselves. This is accomplished by adding the user opt-out module to customer account profile pages.

### Custom extensions

Retailers wanting to create their own extensions to manage the opt-out experience for their users will need to reference the [Call Retail Server APIs](e-commerce-extensibility/call-retail-server-apis.md) and [Online channel extensibility](e-commerce-extensibility/overview.md) documentation.

## Obtain a digital copy of personalized recommendations data on behalf of an authenticated user

Customers may want to obtain a digital copy of their personal data and also see an exported view of their recommendations results. Once asked, the retailer would need to create a customized extension that will call the Retail Server API and query for the full results from the "Picks for you" list based on the customer's Customer ID. The results can then be exported in CSV format and shared with the customer.

An example of how a retailer could accomplish this task is provided below.

- The retailer would need to create a custom extension to pull personal recommendations data on behalf of the user. Steps on how to create modules, clone existing modules, call Retail Server APIs, and call data actions are all covered in the [Online channel extensibility](e-commerce-extensibility/overview.md) documentation.
- The custom extension would need to make a call to the "get-recommendations" core data action and pass it the required information based on the requirements of the list. In the case of a "Picks for you" list, the extension would need to pass the data action the proper list name and Customer ID.
    - One way a retailer might create the custom extension is to clone the existing product collection module used to return recommendations results. By cloning this existing module, a retailer could modify the existing code and add a new button to export the recommendations results to a CSV file. For more information, see [Clone a starter kit module](e-commerce-extensibility/clone-starter-module.md) and [Product collection modules](product-collection-module-overview.md). 
    - For a full view of the Retail Server API library, see [Retail Server Customer and Consumer APIs](retail/dev-itpro/retail-server-customer-consumer-api.md).  
- Once the custom extension is created, the retailer would be able to export a CSV file of all recommendations results based on the unique Customer ID of the authenticated user.
- The retailer could then share the exported CSV file containing the full personalized list of recommended products with the authenticated user.

## Additional resources

[Product recommendations overview](product-recommendations.md)

[Enable product recommendations](enable-product-recommendations.md)

[Enable personalized recommendations](personalized-recommendations.md)

[Add product recommendation lists to pages](add-reco-list-to-page.md)

[Add recommendations panel to POS devices](.../retail/add-recommendations-control-pos-screen)

[Product collection module overview](product-collection-module-overview.md)
