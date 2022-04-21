---
# required metadata

title: Import and export ratings and reviews
description: This topic describes how to import and export product ratings and reviews in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 01/12/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2017-06-20
---

# Import and export ratings and reviews

[!include [banner](includes/banner.md)]

This topic describes how to import and export product ratings and reviews in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce offers [ratings and reviews](ratings-reviews-overview.md) as an omni-channel solution. When you switch to Dynamics 365 Commerce's ratings and reviews solution, you might want to move your existing ratings and reviews data over to the Commerce platform. You might also want to export ratings and reviews data from Commerce, based on your business requirements. A Power Automate connector lets you import ratings and reviews into Commerce and export them from Commerce.

> [!NOTE]
> For information about how to get started with logic flows in Power Automate, see [Create a cloud flow in Power Automate](/power-automate/get-started-logic-flow).

## Prerequisites

Before you can import and export ratings and reviews, you must fulfill the following prerequisites:

- The ratings and review solution must be enabled for your e-commerce site on the Commerce platform. For more information, see [Opt in to use ratings and reviews](opt-in-ratings-reviews.md).
- The Dynamics 365 Ratings and Reviews Power App Connector must be configured to enable either "submit reviews" or "export reviews" actions in Power Automate. For more information, see [Dynamics 365 Commerce - Ratings and Reviews (Preview)](/connectors/dynamics365ratingsre/).
- Service-to-Service (S2S) authentication must be configured to securely call the ratings and reviews application programming interface (API) from outside Commerce. For more information, see [Configure Service-to-Service authentication](service-to-service-auth.md).

## Import ratings and reviews

To import ratings and reviews data from your existing system into Commerce, you must add the Dynamics 365 Ratings and Review Power Automate connector to either an existing Power Automate flow or a new one. For more information, see [Dynamics 365 Commerce - Ratings and Reviews (Preview)](/connectors/dynamics365ratingsre/).

> [!IMPORTANT]
> Before you complete this procedure, you must [configure S2S authentication](service-to-service-auth.md).

To import ratings and reviews into Commerce by using the Dynamics 365 Ratings and Reviews Power Automate connector, follow these steps.

1. Select the **Submit User Review** action.
1. Establish a connection by using the Azure Active Directory (Azure AD) app information that was created when you configured S2S authentication. For more information, see [Configure service-to-service authentication](service-to-service-auth.md).
1. The **Submit User Review** action takes one review at a time. Therefore, repeat the action. Use the source reviews as a list to submit bulk reviews.
	
## Export ratings and reviews

To export ratings and reviews data from Commerce, you must add the Dynamics 365 Ratings and Review Power Automate connector to either an existing Power Automate flow or a new one. For more information, see [Dynamics 365 Commerce - Ratings and Reviews (Preview)](/connectors/dynamics365ratingsre/).

To export ratings and reviews from Commerce by using the Dynamics 365 Ratings and Reviews Power Automate connector, follow these steps.

1. Select the **Export All Reviews** action.
1. Complete the action. 

## Additional resources

[Ratings and reviews overview](ratings-reviews-overview.md)

[Opt in to use ratings and reviews](opt-in-ratings-reviews.md)

[Manage ratings and reviews](manage-reviews.md)

[Configure ratings and reviews](configure-ratings-reviews.md)

[Sync product ratings](sync-product-ratings.md)

[Enable manual publishing of ratings and reviews by a moderator](manual-publish-rating-reviews.md)

[Configure Service-to-Service authentication](service-to-service-auth.md)

[Ratings and reviews FAQ](ratings-reviews-faq.md)
