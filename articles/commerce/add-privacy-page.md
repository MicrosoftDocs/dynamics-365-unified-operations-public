---
# required metadata

title: Add a privacy policy page
description: This topic describes how to add a privacy policy page to your site in Dynamics 365 Commerce.
author: brshoo
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
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

# Add a privacy policy page
This topic describes how to add a privacy policy page to your site in Dynamics 365 Commerce.

## Overview

Privacy compliance includes organizational measures that inform site users on how their data is collected and handled. This information empowers users to then act on how they want their personal data to be handled.

## Review Microsoft's privacy policy in Dynamics 365 Commerce

To review Microsoft's Privacy Policy while logged into Commerce Authoring Tools, do the following.

- Click the question mark icon in the top-right corner and select **Privacy and cookies** from the drop down menu. 

A new tab will launch with a link to the [Microsoft Privacy Statement](https://privacy.microsoft.com/en-US/privacystatement). 

## Build a privacy policy page for your site

With Dynamics 365 Commerce, there are a number of ways to provide users of your site access to your privacy policy. This section will review building a privacy policy page and referencing the page using a footer fragment.
  
### Create a template

In Commerce Authoring Tools, navigate to the site for which you will be building the privacy policy page.

[!NOTE] If you already have a template created that can be used for your privacy page, skip ahead to the **Build a Privacy Page** section.

To create a template, do the following.

1. Go to **Templates /> New Template**.
1. Enter the template name and click **OK**.
1. In the template, add any required modules to the necessary page slots (hover over any red exclamation marks for guidance).
   - Example: The **HTML Head** slot may require a module, like the Default External Script Module.
1. In the **Body** slot, add a **Default Page** module.
1. In the **Main Slot** of the default page module, add a **Content Rich Block** module.
1. In the content rich block module, add a **Content rich block item**.
1. Check and publish the template.

### Build a Privacy Page

To build a privacy page, do the following.

1. Go to **Pages /> New Page**.
1. Select the template to be used for the privacy page.  
1. Enter a page name and URL, then click **OK**. 
1. In the **Main Slot** of the page, add a **Content Rich Block** module.
1. In the content rich block module, add a **Content rich block item**.
1. In the properties panel of the content rich block module, click **Add Data Source** and then select **RICH TEXT CONTENT**.
1. Enter privacy page content into the rich text editor. Expand the rich text editor to full screen mode if needed.
1. When content entry is completed, click **Preview** to preview the page in the browser.
1. Complete any remaining additions to the page and module properties.
1. Check in and publish the privacy page.

To publish the URL for the privacy page, do the following.

1. Go to **URLs** and select the privacy page URL.
1. Publish the selected URL.

### Create a link to the privacy page in a footer

A link to the privacy page can be added to a fragment and then shared and updated across multiple site pages by referencing the fragment. For this example, we will add a link to the privacy page to a footer fragment.

To add a link to a footer fragment, do the following.

1. Go to **Fragments /> New Page Fragment**.
1. Select the **Footer** module and enter a name under **Page Fragment Name**.
1. Under the **sub footer** slot, add a sub footer module.
1. Click **Add Data Source** in the properties panel and select **Links**.
1. Enter the link text and privacy page URL.
   - To obtain the URL for the privacy page, go to the privacy page in **Pages** and copy the URL from the properties panel.
1. Save, check in, and publish the fragment.
1. Preview the fragment and test the link to the privacy policy page.

The fragment can now be referenced in a template for other site pages. Referencing this fragment in the footer module of the template will place the link reference on any pages built with the template.
