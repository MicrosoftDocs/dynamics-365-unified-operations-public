---
# required metadata

title: Embed third-party apps 
description: This topic explains how to embed third-party apps to augment the product's functionality.
author: jasongre
ms.date: 04/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  DefaultDashboard, UserWorkspaceAdd, UserWorkspaceConfigureWebsite
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jasongre
ms.search.validFrom: 2018-02-28
ms.dyn365.ops.version: Platform update 33
---

# [Preview] Embed third-party apps

[!include [banner](../includes/banner.md)]

## Overview 

Many customers utilize a range of applications to run their business including applications that work in conjunction with Finance and Operations apps. To provide a more seamless user experience, you can directly embed those third-party web apps (given that those apps allow themselves to be embedded) within your Finance and Operations apps via the **(Preview) Full page apps** feature. This allows users to access the websites and apps they need without having to switch tabs or windows. 

Before you can embed a third-party app into the product, you must first enable the **(Preview) Full page apps** feature in Feature management. Once enabled, you can choose one of two ways to embed a third-party app or **website** into the product. These are analagous to embedding canvas apps from Power Apps into Finance and Operations apps.

1. Embed as a new tab page (pivot tab, fast tab, blade, or workspace section) in an existing page. 
2. Create a new full-page experience for the app from the dashboard.

## Embedding a website into an existing page

You may want to supplement an existing page in the system with an embedded app. You can accomplish through using the following procedure:
 
1.  Go to the page where you want to embed the app. 

2.  Open the **Add an app** pane.
    - Open the personalization toolbar by selecting **Settings** and then **Personalize**.  
    - Under the **More** button, choose **Add an app**.  
    - Select the region of the page where you would like to add the app. This must be a *tab container* for a pivot tab, FastTab, blade, or workspace section. 

3.  Select **Website** 

4.  Configure the embedded app.
    - The **Name** field indicates the text shown for the tab that will contain the embedded app. Oftentimes, you may want to repeat the name of the app for this field.
    - The **URL** field specifies the location of the application.
        -  For security reasons, the URL must use Hypertext Transfer Protocol Secure (HTTPS)
        -  The app or website must be configured to allow itself to be embedded. 

5.  Select  **Save** to embed the app on the page. 
6.  The app will be added as the last tab or section in the group. Confirm that the app is displaying as expected. If the app does not render, see the [Troubleshooting][#troubleshooting] section below. 
    
7.  Open the view selector and select **Save** or **Save as...** depending on whether this app should be associated with the current view or if you want to save this app to a different view.  
    -  If the page doesn't have a view selector (e.g. a dialog page or a workspace), then you can skip this step. 

## Embedding a website as a full-page experience from the dashboard

If the app you want to embed is not related to an existing page, or you just want a full-page experience for the app inside of the Finance and Operations app, you can use the  following procedure. 

1.  Go to the dashboard
2.  Right-click on the page, select **Personalize**, and then select **Add a page**. 
3.  In the **Add a page** pane, select **Website**.
4.  Configure the embedded app.
    - The **Name** field indicates the text shown on the tile added to the dashboard for this embedded app. Oftentimes, you may want to repeat the name of the app for this field.
    - The **URL** field specifies the location of the application.
        -  For security reasons, the URL must use Hypertext Transfer Protocol Secure (HTTPS)
        -  The app or website must be configured to allow itself to be embedded. 
5.  Select **Save** to add the app as a new tile on the dashboard. 
6.  Select the new tile on the dashboard and confirm that the app is displaying as expected. If the app does not render, see the [Troubleshooting][#troubleshooting] section below.

## Sharing an embedded app

After you've embedded an app using either of the two approaches mentioned above, you may want to share the view with other users in the system. To share an embedded canvas app, choose one of these options.

-  [Recommended] **Publish the view**: When the embedded app has been saved to a view, the recommended and preferred sharing approach is to **publish** the view to users in the appropriate security role(s). This approach ensures that all users who have the security roles targeted by the published view will see the app in Finance and Operations apps. See the **Published views** section  in the [Saved views](saved-views.md#publishing-views) article for more details on how to publish a view.
    - You can also publish app that have been embedded as a full-page experience from the dashboard by right-clicking on the corresponding tile from the dashboard, selecting **Personalize**, and then selecting **Publish page**. Note that this publish option only allows publishing to security roles. The ability to publish to legal entities will be added before the feature becomes generally available.  

-  **Copy the personalization**: For forms that do not support views (e.g. dialogs, workspaces) or for the full-page app experience, you can **copy** the personalization to the appropriate users. See the **Sharing personalizations** section in the [Personalize the user experience](personalize-user-experience.md#sharing-personalizations) article for more details. 

## Viewing an embedded app

To view an embedded app on a page in Finance and Operations apps, navigate to the page that has an embedded app. Remember that on some pages, embedded apps can be accessed by using the **Power Apps** button on the standard Action Pane, or they may directly on the page as a new tab, or FastTab, or blade, or as a new section in a workspace. 

## Editing or removing an embedded app

After an app has been embedded onto a page, you may need to make some changes to the configuration of the app (e.g. modify the section label or the URL) or remove it from the page. Follow the appropriate steps below to edit the configuration of an embedded app or remove it entirely:

### Apps embedded in existing pages
1.  Navigate to the page where the app is located.
2.  Select **Settings** and then **Personalize** to open the personalization toolbar. 
3.  With the **Select** tool chosen, click the embedded app. 
4  If editing the app, make the needed modifications to the app configuration, and then select **Save**.
5.  If deleting the app, select **Delete**.
6.  Re-save or re-publish the view. Note if you leave the page without explicitly saving the view, the actions taken in the **Edit website** pane will not be maintained.  

### Apps embedded from the dashboard
1.  Navigate to the dashboard
2.  Right-click on the tile associated with the app, select **Personalize**
3.  To edit the embedded app, select **Edit page**. 
    -  On the **Edit website** pane, make the desired modifications to the app configiration and then select **Save** 
5.  To remove the embedded app, select **Remove page**.

## Appendix

### Troubleshooting

If the website isn't rendering correctly after being embedded in a Finance and Operation app, this usually indicates that the website is configured to restrict itself from being embedded in an iframe. To confirm this, do the following: 

1. Open the developer tools for the browser you are using. 
2. Switch to the **Network** tab
3. Look for the response from the embedded site. 
4. With that response highlighted, look in **Headers > Response headers** for x-frame-options. 

If x-frame-options exists in the response headers with a value of DENY or SAMEORIGIN, then the website cannot currently be embedded. You will need to work with the owner of the app to safely allow it to be embedded.  

### [Developer] Modeling a website on a form
While this topic focuses on embedding third-party apps or websites through personalization, developers also have the option to embedding these apps to a form using the Visual Studio development experience. To do this, simply add a WebsiteHostControl to the form. The metadata properties available on the control provide the same capabilities as the personalization experience.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
