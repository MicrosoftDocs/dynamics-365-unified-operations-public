---
# required metadata

title: Add a privacy policy
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

# Add a privacy policy

This topic describes how to add a privacy policy page to your site in Dynamics 365 Commerce.

## Overview

Privacy compliance includes organizational measures that inform site users on how their data is collected and handled. This information empowers users to then act on how they want their personal data to be handled.

## Review Microsoft's privacy policy in Dynamics 365 Commerce

To review Microsoft's Privacy Policy while logged into Dynamics 365 Commerce Authoring Tools, do the following.

- Click the question mark icon in the top-right corner and select **Privacy and cookies** from the drop down menu. 

A new tab will launch with a link to the [Microsoft Privacy Statement](https://privacy.microsoft.com/en-US/privacystatement). 

## Build a privacy policy page for your site

With Dynamics 365 Commerce, there are a number of ways to provide users of your site access to your privacy policy. This section will review building a privacy policy page and referencing the page using a footer fragment.

### Build a Privacy Page

In Dynamics 365 Commerce Authoring Tools, navigate to the site you will be building the privacy policy page. Then perform the following:

#### Create a Master Template

- If you already have a master template created that can be utilized for your privacy page, skip ahead to the **Build a Privacy Page** section.
- Select "New Master Template" and name your template to reference for your Privacy Page.  
- Add any required modules to the necessary page slots within the template.
  - Example: The HTML Head slot may require a module, like the 'Default External Script Module'
- In the **Body** slot, add a 'Default Page' module.
- Within the **Main Slot** of the Default Page, add a 'Content Rich Block' module.
- Next, add a 'Content rich block item' to the Content Rich Block module.
- Check-In and then Publish your Master Page.

#### Build a Privacy Page

1. Navigate back to the Main page and select the Pages section in the navigation menu.
1. Select 'New Page', and select your Privacy Page Master Template.  Provide a name and URL for your Privacy Page. 
1. In the **Main Slot** of your Default Page, add a 'Content Rich Block' module.
1. Add a 'Content rich block item' to your Content Rich Block module.
1. In the Properties panel of the Content rich block item, click on "Add Data Source" and select "RICH TEXT CONTENT".
- Enter your information in the Rich Text Editor. Use the expand icon to bring the Rich Text Editor into full screen mode if needed.
- Once completed, use the "Preview" button to preview the page in the Browser.
- Complete any remaining additions to the page and module properties.
- Check-in and then Publish your Privacy Page.
- Navigate to **Main** and then to the **URLs** section. Find the URL/Page reference in the URLs list for the site.
- Select and Publish the URL item for the page.

#### Create a link to the privacy page

A reference page such as a privacy page can be created in a page fragment and easily utilized or updated across multiple sites using the fragment. For this example, we will use a footer fragment to link to the privacy page created.

1. Navigate to the Fragments section on the navigation pane.
1. Select 'New Page Fragment', choosing the 'Footer' module and providing a fragment name.
1. Under the **sub footer** slot, add a 'sub footer' module.
1. Click 'Add Data Source' in the Sub footer Properties panel and choose 'Links'.
1. Add the **Link Text** to set the label text of the link; and set the **Url of content** to the URL of the Privacy Page created.
  - **Note:** Navigate to the Privacy Page created in the **Pages** section and reference the URL from the Page Properties panel.
1. Save the fragment, Check-in, and then publish.
1. Preview the fragment and test the link to the Privacy Policy page.
1. This fragment can now be referenced in a Master Template for other site pages. Referencing this fragment in the footer module of the Master Template will include the link reference in any pages built with the Master Template.

### Summary

This is a very basic example of how a Privacy Page can be created and easily referenced across site pages. The e-Commerce Authoring Tools can be utilized to build reference pages such as a Privacy Page as full featured as needed for your company.

## Additional References

- [GDPR: Rights of the data subject](https://gdpr.eu/tag/chapter-3/)

