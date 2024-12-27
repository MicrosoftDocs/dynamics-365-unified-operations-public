---
title: Embed canvas apps from Power Apps
description: Learn about how to embed canvas apps from Microsoft Power Apps into the client to augment the product's functionality.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/27/2024
ms.reviewer: twheeloc
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-02-28
ms.search.form:  FormRunConfigurationAddPAControl, FormRunConfigurationEditPAControl
ms.custom: 
  - bap-template
---

# Embed canvas apps from Power Apps

[!include [banner](../../../finance/includes/banner.md)]

Microsoft Power Apps is a service that lets developers and nontechnical users build custom business apps for mobile devices, tablets, and the web without writing code. Finance and operations apps support integration with Power Apps. Canvas apps that you, your organization, or the broader ecosystem develop can be embedded into finance and operations apps to augment the product's functionality. For example, you might build a canvas app from Power Apps to supplement a finance and operations app with information that is retrieved from another system.

To learn more about embedding canvas apps, watch the short [How to embed canvas apps](https://www.youtube.com/watch?v=x3qyA1bH-NY) video.

## Adding an embedded canvas app from Power Apps to a page

Before you embed a canvas app from Power Apps into the client, you must find or build an app that has the desired visuals or functionality. This article doesn't include a detailed description of the process for building apps. If you're new to Power Apps, see the [Power Apps documentation](/powerapps/).

There are three ways to embed a canvas app into a finance and operations app. You can use the approach that best fits your scenario. 

- Embed the canvas app into the **Power Apps** button on the standard Action Pane of a page. Apps that you add in this way appear as items on the **Power Apps** menu button, and the apps open in side panes. 
- Embed the canvas app directly on an existing page as a new tab page (pivot tab, FastTab, blade, or workspace section).
- Create a new full-page experience for the canvas app from the dashboard.

When you configure your embedded canvas app, you can select a single field that you want to send as context to the app. This step enables the app to be responsive, based on the data that you're currently viewing.

> [!NOTE]
> You can't use this mechanism to embed model-driven apps.

### Embedding a canvas app on an existing page

The following procedure shows how to embed a canvas app on an existing page from Power Apps.

1. Go to the page where you want to embed the canvas app. This page contains any data that must be passed to the app as input.
2. Open the **Add an app from Power Apps** pane:

    - If the app will be embedded directly on the page, select **Options** \> **Personalize this page** \> **More**. Select **Add a page**, and then select the region on the page where you want to add the app. To embed the app into the **Power Apps** menu button, on the Action Pane select **Power Apps**. To embed the app directly on the page, select the appropriate tab, FastTab, blade, or section (if you're on a workspace). Then, in the **Add an app** pane, select **Power Apps**.
    - If the app will be accessed by using the **Power Apps** menu button, you can select the **Power Apps** menu button on the standard Action Pane and then select **Add an app**.

3. Configure the embedded app. For more information, see the [Configuring a canvas app](#configuring-a-canvas-app) section later in this article.
4. After you confirm that the configuration is correct, select **Insert**. Remember to save the view for the change to be persisted if you're adding the app to a page that supports views. 

### Embedding a canvas app as a full-page experience from the dashboard

You might want to embed a canvas app from the dashboard if the app isn't related to an existing page, or if you just want to surface the app as a full-page experience inside the finance and operations app.

1. Open the dashboard.
2. Select and hold (or right-click) the page, select **Personalize**, and then select **Add a page**.
3. In the **Add a page** pane, select **Power Apps**.
4. Configure the embedded app. For more information, see the [Configuring a canvas app](#configuring-a-canvas-app) section later in this article.
5. Select **Save** to add the app to the dashboard as a new tile.
6. Select the new tile on the dashboard, and confirm that the canvas app appears as expected.

### Configuring a canvas app

When you embed a canvas app, you must set the following parameters:

- **Name** – Enter the text that should be shown for the button or tab that contains the embedded app. Often, you might want to repeat the name of the app in this field.
- **App ID** – Specify the globally unique identifier (GUID) for the canvas app that you want to embed. To retrieve this value, find the app on [make.powerapps.com](https://make.powerapps.com), and then look in the **App ID** field under **Details**.
- **Input context for the app** – You can optionally select the field that contains the data that you want to pass to the app as input. For information about how the app can access the data that is sent from finance and operations apps, see [Building an app that leverages data sent from finance and operations apps](#building-a-canvas-app-that-uses-data-that-is-sent-from-finance-and-operations-apps).

    The current legal entity is also passed to the canvas app as context, via the **cmp** URL parameter. 

- **Application size** – Select the type of app that you're embedding. Select **Thin** for apps that are built for mobile devices or **Wide** for apps that are built for tablets. This parameter ensures that enough space is allotted for the embedded app.

## Sharing an embedded app

After you embed a canvas app on a page and confirmed that it's working correctly, you might want to share the app with other users in the system. 

To share an embedded canvas app, follow these steps.

1. [Share the canvas app in Power Apps](/powerapps/maker/canvas-apps/share-app) with the appropriate users, so that they can access the app directly in Power Apps.
2. Share the personalizations that are associated with the embedded app with the desired users. You can use either of the following approaches:

    - **Publish the view (Recommended):** For pages that support views, the recommended and preferred approach is to create a view that includes the embedded canvas app, and then publish that view to the desired users. This approach ensures that all users who have the security roles that are targeted by the published view see the canvas app on the page.

        You can also publish a canvas app that is embedded as a full-page experience from the dashboard. On the dashboard, select and hold (or right-click) the tile that is associated with the app, select **Personalize**, and then select **Publish page**. An experience that resembles the *Publishing views* experience is shown, and you can select the security roles and legal entities to publish to.

    - For pages that don't support views, the system administrator can implement a personalization that provides the canvas app to the appropriate set of users via the **Personalization** page. Alternatively, you can export your page's personalizations and send them to one or more users. Each of those users can then import the personalization. The personalization toolbar has buttons that let you export and import personalizations.

> [!NOTE]
> If the canvas app has been shared with external users, those users can't use the embedded app inside finance and operations apps. However, they can access the app directly inside Power Apps. External users include guests and users who don't belong to the Microsoft 365 Azure Directory where the finance and operations app is deployed.

For more information about the personalization capabilities in the product and how to use them, see [Personalize the user experience](personalize-user-experience.md).

## Building a canvas app that uses data that is sent from finance and operations apps

When you build a canvas app that will be embedded in a finance and operations app, one important part of the process is to use the input data from that finance and operations app. From the Power Apps development experience, the input data that is passed from a finance and operations app can be accessed by using the **Param("EntityId")** variable. The current legal entity is also passed to the canvas app via the **Param("cmp")** variable. 

For example, in the OnStart function of the app, you could set the input data from finance and operations apps to a variable like this:

``` Power Apps
If(!IsBlank(Param("EntityId")), Set(FinOpsInput, Param("EntityId")), Set(FinOpsInput, ""));

If(!IsBlank(Param("cmp")), Set(FinOpsLegalEntity, Param("cmp")), Set(FinOpsLegalEntity, ""));
```

## Viewing a canvas app

To view an embedded canvas app on a page in finance and operations apps, just go to a page that has an embedded app. Remember that apps can be accessed by using the **Power Apps** button on the standard Action Pane. Alternatively, they can appear directly on the page as a new tab, or FastTab, or blade, or as a new section in a workspace. When users first try to load an app on a page, they are prompted to sign in. This step ensures that the users have the appropriate permissions to use the app.

## Editing an embedded app

After an app is embedded on a page, you may need to make some changes to the configuration of the app. For example, you may want to modify the label that is associated with the embedded app, or a new version of the app is released and you need to update the App ID to point to the latest version.

Follow these steps to edit the configuration of an embedded app:

1. Go to the **Edit the app** pane.

    - If the embedded app is accessed through the Power Apps menu button, select and hold (or right-click) the Power Apps menu button and select **Personalize**. Select the app that you want to configure from the **Select an app** drop-down menu.
    - If the embedded app appears directly on the page, select **Options**, and then select **Personalize this page**. Using the **Select** tool, click the embedded app.
    - If the embedded app was added from the dashboard, open the dashboard, select and hold (or right-click) the tile that is associated with the canvas app, select **Personalize**, and then select **Edit page**.

2. Make the needed modifications to the app configuration, and then click **Save**.
3. Resave or republish the view. If you leave the page without explicitly saving the view, none of the actions that you performed in the **Edit website** pane are maintained. This step isn't needed for pages that don't support views.  
   
## Removing an app

After an app is embedded on a page, there are a few ways to remove it if needed:

- Go to the **Edit an app** pane using the instructions from the [Editing an embedded app](#editing-an-embedded-app) section earlier in this article. Confirm that the pane displays information for the embedded app that you would like to remove, and then click the **Delete** button.
- If the embedded app was added from the dashboard, open the dashboard, select and hold (or right-click) the tile that is associated with the canvas app, select **Personalize**, and then select **Remove page**. 
- Because the embedded app is saved as personalization data, clearing your page's personalization also removes any embedded apps on that page. Clearing the page's personalization is permanent and can't be undone. To remove your personalizations on a page, select **Options**, select **Personalize this page**, and then select the **Clear** button. After you refresh your browser, all previous personalizations for the current view (or the entire page if the page doesn't support views) are removed. For more information about how to optimize pages using personalization, see [Personalize the user experience](personalize-user-experience.md).

## Appendix

### [Developer] Modeling a canvas app on a form

While this article focuses on embedding canvas apps through personalization, developers also have the option to add a canvas app to a form using the Visual Studio development experience by adding a PowerAppsHostControl to the form. The metadata properties available on the control provide the same capabilities as the personalization experience.

### [Developer] Specifying where an app can be embedded

By default, users can embed apps on any page, either under the Power Apps menu button or directly on the page as a tab, FastTab, blade or as a new section in a workspace. However, if necessary developers can also configure this feature to only allow embedding of apps on certain pages by implementing the following methods:

- **isPowerAppPersonalizationEnabled** – If this method returns false for a specific page, then the Power Apps menu button isn't shown, and users aren't able to embed apps anywhere on this page, including as a tab.
- **isPowerAppTabPersonalizationEnabled** – If this method returns false for a specific page, then users aren't able to embed apps directly on the page as a tab, FastTab, or panorama section. Users are still able to embed apps through the Power Apps menu button if embedding is allowed on the page.

The following example shows a new class with the two methods needed to configure where apps can be embedded.

```powerapps
[ExtensionOf(classStr(FormRunConfigurationPowerAppsConfiguration))]

public final class ClassTest_Extension
{
    public static boolean isPowerAppPersonalizationEnabled(str pageName)
    {
        var result = next isPowerAppPersonalizationEnabled(pageName);
        return result;
    }
    
    public static boolean isPowerAppTabPersonalizationEnabled(str pageName)
    {
        var result = next isPowerAppTabPersonalizationEnabled(pageName);
        return result;
    }
}
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

