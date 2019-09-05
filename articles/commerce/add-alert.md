---
# required metadata

title: Add an alert module to a page 
description: This topic covers alert modules and how to add them to site pages in Dynamics 365 Commerce.
author:  anupamar-ms
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
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-01
ms.dyn365.ops.version: 
---

# Add an alert module to a page

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers alert modules and how to add them to site pages in Dynamics 365 Commerce.

## Overview

An alert module is used to show informational messages inline on a page. Alert modules support a text message and a link. Alert modules can be used to show sitewide promotions which appear on all pages of am e-Commerce site. 

Alert modules are driven by CMS data which can authored in the tooling. This allows alert modules to be placed on any page.

## Examples of alert module uses in e-Commerce

* Alert modules can be used on the site header to indicate sitewide promotions or messages such as "Annual sale ends in 10 days" or "Save big with back to school sale. Shop Now." 

## Alert module properties

| Property name  |                 Values                 | Property Description                                         |
| :------------: | :------------------------------------: | ------------------------------------------------------------ |
|      Text      |                  Text                  | This is the text configured in the alert module.         |
| Text alignment | Right<br />        Left   <br />Center | This defines how text should be aligned within the alert module. |
| Dismiss alert  |             True or False              | Setting this property to True makes the alert dismissible by the customer. |
|      Link      |                                        | This is the URL for an optional link.                              |

 
## Add an alert module to a page 

To add an alert module to a page and set the required properties, do the following.

1. Create a new page template named "alert template."
1. In the **Main** slot of the default page, add an alert module.
1. Check in and publish the template. 
1. Create a new page named "alert page" with the "alert template" you created. 
1. In the **Main** slot of the new page, add an alert module.
1. In the settings for the alert module, add the alert text. You can edit the other properties if you want to further customize the alert module.
1. Save and preview the page. You should see an alert on the top of the page with the text you added.
1. Check in and publish the page. 
