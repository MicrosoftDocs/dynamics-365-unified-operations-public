---
# required metadata

title: Add an alert module to a page 
description: This topic covers alert modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
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
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Add an alert module to a page

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers alert modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

An alert module is used to show inline informational messages on a page. Alert modules support a text message and a link. They can be used to show site-wide promotions that appear on all pages of an e-Commerce site. 

Alert modules are driven by data from the content management system (CMS) and can be put on any page.

## Examples of alert modules in e-Commerce

Alert modules can be used in the site header to indicate site-wide promotions or messages. Here are some examples:

"Annual sale ends in 10 days"

"Save big with back to school sale. Shop Now."

## Alert module properties

| Property name  | Value                              | Description |
|----------------|------------------------------------|-------------|
| Text           | Text                               | The text message that appears in the alert module. |
| Text alignment | **Right**, **Left**, or **Center** | A value that defines how text is aligned in the alert module. |
| Dismiss alert  | **True** or **False**              | If the value is set to **True**, the customer can dismiss the alert. |
| Link           | URL                                | The URL for an optional link. |

## Add an alert module to a page 

To add an alert module to a page and set the required properties, follow these steps.

1. Create a page template that is named **alert template**.
1. In the **Main** slot of the default page, add an alert module.
1. Check in the template, and publish it. 
1. Use the alert template that you just created to create a page that is named **alert page**. 
1. In the **Main** slot of the new page, add an alert module.
1. In the settings for the alert module, enter the alert text. You can edit the other properties if you want to customize the alert module further.
1. Save and preview the page. At the top of the page, you should see an alert that has the text that you added.
1. Check in the page, and publish it. 
