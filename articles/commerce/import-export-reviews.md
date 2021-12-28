---
# required metadata

title: Import and export ratings and reviews
description: This topic describes how to import and export product ratings and reviews in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 12/28/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2017-06-20
---

# Import and export ratings and reviews

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to import and export product ratings and reviews in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce offers [ratings and reviews](ratings-reviews-overview.md) as an omni-channel solution. When you decide to switch to Dynamics 365 Commerce's ratings and reviews solution, you may want to bring your existing ratings and reviews data to the Dynamics 365 Commerce platform. You may also want to export ratings and reviews data from Dynamics 365 Commerce based on your business requirements. Both importing and exporting ratings and reviews to and from Dynamics 365 Commerce is made possible using a Microsoft Power Automate connector. 

> [!NOTE]
> For information on getting started with logic flows in Power Automate, see [Create a cloud flow in Power Automate](/power-automate/get-started-logic-flow).

## Prerequisites

To import and export rating and reviews in Commerce you must fulfill the following prerequisites.

- The ratings and review solution must be enabled for your e-commerce site on the Dynamics 365 Commerce platform. For more information, see [Opt in to use ratings and reviews](opt-in-ratings-reviews.md).
- The Dynamics 365 Ratings and Reviews Power App Connector must be configured to enable Power Automate with either "submit reviews" or "export reviews" actions. For more information, see [Dynamics 365 Commerce - Ratings and Reviews (Preview)](/connectors/dynamics365ratingsre/). 
- Service-to-Service (S2S) authentication must be configured to securely call the ratings and reviews API from outside of Dynamics 365 Commerce. For more information, see [Configure Service-to-Service authentication](service-to-service-auth.md).

## Import ratings and reviews

To import ratings and reviews data from your existing system into Dynamics 365 Commerce you must add the Dynamics 365 Ratings and Review Power Automate connector to either an existing or new Power Automate flow. For more information, see [Dynamics 365 Commerce - Ratings and Reviews (Preview)](/connectors/dynamics365ratingsre/).  

> [!NOTE]
> Before following the steps below, you must first [configure Service-to-Service authentication](service-to-service-auth.md).

To import ratings and reviews into Commerce using the Dynamics 365 Ratings and Reviews Power Automate connector, follow these steps.

1. Select the **Submit User Review** action.
1. Establish a connection using the Azure Active Directory (Azure AD) app information created when you configured Service-to-Service authentication. For more information, see [Configure service-to-service authentication](service-to-service-auth.md).
1. The **Submit User Review** action takes one review at a time, so repeat the action using the source reviews as a list to submit bulk reviews. 
	
## Export ratings and reviews

To export ratings and reviews data from Dynamics 365 Commerce you must add the Dynamics 365 Ratings and Review Power Automate connector to either an existing or new Power Automate flow. For more information, see [Dynamics 365 Commerce - Ratings and Reviews (Preview)](/connectors/dynamics365ratingsre/).  

To export ratings and reviews from Commerce using the Dynamics 365 Ratings and Reviews Power Automate connector, follow these steps.

1. Select the **Export All Reviews** action.
1. Complete the action. 

## Additional resources

[Ratings and reviews overview](ratings-reviews-overview.md)

[Manage ratings and reviews](manage-reviews.md)

[Configure ratings and reviews](configure-ratings-reviews.md)

[Configure Service-to-Service authentication](service-to-service-auth.md)

[Ratings and reviews FAQ](ratings-reviews-faq.md)
