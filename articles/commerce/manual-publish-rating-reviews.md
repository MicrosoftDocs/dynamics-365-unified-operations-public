---
# required metadata
title: Enable manual publishing of ratings and reviews by a moderator
description: This topic describes how to enable manual publishing of ratings and reviews by a moderator in Microsoft Dynamics 365 Commerce, and how to manually publish ratings and reviews.
author: gvrmohanreddy
manager: annbe
ms.date: 09/03/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 
# optional metadata
# ms.search.form:  
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2021-09-03
ms.dyn365.ops.version: 10.0.22
---

# Enable manual publishing of ratings and reviews by a moderator

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to enable manual publishing of ratings and reviews by a moderator in Microsoft Dynamics 365 Commerce, and how to manually publish ratings and reviews.

Dynamics 365 Commerce's ratings and reviews solution uses Azure Cognitive Services to automatically redact profane words from review content and publish ratings and reviews. This process avoids the need for manual intervention to review and publish ratings and reviews to your e-commerce site. 

However, some businesses may prefer to manually review and approve reviews prior to publishing them. To enable the manual publishing of ratings and reviews by a moderator, you must enable the **Require moderator for ratings and reviews** feature in Commerce site builder.

## Enable the "Require moderator for ratings and reviews" feature in Commerce site builder

To enable the **Require moderator for ratings and reviews** feature in Commerce site builder, follow these steps.

1. Go to **Home \> Reviews \> Settings**.
1. Set the **Require moderator for ratings and reviews** option to **On**.

> [!NOTE]
> Enabling the **Require moderator for ratings and reviews** feature will stop the automatic publishing of ratings and reviews and will require manual publishing. Azure Cognitive Services will continue to filter profanity in review titles and content.

<!--!["Require moderator for ratings and reviews" setting in site builder](media/Ratings-reviews-settings-human-moderation.png)-->

## Publish ratings and reviews

When you enable the **Require moderator for ratings and reviews** feature, a moderator must manually review and publish ratings and reviews to make them appear on your e-commerce site. 

To review and publish ratings and reviews in site builder, follow these steps.

1. Go to **Reviews \> Moderation**. 
1. Ratings and review rows with **Unpublished** in the **Status** column indicate rating and reviews that are not published yet. To view only **Unpublished** ratings and reviews, select **Status: Needs review** from the status dropdown filter list above the ratings and reviews list.
1. Select one or more ratings and reviews that are in the **Unpublished** state and then select **Publish** on the command bar. The selected ratings and reviews will then be added to the publishing queue and will appear on the e-commerce website once published.  

> [!NOTE]
> - Once a rating and review is published, the status value changes from **Unpublished** to a null value (empty field).  
> - If you select multiple ratings and reviews that have mixed statuses and then select **Publish**, ratings and reviews in the unpublished state will be published and those already published will not be published again.

The following example illustration shows the site builder **Moderator** page with three unpublished ratings and review selected.

![Commerce site builder Moderator page with three unpublished ratings and review selected](media/Ratings-reviews-publishing-reviews.png)


<!--![Dynamics 365 Commerce - Ratings and Review configuration 2](media/Ratings-reviews-published-reviews.png)-->
<!--![Status filter](media/Ratings-reviews-published-reviews-status-filter.png)-->

## Additional resources

[Ratings and reviews overview](ratings-reviews-overview.md)
