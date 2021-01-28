---
# required metadata

title: Embed canvas apps from Power Apps
description: This topic explains how to embed canvas apps from Microsoft Power Apps into the client to augment the product's functionality.
author: jasongre
manager: AnnBe
ms.date: 11/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form:  FormRunConfigurationAddPAControl, FormRunConfigurationEditPAControl
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jasongre
ms.search.validFrom: 2018-02-28
ms.dyn365.ops.version: Platform update 14
---

# Embed canvas apps from Power Apps

[!include [banner](../includes/banner.md)]

Microsoft Power Apps is a service that lets developers and non-technical users build custom business apps for mobile devices, tablets, and the web without writing code. Finance and Operations apps support integration with Power Apps. Canvas apps that you, your organization, or the broader ecosystem develop can be embedded into Finance and Operations apps to augment the product's functionality. For example, you might build a canvas app from Power Apps to supplement a Finance and Operations app with information that is retrieved from another system.

To learn more about embedding Power Apps, watch the short [How to embed Power Apps](https://www.youtube.com/watch?v=x3qyA1bH-NY) video.

## Adding an embedded canvas app from Power Apps to a page

### Overview

Before you embed a canvas app from Power Apps into the client, you must find or build an app that has the desired visuals or functionality. This topic doesn't include a detailed description of the process for building apps. If you're new to Power Apps, see the [Power Apps documentation](https://docs.microsoft.com/powerapps/).

There are two ways to access a specific canvas app on a page when you're ready to embed the app. You can choose whichever approach fits your scenario better. The first approach uses the **Power Apps** button that has been added to the standard Action Pane. Apps that you add by using this approach appear as items on the **Power Apps** menu button. When you select one of these items, a side pane that contains the embedded app appears. Alternatively, you can embed an app directly on a page as a new tab, FastTab, or blade, or as a new section in a workspace.

When you configure your embedded canvas app, you can select a single field that you want to send as context to the app. This step enables the app to be responsive, based on the data that you're currently viewing.

> [!NOTE]
> You can't currently use this mechanism to embed modeled apps.  

### Details

The following procedure shows how to embed a canvas app from Power Apps into the web client.

1. Go to the page where you want to embed the canvas app. This page will be the page that contains data that must be passed to the app as input.
2. Open the **Add an app from Power Apps** pane:

    - Click **Options**, and then select **Personalize this page**. Under the **Insert** menu, choose **Power Apps**. Finally, select the region where you would like to add the app. If you want to embed the app under the Power Apps menu button, choose the Action Pane. If you want to embed the app directly onto the page, choose the appropriate tab, FastTab, blade, or section (if you're on a workspace).
    - If the app will be accessed using the Power Apps menu button, you can alternatively click the **Power Apps** menu button in the standard Action Pane, and then select **Add an app**.

3. Configure the embedded app:

    - The **Name** field indicates the text shown for the button or tab that will contain the embedded app. Oftentimes, you may want to repeat the name of the app in this field.
    - The **App ID** field indicates the globally unique identifier (GUID) for the canvas app that you want to embed. To retrieve this value, find the app on [make.powerapps.com](https://make.powerapps.com), and then look in the **App ID** field under **Details**.
    - For **Input context for the app**, you can optionally select the field that contains the data that you want to pass to the app as input. See the section later in this topic titled [Building an app that leverages data sent from Finance and Operations apps](#building-a-canvas-app-that-uses-data-that-is-sent-from-finance-and-operations-apps) for details on how the app can access the data sent from Finance and Operations apps.
    - Choose the **Application size** that matches the type of app that you're embedding. Select **Thin** for apps built for mobile devices, and **Wide** for apps built for tablets. This ensures a sufficient amount of space is allotted for the embedded app.
    - The **Legal entities** FastTab provides the ability to choose which legal entities the app is available for. The default is to make the app accessible to all legal entities. This option is only available when the [Saved views](saved-views.md) feature is disabled. 

4. After confirming that the configuration is correct, click **Insert** to embed the Power App on the page. You will be prompted to refresh the browser in order to see the embedded app.

## Sharing an embedded app

After you've embedded a canvas app on a page and confirmed that it's working correctly with any data context that is passed from that page, you might want to share the app with other users in the system. To share an embedded canvas app, follow these steps.

1. [Share the canvas app](https://docs.microsoft.com/powerapps/maker/canvas-apps/share-app) with the appropriate users, so that they can access the app in Power Apps. 

2. Make sure that the targeted users have the appropriate personalizations, so that the embedded app appears when those users view the page. You can use either of the following approaches:

    - Recommended: Use the [Saved views](saved-views.md) feature to create and publish a view that includes the embedded app. This approach ensures that all users who have the security roles that are targeted by the published view will see the app in Finance and Operations apps. 
    - If you don't have the Saved views feature turned on, you can have the system admin push a personalization that includes the embedded app to all users or a subset of users. Alternatively, you can export your page's personalizations, and send them to one or more users. Each of those users can then import the personalizations. The personalization toolbar has actions that let you export and import personalizations. 
    
> [!NOTE]
> If the canvas app has been shared with external users, those users can't use the embedded app inside Finance and Operations apps. However, they can access the app directly inside Power Apps. External users include guests and users who don't belong to the Microsoft 365 Azure Directory where the Finance and Operations app is deployed.

See [Personalize the user experience](personalize-user-experience.md) for more details about the personalization capabilities in the product and how to use them.

## Building a canvas app that uses data that is sent from Finance and Operations apps

When you build a canvas app that will be embedded in a Finance and Operations app, one important part of the process is to use the input data from that Finance and Operations app. From the Power Apps development experience, the input data that is passed from a Finance and Operations app can be accessed by using the **Param("EntityId")** variable.

For example, in the OnStart function of the app, you could set the input data from Finance and Operations apps to a variable like this:

```powerapps
If(!IsBlank(Param("EntityId")), Set(FinOpsInput, Param("EntityId")), Set(FinOpsInput, ""));
```

## Viewing a canvas app

To view an embedded canvas app on a page in Finance and Operations apps, just go to a page that has an embedded app. Remember that apps can be accessed by using the **Power Apps** button on the standard Action Pane. Alternatively, they can appear directly on the page as a new tab, or FastTab, or blade, or as a new section in a workspace. When users first try to load an app on a page, they will be prompted to sign in. This step ensures that the users have the appropriate permissions to use the app.

## Editing an embedded app

After an app has been embedded onto a page, you may need to make some changes to the configuration of the app. For example, perhaps you want to modify the label associated with the embedded app or a new version of the app has been created and you need to update the App ID to point at the latest.

Follow these steps to edit the configuration of an embedded app:

1. Go to the **Edit the app** pane.

    - If the embedded app is accessed through the Power Apps menu button, right-click on the Power Apps menu button and select **Personalize**. Select the app that you want to configure from the **Select an app** drop-down menu.
    - If the embedded app appears directly on the page, select **Options**, and then select **Personalize this page**. Using the **Select** tool, click the embedded app.

2. Make the needed modifications to the app configuration, and then click **Save**.

## Removing an app

After an app has been embedded onto a page, there are two ways to remove it if needed:

- Go to the **Edit an app** pane using the instructions from the [Editing an embedded app](#editing-an-embedded-app) section earlier in this topic. Confirm that the pane displays information for the embedded app that you would like to remove, and then click the **Delete** button.
- Because the embedded app is saved as personalization data, clearing your page's personalization will also remove any embedded apps on that page. Note that clearing the page's personalization is permanent and cannot be undone. To remove your personalizations on a page, select **Options**, and then **Personalize this page**, and finally the **Clear** button. After refreshing your browser, all the previous personalizations for this page will be removed. See [Personalize the user experience](personalize-user-experience.md) for more information about how to optimize pages using personalization.

## Appendix

### [Developer] Specifying where an app can be embedded

By default, users can embed apps on any page, either under the Power Apps menu button or directly on the page as a tab, FastTab, blade or as a new section in a workspace. However, if required, developers can also configure this feature to only allow embedding of apps on certain pages by implementing the following methods:

- **isPowerAppPersonalizationEnabled** – If this method returns false for a specific page, then the Power Apps menu button will not be shown, and users will not be able to embed apps anywhere on this page, including as a tab.
- **isPowerAppTabPersonalizationEnabled** – If this method returns false for a specific page, then users will not be able to embed apps directly on the page as a tab, FastTab, or panorama section. Users will still be able to embed apps through the Power Apps menu button if embedding is allowed on the page.

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
