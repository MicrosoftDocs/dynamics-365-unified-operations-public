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

This topic covers alert modules and how to add them to site pages in Dynamics 365 Commerce.

## Overview

Alert is used to show informational messages inline on a page. Alerts supports textual message and a link. For example, it can be used to show site wide promotions which appear on all pages of the site. 

Alert is driven by CMS data which can authored in the tooling. This allows Alerts to be placed on any page.

## Usage examples on ecommerce

* Alerts can be used on the site header to indicate site wide promotions or messages such as “Annual sale ends in 10 days” or “Save big with back to school sale. Shop Now”. 

## Alert module properties

| Property name  |                 Values                 | Property Description                                         |
| :------------: | :------------------------------------: | ------------------------------------------------------------ |
|      Text      |                  Text                  | This will be the text you can configure in the alert         |
| Text alignment | Right<br />        Left   <br />Center | This defines how text should be aligned within the alert module. |
| Dismiss alert  |             True or False              | By setting this property a C1 can choose the alert to be dismissible |
|      Link      |                                        | A link can be provided to Alert                              |

 

## Creating a page with Alert module 

This section explains how to add a Alert module to a new page and set the required properties. Refer to Templates and Pages for more details.

 

1. We need to first create a template. In tooling, create a new page template “Alert template”.

2. In the Main slot the Default Page, add an Alert module
3. Check-in and Publish. 

4. Now create a new page with the “Alert template” and call it “Alert page”
5. In the page outline, add Alert module to the Main slot
6. In the settings for Alert module, set the Text. You can edit the other properties if you want to customize it further.
7. Save and Preview. On Preview, you should see an alert on the top of the page with the text.
8. Check-in and Publish the page. 



See Header module for details on how to configure Alert on the site header.
