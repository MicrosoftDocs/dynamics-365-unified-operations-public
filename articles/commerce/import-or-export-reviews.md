---
# required metadata

title: Import or export ratings and reviews
description: This describes how to import and export product ratings and reviews in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 10/26/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2017-06-20
---

# Import or export ratings and reviews

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This describes how to import and export reviews in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce offers [ratings and reviews](ratings-reviews-overview.md) as an omni-channel solution. When you decide to switch over to Dynamics 365 Commerce's ratings and reviews solution you may want to bring your existing ratings and reviews data to the Dynamics 365 Commerce platform. You may want to export ratings and reviews data from Dynamics 365 Commerce based on your business requirements. 

## Prerequisites

To import and export rating and reviews in Commerce you will need to fulfill the following prerequisites.

1. The ratings and review solution must be enabled for your e-commerce site on the Dynamics 365 Commerce platform. For more information, see [Opt in to use ratings and reviews] (opt-in-ratings-reviews.md) .
1. The Dynamics 365 Ratings and Reviews Power App Connector must be configured to enable Power Automate with either submit reviews or export reviews actions. For more information, see [TBD](TBD.md). 
1. Service-to-service authentication must be configured to securely call the ratings and reviews API from outside of Dynamics 365 Commerce. For more information, see [Configure service-to-service authentication](TBD.md).

## Import reviews

To migrate ratings and reviews data from your existing system into Dynamics 365 Commerce you must use a Power Automate connector. To do this you can either create a new Power Automate flow or using an existing flow. In the flow, you must add the Dynamics 365 Ratings and Review connector. documentation can be found [here] (http://url-to-be-created).  

1. Select the action for **Submit User Review**
2. Establish connection with the AAD app information created earlier.For more information, see [Configure service-to-service authentication](TBD.md).
3. The **Submit User Review** action takes one review at a time, so repeat the action sing the source reviews as a list to submit bulk reviews. 
	
## Export reviews

To export ratings and reviews data from Dynamics 365 Commerce using Power Automate  connector you can either create a new Power Automate flow or using an existing flow. In the flow, add the **Dynamics 365 Ratings and Review Connector**, documentation can be found **[here] (http://url-to-be-created)**.  


	1. Select the action for **Export All Reviews**
	2. Complete the action. 

![image](https://user-images.githubusercontent.com/42852473/137647111-8f0db51c-6124-4a00-ae7e-dbce94f566fd.png)
