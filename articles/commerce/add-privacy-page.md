---
# required metadata

title: Add a privacy policy page
description: This topic describes how to add a privacy policy page to your site in Microsoft Dynamics 365 Commerce.
author: v-chgri
manager: annbe
ms.date: 01/08/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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

# Add a privacy policy page

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic describes how to add a privacy policy page to your site in Microsoft Dynamics 365 Commerce.

## Overview

Privacy compliance includes organizational measures that inform site users about how their data is collected and handled. Users can then decide how they want their personal data to be handled and can take appropriate action.

## Review the Microsoft privacy statement in Dynamics 365 Commerce

To review the Microsoft privacy statement while you're signed in to the Dynamics 365 Commerce authoring tools, select the **Help** button (**?**) in the upper-right corner, and then select **Privacy and cookies**. A new tab is opened that has a link to the [Microsoft privacy statement](https://privacy.microsoft.com/privacystatement).

## Build a privacy policy page for your site

In Dynamics 365 Commerce, there are several ways to give users of your site access to your privacy policy. This section shows how to build a privacy policy page and then reference the page by using a footer fragment.

The guidance that follows is an example that shows how to build a generic privacy policy page for a Commerce site. You're responsible for designing and implementing a privacy policy page solution that best meets your company's legal requirements.

To start, in the authoring tools, go to the site that you want to build a privacy policy page for.

### Create a template

> [!NOTE]
> If a template that can be used for the privacy policy page has already been created, skip ahead to the [Build a privacy policy page](#build-a-privacy-policy-page) section.

To create a template, follow these steps.

1. Go to **Templates \> New Template**.
1. Enter the template name, and then select **OK**.
1. In the template, add any required modules to the required page slots. For guidance, hover over the red exclamation marks.

    For example, the **HTML Head** slot might require a **Default External Script** module.

1. In the **Body** slot, add a **Default Page** module.
1. In the **Default Page** module, in the **Main** slot, add a **Content Rich Block** module.
1. In the **Content Rich Block** module, add a **Content rich block item** module.
1. Check the template in, and publish it.

### Build a privacy policy page

To build a privacy policy page, follow these steps.

1. Go to **Pages \> New Page**.
1. Select the template for the privacy policy page.
1. Enter a page name and URL, and then select **OK**. 
1. In the **Main** slot of the page, add a **Content Rich Block** module.
1. In the **Content Rich Block** module, add a **Content rich block item** module.
1. In the properties pane for the **Content Rich Block** module, select **Add Data Source**, and then select **Rich Text Content**.
1. In the rich text editor, enter the content for the privacy policy page. Expand the rich text editor to full-screen mode as you require.
1. When you've finished entering content, select **Preview** to preview the page in the web browser.
1. Complete any remaining additions to the page and module properties.
1. Check the privacy policy page in, and publish it.

To publish the URL for the privacy policy page, follow these steps.

1. Go to **URLs**, and select the URL for the privacy policy page.
1. Publish the selected URL.

### Create a link to the privacy policy page in a footer

You can add a link to the privacy policy page to a fragment. In this way, you can share the link and update it across multiple site pages by referencing the fragment. This example shows how to add a link to the privacy policy page to a footer fragment.

To add a link to a footer fragment, follow these steps.

1. Go to **Page Fragments \> New Page Fragment**.
1. Select the **Footer** module, and then enter a name in the **Page Fragment Name** field.
1. In the **Footer category** slot, add a **Footer item** module.
1. In the properties pane on the right, select **Link text**.
1. In the **Link text** dialog box, enter the link text and link target of the privacy policy page, and then click **OK**.

    To get the URL of the privacy policy page, go to **Pages**, go to the privacy policy page, and copy the URL from the properties pane.

1. Save the fragment, check it in, and publish it.
1. Preview the fragment, and test the link to the privacy policy page.

The fragment can now be referenced in the template for other site pages. When this fragment is referenced in the **Footer** module of a template, the link reference will appear on any pages that are built by using that template.

## Additional resources

[Compliance overview](compliance-overview.md)

[Accessibility features and capabilities](accessibility.md)

[Cookie compliance](cookie-compliance.md)
