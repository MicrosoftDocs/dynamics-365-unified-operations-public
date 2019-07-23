---
# required metadata

title:Add a Privacy Policy
description: This topic reviews setting up a Privacy Policy page within Dynamics 365 e-Commerce.
author: BrianShook
manager: BrendanSullivanMSFT
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---

# Add a Privacy Policy

Applies to Dynamics 365 e-Commerce Privacy Policy and building a Privacy Policy for your site.

Privacy compliance includes organizational measures or transparency to data subjects on how their data is collected and handled. This information empowers users to act on how they want their personal data to be handled.

## Dynamics 365 e-Commerce's Privacy Policy

As a user of the Dynamics 365 e-Commerce Authoring Tools, you can review Microsoft's Privacy Policy by the following:

- At any time while logged in to Dynamics 365 e-Commerce Authoring Tools, look for the question mark (?) icon in the top-right corner.
- Click the question mark icon to drop down the context menu and select "Privacy and cookies".
- A new tab will launch with a link to the [**Microsoft Privacy Statement**](https://privacy.microsoft.com/en-US/privacystatement). 



## Building a Privacy Policy page for your site

With Dynamics 365 e-Commerce, there are a number of ways to provide users of your site access to your Privacy Policy. This section will review building a Privacy Policy page and referencing the page using a Footer Fragment.

### Building a Privacy Page

In the e-Commerce Authoring Tools, navigate to the Site you will be building the Privacy Policy page. Then perform the following:

#### Create a Master Template

- If you already have a Master Template created that can be utilized for your Privacy Page, skip ahead to the **Build a Privacy Page** section.
- Select "New Master Template" and name your template to reference for your Privacy Page.  
- Add any required modules to the necessary page slots within the template.
  - Example: The HTML Head slot may require a module, like the 'Default External Script Module'
- In the **Body** slot, add a 'Default Page' module.
- Within the **Main Slot** of the Default Page, add a 'Content Rich Block' module.
- Next, add a 'Content rich block item' to the Content Rich Block module.
- Check-In and then Publish your Master Page.



#### Build a Privacy Page

- Navigate back to the Main page and select the Pages section in the navigation menu.
- Select 'New Page', and select your Privacy Page Master Template.  Provide a name and URL for your Privacy Page. 
- In the **Main Slot** of your Default Page, add a 'Content Rich Block' module.
- Add a 'Content rich block item' to your Content Rich Block module.
- In the Properties panel of the Content rich block item, click on "Add Data Source" and select "RICH TEXT CONTENT".
- Enter your information in the Rich Text Editor. Use the expand icon to bring the Rich Text Editor into full screen mode if needed.
- Once completed, use the "Preview" button to preview the page in the Browser.
- Complete any remaining additions to the page and module properties.
- Check-in and then Publish your Privacy Page.
- Navigate to **Main** and then to the **URLs** section. Find the URL/Page reference in the URLs list for the site.
- Select and Publish the URL item for the page.

#### Create a link to the Privacy Page

A reference page such as a Privacy Page can be created in a page fragment and easily utilized or updated across multiple sites using the fragment. For this example, we will use a Footer fragment to link to the Privacy Page created.

- Navigate to the Fragments section on the navigation pane.
- Select 'New Page Fragment', choosing the 'Footer' module and providing a fragment name.
- Under the **sub footer** slot, add a 'sub footer' module.
- Click 'Add Data Source' in the Sub footer Properties panel and choose 'Links'.
- Add the **Link Text** to set the label text of the link; and set the **Url of content** to the URL of the Privacy Page created.
  - **Note:** Navigate to the Privacy Page created in the **Pages** section and reference the URL from the Page Properties panel.
- Save the fragment, Check-in, and then publish.
- Preview the fragment and test the link to the Privacy Policy page.
- This fragment can now be referenced in a Master Template for other site pages. Referencing this fragment in the footer module of the Master Template will include the link reference in any pages built with the Master Template.

### Summary

This is a very basic example of how a Privacy Page can be created and easily referenced across site pages. The e-Commerce Authoring Tools can be utilized to build reference pages such as a Privacy Page as full featured as needed for your company.

## Additional References

- [GDPR: Rights of the data subject](https://gdpr.eu/tag/chapter-3/)

