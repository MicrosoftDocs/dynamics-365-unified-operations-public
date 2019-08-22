---
# required metadata

title: Manage ratings and reviews 
description: This topic explains how to manage ratings and reviews using the Ratings and Reviews Moderation tool.
author:  gvrmohanreddy 
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2019-10-01
ms.dyn365.ops.version: Release 10.0.5
---

# Manage ratings and reviews

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic explains how to manage ratings and reviews using the Dynamics 365 Commerce Ratings and Reviews Moderation tool.

## Overview

Dynamics 365 Commerce uses Azure Cognitive Service to automatically moderate review text by redacting profane words. In addition, the Ratings and Reviews Moderation tool can be used to do the following.

- Moderate reviews by responding to them or taking them down
- Bulk import review data across products into a provided Power BI template and analyze ratings and reviews trends
- Delete a user's reviews after a request by the user

## Reading Reviews 
  
1. Go to **Site Management > Global Settings**.
1. Under **RnR Moderator**, click **Manage**.
1. Use the **Search** feature at the top of page to filter reviews by product ID, product name, or review text.
1. Additionally, there are filters to limit displayed reviews by time period, rating, channel, or takedown / responded / reported concern status.

![Ratings and Reviews Moderation home page](media/rnr-moderation-home.png) 

## Respond to a review 

Sometimes customers who have purchased a product express their satisfaction or dissatisfaction or may have misunderstandings about a product's usage. As a moderator, you can post a response to a review that will display inline with the review on the site. 

To respond to a review, do the following.

1. Go to **Site Management > Global Settings**.
1. Under **RnR Moderator**, click **Manage**.
1. ???
1. In the left pane, select the review that needs a response.
1. In the right pane, click **Add a response** to provide a response.
1. Enter the response text and choose which responder name to display. The default responder name is "Moderator."
1. When done, click **Post response**.

![Ratings and Reviews Moderation home page](media/rnr-moderation-response.png) 

## Take down a review 

Sometimes there is a business justification for a moderator to take down a customer review. 

To take down a review, do the following.

1. Go to **Site Management > Global Settings**.
1. Under **RnR Moderator**, click **Manage**.
1. ???
1. In the left pane, select the review that needs to be taken down.
1. In the right pane, select a takedown reason and click **Take down**.
	
## Delete a customer's reviews on request 

Sometimes a customer wants their ratings and reviews data to be permanently deleted from an e-Commerce website. When a moderator receives a removal request from a customer, they can remove the customer's data by using the delete reviews feature. To locate users, the email address the customer used to sign in and provide reviews is required. 

To locate and delete user data, do the following.

1. Go to **Site Management > Global Settings**.
1. Under **RnR Moderator**, click **Manage**. 
2. Click on Reviews in the left nav and then click on **Delete**. 
3. In the **Search for users by email address** box, enter the customer's email address and click **Search**.
5. If the customer has any reviews activity (for example, review submissions, votes on the helpfulness of other's reviews, or comments on another customer's review), the results will be displayed and each item will have a "Delete" option for the moderator to act on.
6. Click **Delete** for the review item you want to delete. When prompted for confirmation, click **Yes**. 
	
Refer to the following screenshot for more details.  
	
[!NOTE]
 - It may take up to 7 days for data to be completely removed from the system. Moderators should notify customers of this delay.
 - If a customer has changed their name in account settings, multiple items may display in the search results. The moderator should click **Delete** for each item to completely delete the customer's data. 

![Ratings and Reviews Moderation home page](media/rnr-moderation-delete-reviews.png) 

##  Downloading Ratings and Review data
Dynamics 365 Commerce - Ratings and Reviews allows C1's to import bulk data of ratings and reviews for analyzing trends.  There is a PowerBI template, with basic metrics, available for customer to connect the imported bulk data and see a dashboard, without needing to create your own dashboard.  C1 can also enhance the PowerBI template to meet their custom needs. 

1. Go to [eCommerce Authoring Tools](https://eCommerceAuthoringTool/) . 
2. Click on Reviews in the left nav and then click on Reporting link. 
3. Click on "Download reviews data" link to download ratings and reviews bulk data in .csv format and then save to your file location, e.g. c:\reviews\ReviewsData.csv file.


##  Steps to use PowerBI template to view ratings and review trends

1. C1 can also download "Power BI template" to view trends in a dashboard
2. Now open the downloaded Template, it will open in Power BI app. After opening this template it will show "Access to web content." then close this popup, and then close the "Refresh" error message as well.
3. Now go to Home menu, and click on "Edit queries", and then click on "Data source settings".
4. Now on "Data source settings" popup window, click on Change Source there is a url edit box.
5. In the URL text box, give the path of the previously downloaded reviews data, e.g. c:\reviews\ReviewsData.csv file.
6. Now click ok and then click Apply changes 
7.It will take 1-2 minutes to apply the data source, then click on Trends sheet to view ratings and reviews trends.


Refer to the following screenshots for more details:

![Ratings and Reviews Moderation home page](media/rnr-moderation-reports.png) 
![Ratings and Reviews Moderation home page](media/rnr-powerbi-datasource-settings.png) 
![Ratings and Reviews Moderation home page](media/rnr-powerbi-dashboard-template.png) 
