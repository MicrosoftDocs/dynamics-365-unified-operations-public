---
# required metadata

title: Author a footer module 
description: This topic covers footer modules and how to author them in Dynamics 365 for Commerce.
author: anupamar
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar-ms
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Author a footer module 

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]

This topic covers footer modules and how to author them in Dynamics 365 for Commerce.

## Overview

The footer module is special container that is used for hosting the modules that will be displayed on the page footer. For example, it includes links to various pages across the site such as Contact Us and Store Policies.

## Footer module properties 

Footer modules support heading and width properties similar to most containers. Footer container has multiple footer category slots. Each Footer category will render as a column in the footer module.

## Modules available in Footer

**Footer items:** A footer item can be a heading, an image, or a link. A heading can be used alone or in combination with an image and link. Each link in the footer can be configured as a link with text (for example, Contact Us, Privacy, etc.) or a link with text and an image (for example, social media links).

**Back to top.** A back to top module provides a link for quick navigation to the top of the page. A destination is required, and the default destination value is "**#**", which takes the user to the top of the page. 

## Author a footer module

1. Create a page fragment with a footer module.

1. Populate the footer module slots with the the desired modules (for example, "footer items," "back to top").

1. In the footer category, add a footer items module, then add a heading to it.

1. In the footer category, add multiple footer items with links.

1. Repeat for each footer category.

1. Save the page fragment.

1. Check in and publish.

On every page template created for the site, do the following.

1. In the **Main** slot of the default page, add the footer fragment to the footer module. 

1. Save the template.

1. Check in and publish the template.

This will ensure that every page renders the footer.
