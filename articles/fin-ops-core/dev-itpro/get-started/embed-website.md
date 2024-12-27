---
title: Embed third-party apps 
description: This article explains how to embed third-party apps to augment the product's functionality, including an overview on embedding wesites on existing pages.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/27/2024
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-04-30
ms.search.form: DefaultDashboard, UserWorkspaceAdd, UserWorkspaceConfigureWebsite
ms.custom: 
  - bap-template
---

# Embed third-party apps

[!include [banner](../../../finance/includes/banner.md)]

Many customers use a range of applications to run their businesses. Some of those applications are third-party web apps that work in conjunction with finance and operations apps. To provide a more seamless user experience, you can embed third-party apps directly into your finance and operations apps (provided that the third-party apps allow themselves to be embedded). In this way, users can access the websites and apps they require without having to switch tabs or windows.

Use one of the following methods to embed a third-party app or website. These methods are analogous to the methods that are used to embed canvas apps from Microsoft Power Apps into finance and operations apps.

- Embed the app or website on an existing page as a new tab page (pivot tab, FastTab, blade, or workspace section).
- Create a new full-page experience for the app or website from the dashboard.

## Embed a website on an existing page

Use this procedure if you want to supplement an existing page in the system with an embedded app.

1. Open the page where you want to embed the app.
2. Open the **Add an app** pane:

    1. Select **Settings** and then **Personalize** to open the **Personalization** toolbar.
    2. Select **More \> Add an app**.

3. Select the region of the page where you want to add the app. This region must be a *tab container* for a pivot tab, FastTab, blade, or workspace section.
4. Select **Website**.
5. Configure the embedded app:

    - **Name** – Enter the text that should be shown for the tab that contains the embedded app. Often, you will want this text to be the name of the app.
    - **URL** – Specify the location of the app.

    > [!IMPORTANT]
    > - For security reasons, the URL must use Hypertext Transfer Protocol Secure (HTTPS).
    > - The app or website must be configured to allow itself to be embedded.

6. Select **Save** to embed the app on the page. The app is added as the last tab or section in the group.
7. Confirm that the app appears as expected. If the app isn't rendered, see the [Troubleshooting](#troubleshooting) section later in this article.
8. Open the view selector, and select either **Save** (if the app should be associated with the current view) or **Save as** (to save the app to a different view). If the page doesn't support views, you can skip this step.

## Embed a website as a full-page experience from the dashboard

Use this procedure if the app that you want to embed isn't related to an existing page, or if you just want a full-page experience for the app inside the finance and operations app.

1. Open the dashboard.
2. Select and hold (or right-click) on the dashboard, select **Personalize**, and then select **Add a page**.
3. In the **Add a page** pane, select **Website**.
4. Configure the embedded app:

    - **Name** – Enter the text that should be shown on the tile that is added for the embedded app on the dashboard. Often, you will want this text to be the name of the app.
    - **URL** – Specify the location of the app.

    > [!IMPORTANT]
    > - For security reasons, the URL must use HTTPS.
    > - The app or website must be configured to allow itself to be embedded.

5. Select **Save** to add the app to the dashboard as a new tile.
6. Select the new tile on the dashboard, and confirm that the app appears as expected. If the app isn't being rendered, see the [Troubleshooting](#troubleshooting) section later in this article.

## Sharing embedded apps

After you've embedded an app by using one of the methods that are described in the previous sections, you might want to share the view with other users in the system. To share an embedded app, use one of the following methods:

- **Publish the view (Recommended):** If the embedded app has been saved to a view, the recommended and preferred way to share it is to publish the view to users who have the appropriate security roles in the targeted legal entities. In this case, only the desired users will see the embedded app on that page. For more information about how to publish a view, see [Publishing views](saved-views.md#publishing-views).

    You can also publish an app that has been embedded as a full-page experience from the dashboard. On the dashboard, select and hold (or right-click) the tile that is associated with the app, select **Personalize**, and then select **Publish page**. An experience that resembles the *Publishing views* experience is shown, and you can select the security roles and legal entities to publish to.  

- **Copy the personalization:** For pages that don't support views, you can copy the personalization to the appropriate users. For more information, see [Sharing personalizations](personalize-user-experience.md#share-personalizations).

## Viewing embedded apps

To view an embedded app on a page in finance and operations apps, open the page that has the embedded app. On some pages, embedded Power Apps can be accessed by using the **Power Apps** button on the standard Action Pane. Alternatively, any embedded app might appear directly on the page as a new tab, FastTab, or blade, or as a new section in a workspace.

## Editing or removing embedded apps

After an app has been embedded on a page, you might have to edit its configuration (for example, by changing the section label or the URL). Alternatively, you might have to remove it from the page. Use one of the following procedures to edit the configuration of an embedded app or remove it completely.

### Apps that are embedded on existing pages

1. Open the page where the app is embedded.
2. Select **Settings** and then **Personalize** to open the **Personalization** toolbar.
3. Select the **Select** tool, and then select the embedded app.
4. To edit the app, make the required changes to its configuration, and then select **Save**.

    Alternatively, to remove the app, select **Delete**.

5. Re-save or republish the view. Note that if you leave the page without explicitly saving the view, none of the actions that you performed in the **Edit website** pane will be maintained.

### Apps that are embedded from the dashboard

1. Open the dashboard.
2. Select and hold (or right-click) the tile that is associated with the embedded app, and then select **Personalize**.
3. To edit the app, select **Edit page**. In the **Edit website** pane, make the required changes to the app configuration, and then select **Save**.

    Alternatively, to remove the app, select **Remove page**.

## Appendix

### Troubleshooting

If a website isn't rendered correctly after it's embedded in a Finance and Operation app, or if you receive an error message that states that the URL was denied a connection, the website is probably configured to prevent itself from being embedded in an iframe. Follow these steps to determine whether the website can be embedded.

1. Open the developer tools for the browser that you're using.
2. On the **Network** tab, find and select the response from the embedded site.
3. On the **Headers** tab, under **Response Headers**, look for **x-frame-options**. If **x-frame-options** exists in the response headers, and has a value of **DENY** or **SAMEORIGIN**, the website can't currently be embedded. You will have to work with the owner of the app to enable it to be safely embedded.

### [Developer] Modeling a website on a form

Although this article is focused on embedding third-party apps or websites through personalization, developers can also embed them in a form by using the Visual Studio development experience. Just add a **WebsiteHostControl** control to the form. The metadata properties that are available for the control provide the same capabilities as the personalization experience.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

