---
# required metadata

title: Cookie consent module 
description: This topic covers cookie consent module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 05/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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

# Cookie consent module

[!include [banner](includes/banner.md)]

This topic covers cookie consent module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A cookie consent module is required to allow users to provide consent for any feature/module that tracks browser cookies. Per [Cookie compliance](cookie-compliance.md) its required for a site user to explicitly provide consent to these cookies. The consent is required the first time the user browses the site on a new browser session, once consent is received its tracked it will not be prompted again.

If user consent is not received, modules/feature that require the consent will not be rendered on the page. E.g. Checkout module, Social share module, Preferred store feature etc require cookie consent and will not be rendered if consent is not received. 

A cookie consent module is can be configured on the page [Header fragment](author-header-module.md) so it can be enforced when the page loads.

![Example of a cookie consent module](./media/ecommerce_cookieconsent.PNG)

## Cookie consent module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Rich text                  | text | The text provides a notification to the site user that the site uses browser cookies and the user should accept for the site to be fully functional|
| Links | Link    | One or more links can be added to the site's privacy page, explaining the privacy policy and types of cookies, session storage etc that are tracked on the site. |


## Add a cookie consent module to a page

The cookie consent module can be authored on the page Header fragment. Once the header is added to all the site pages, cookie consent will be automatically rendered the first time the user navigates to any link on the page.

See [Header fragment](author-header-module.md) for more details.


## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Header fragment](author-header-module.md) 

[Cookie compliance](cookie-compliance.md)
