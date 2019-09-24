---
# required metadata

title: Author a footer module 
description: This topic covers footer modules and how to author them in Dynamics 365 Commerce.
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
ms.dyn365.ops.version: Release 10.0.5
---

# Author a footer module 

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers footer modules and how to author them in Dynamics 365 Commerce.

## Overview

The footer module is special container that is used for hosting the modules that will be displayed on the page footer. For example, it includes links to various pages across the site such as Contact Us and Store Policies.

## Footer module properties 

Footer modules support heading and width properties similar to most containers, and also support adding multiple footer category slots. Each footer category module added will render as a column in the footer module.

## Modules available in a footer module

**Footer items:** A footer items module can contain a heading, an image, or a link. A heading can be used alone or in combination with an image and link. Each link in the footer can be configured as a link with text (for example, Contact Us, Privacy, etc.) or a link with text and an image (for example, social media links).

**Back to top.** A back to top module provides a link for quick navigation to the top of the page. A destination is required, and the default destination value is "**#**", which takes the user to the top of the page. 

## Author a footer module

1. In the navigation pane, click **Fragments**, then click **New Page Fragment**.
1. In the New Page Fragment dialog box, select the footer module, enter a name for the page fragment, then click **OK**.
1. In the outline tree pane, click the footer module ellipsis button (**...**), then select **Add Module**.
1. In the Add Module dialog box, select the footer category module, then click **OK**.
1. In the outline tree pane, click the footer category module ellipsis button (**...**), then select **Add Module**.
1. In the Add Module dialog box, select the footer item module, then click **OK**.
1. In the outline tree, select the footer item module. In the right-side properties pane, configure the desired heading, link and link text, and image as needed.
1. To add additional footer items, repeat steps 5-7 as needed.
1. To add a "back to top" link to your footer, click the footer category module ellipsis button (**...**), then select **Add Module**.
1. In the Add Module dialog box, select the back to top module, then click **OK**.
1. In the outline tree pane, select the back to top module. In the right-side properties pane, configure the back to top module as needed.
1. Save, check in, and publish the page fragment.

On every page template created for the site, do the following.

1. In the **Main** slot of the default page, add the footer fragment you created to the footer module. 
1. Save, check in, and publish the template.

This will ensure that every page renders the footer.
