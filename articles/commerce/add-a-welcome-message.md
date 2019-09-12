---
# required metadata

title: Add a welcome message to your site
description: This topic describes how to add a welcome message to your Dynamics 365 Commerce website.
author: psimolin
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Add a welcome message to your site

This topic describes how to add a welcome message to your Dynamics 365 Commerce website.

## Overview

A welcome message on your e-Commerce website can inform visitors of ongoing sales, site updates, or seasonal collection availability.  The welcome message is set using the alert module.

The alert module should be added to the **Error/Information messages** slot of the header fragment. This allows you to specify the text to be displayed as well as the text color and alignment. You can also configure whether the message can be dismissed by a visitor to the site. When the welcome message is added to the shared header fragment, it will be displayed on each page that is using the template where the shared header fragment is used.

To add a welcome message to your site, do the following.

1. In Commerce, navigate to your site.
1. Click **Fragments**.
1. Click the header fragment you want to add the message to.
1. Expand **Error/Information messages** in the outline tree.
1. Select the **Alert** module. If one does not yet exist, click the ellipsis button (**...**) next to **Error/Information messages**, select **Add module**, then select the alert module and click **OK*.
1. From the right-side property pane, select the **Data** tab.
1. Click **Add Data Source**, then select **Content**.
1. Add the welcome message text to the **Input Text** field. 
1. Save, check in, and publish the header fragment.

Now all site pages that use the header fragment will display your welcome message on the top of the page.
