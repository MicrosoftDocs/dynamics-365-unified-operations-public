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

Many customers utilize a range of applications to run their business including applications that work in conjunction with Finance and Operations apps. To help provide a more seamless user experience, you can directly embed those third-party web apps within your Finance and Operations apps via the **(Preview) Full page apps** feature . This allows users to access the websites and apps they need without having to switch tabs or windows. 




## Adding an embedded canvas app from Power Apps to a page




### Overview

Before you can embed a third-party app into the product, you must first enable the **(Preview) Full page apps** feature in Feature management. Once enabled, you can choose one of two ways to embed a third-party app or **website** into the product. These are analagous to embedding canvas apps from Power Apps into Finance and Operations apps.

1. Embed as a new tab page (pivot tab, fast tab, blade, or workspace section) in an existing page. 
2. Create a new full-page experience for the app from the dashboard.

### Details

The following procedure shows how to embed a website into an existing page.

1. Go to the page where you want to embed the app. 

2. Open the **Add an app** pane.
    - Open the personalization toolbar by selecting **Settings** and then **Personalize**.  
    - Under the **More** button, choose **Add an app**.  
    - Select the region of the page where you would like to add the app. This must be a *tab container* for a pivot tab, FastTab, blade, or workspace section. 

3. Select **Website** 

4. Configure the embedded app.
    - The **Name** field indicates the text shown for the tab that will contain the embedded app. Oftentimes, you may want to repeat the name of the app for this field.
    - The **URL** field specifies the location of the application.
        -  https
        -  webiste must allow itself to be embedded (xframe options) 
        -  
4. After confirming that the configuration is correct, click **Save** to embed the app on the page. 
5. The app will be added as the last tab or section in the group. Confirm that the app is displaying as expected.  If the app is not shown, see the Troubleshooting section below.  
6. Open the view selector and select **Save** or **Save as...** depending on whether this app should be associated with the current view or if you want to save this app to a different view.  
    -  If the page doesn't have a view selector (e.g. a dialog page or a workspace), then you can skip this step. 

## Sharing an embedded app

After you've saved a view with an embedded app and confirmed that the app is displaying correctly, you may want to share the view with other users in the system. To share an embedded canvas app, choose one of these options.

-  **Publish** the view to the users in the desired security role(s). This approach ensures that all users who have the security roles that are targeted by the published view will see the app in Finance and Operations apps. See [] for more details on how to publish a view.

-  For forms that do not support views (e.g. dialogs, workspaces), **copy** the personalization to the appropriate users. See [Personalize the user experience](personalize-user-experience.md) for more details. 
   

## Viewing a canvas app

To view an embedded canvas app on a page in Finance and Operations apps, just go to a page that has an embedded app. Remember that apps can be accessed by using the **Power Apps** button on the standard Action Pane. Alternatively, they can appear directly on the page as a new tab, or FastTab, or blade, or as a new section in a workspace. When users first try to load an app on a page, they will be prompted to sign in. This step ensures that the users have the appropriate permissions to use the app.

## Editing or removing an embedded app

After an app has been embedded onto a page, you may need to make some changes to the configuration of the app (e.g. modify the section label or the URL) or remove it from the page. Follow these steps to edit the configuration of an embedded app or remote it entirely:

1. Navigate to the page where the app is located.
2. Select **Settings** and then **Personalize** to open the personalization toolbar. 
3. With the **Select** tool chosen, click the embedded app. 
4. If editing the app, make the needed modifications to the app configuration, and then select **Save**.
5. If deleting the app, select **Delete**.
6. Re-save or re-publish the view. Note if you leave the page without explicitly saving the view, the actions taken in the **Edit website** pane will not be maintained.  

## Appendix

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
