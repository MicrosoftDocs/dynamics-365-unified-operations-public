---
# required metadata

title: Embed Power Apps
description: This topic describes how to embed Power Apps into the client to augment the product's functionality.
author: jasongre
manager: AnnBe
ms.date: 12/02/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form:  FormRunConfigurationAddPAControl, FormRunConfigurationEditPAControl
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jasongre
ms.search.validFrom: 2018-02-28
ms.dyn365.ops.version: Platform update 14
---

# Embed Microsoft Power Apps

[!include [banner](../includes/banner.md)]

Platform update 14 supports integration with Microsoft Power Apps, a service for developers and non-technical users to build custom business apps for mobile devices, tablets, and the web without writing code. Power Apps developed by you, your organization, or the broader ecosystem can then be embedded in the Finance and Operations apps to augment the product's functionality. For example, you might build a Power App to supplement Finance and Operations apps with information retrieved from another system.

To learn more about embedding Power Apps, watch the short [How to embed Power Apps](https://www.youtube.com/watch?v=x3qyA1bH-NY) video.

## Adding an embedded Power App to a page

### Overview

Before embedding a Power App into the client, you first need to find or build a Power App with the desired visuals and/or functionality. We will not describe the detailed process for building a Power App here. The [Introduction to Power Apps](https://docs.microsoft.com/powerapps/getting-started) topic is a good starting point if you are new to Power Apps.

When you are ready to embed a specific Power App, you can choose between one of two ways of accessing the Power App on a page, whichever route better fits your scenario. The first way is through the Power Apps button that has been added to the standard Action Pane. Power Apps added using this mechanism will appear as menu items inside the Power Apps menu button. When selected, each of these menu items will open a side pane that contains the embedded Power App. Alternatively, you may choose to show a Power App directly on a page as a new tab, FastTab, blade, or as a new section in a workspace.

When configuring your embedded Power App, you can select a single field that you want to send as input to the Power App. This allows the Power App to be responsive based on the data that you are currently viewing.

### Details

The following instructions show how to embed a Power App into the web client.

1. Go to the page where you would like to embed the Power App. This will be the same page that contains any data that needs to be passed to the Power App as input.
2. Open the **Insert a Power App** pane:

    - Click **Options**, and then select **Personalize this form**. Under the **Insert** menu, choose **Power App**. Finally, select the region where you would like to add the Power App. If you want to embed the Power App under the Power Apps menu button, choose the Action Pane. If you want to embed the Power App directly onto the page, choose the appropriate tab, FastTab, blade, or section (if you're on a workspace).
    - If the Power App will be accessed using the Power Apps menu button, you can alternatively click the **Power Apps** menu button in the standard Action Pane, and then select **Insert a Power App**.

3. Configure the embedded Power App:

    - The **Name** field indicates the text shown for the button or tab that will contain the embedded Power App. Oftentimes, you may want to repeat the name of the Power App in this field.
    - **App ID** is the GUID for the Power App that you want to embed. To retrieve this value, find the Power App on [web.powerapps.com](https://web.powerapps.com) and then locate the **App ID** field under **Details**.
    - For **Input data for the Power App**, you can optionally select the field that contains the data that you want to pass to the Power App as input. See the section later in this topic titled [Building a Power App that leverages data from Finance and Operations apps](#building-a-power-app-that-leverages-data-sent-from-finance-and-operations-apps) for details on how the Power App can access the data sent from Finance and Operations apps.
    - Choose the **Application size** that matches the type of Power App that you're embedding. Select **Thin** for Power Apps built for mobile devices, and **Wide** for Power Apps built for tablets. This ensures a sufficient amount of space is allotted for the embedded Power App.
    - The **Legal entities** FastTab provides the ability to choose which legal entities the Power App is available for. The default is to show the Power App in all legal entities.

4. After confirming that the configuration is correct, click **Insert** to embed the Power App on the page. You will be prompted to refresh the browser in order to see the embedded Power App.

## Sharing an embedded Power App

After you have embedded a Power App on a page and confirmed that it is working correctly with any data context passed from the page, you might want to share this embedded Power App with other users in the system. This can be accomplished in two different ways using the personalization capabilities of the product:

- The recommended scenario is through the system administrator, who can push a personalization to all users or a subset of users.
- Alternatively, you can export your page's personalizations, send them to one or more users, and have each of those users import those changes. The Manage option on the personalization toolbar enables you to export and import personalizations.

See [Personalize the user experience](personalize-user-experience.md) for more details about the personalization capabilities in the product and how to use them.

## Building a Power App that leverages data sent from Finance and Operations apps

An important part of building a Power App that will be embedded in Finance and Operations apps is utilizing the input data from Finance and Operations apps. Inside the Power App, that input data can be accessed using the Param("EntityId") variable.

For example, in the OnStart function of the Power App, you could set the input data from Finance and Operations apps to a variable like this:

```
If(!IsBlank(Param("EntityId")), Set(FinOpsInput, Param("EntityId")), Set(FinOpsInput, ""));
```

## Viewing an embedded Power App

To view an embedded Power App on a page in Finance and Operations apps, simply go to a page with an embedded Power App. Recall that Power Apps can be accessed through the Power Apps button in the standard Action Pane, or can appear directly on the page as a new tab, FastTab, blade, or as a new section in a workspace. When a user first attempts to load a Power App on a page, he or she will be prompted to sign in to Power Apps to ensure the user has the appropriate permissions to use the Power App.

## Editing an embedded Power App

After a Power App has been embedded onto a page, you may need to make some changes to the configuration of that Power App. For example, perhaps you want to modify the label associated with the embedded Power App or a new version of a Power App has been created and you need to update the App ID to point at the latest Power App.

Follow these steps to edit the configuration of an embedded Power App:

1. Go to the **Edit a Power App** pane.

    - If the embedded Power App is accessed through the Power Apps menu button, right-click on the Power Apps menu button and select **Personalize**. Select the Power App that you want to configure from the **Select Power App** drop-down menu.
    - If the embedded Power App appears directly on the page, select **Options**, and then select **Personalize this form**. Using the **Select** tool, click the embedded Power App.

2. Make the needed modifications to the Power Apps configuration, and then click **Save**.

## Removing an embedded Power App

After a Power App has been embedded onto a page, there are two ways to remove it if needed:

- Go to the **Edit a Power App** pane using the instructions from the [Editing an embedded Power App](#editing-an-embedded-power-app) section earlier in this topic. Confirm that the pane displays information for the embedded Power App that you would like to remove, and then click the **Delete** button.
- Because an embedded Power App is saved as personalization data, clearing your page's personalization will also remove any embedded Power Apps on that page. Note that clearing the page's personalization is permanent and cannot be undone. To remove your personalizations on a page, select **Options** and then click **Personalize this form**. Under the **Manage** menu, select the **Clear** button. After refreshing your browser, all the previous personalizations for this page will be removed. See [Personalize the user experience](personalize-user-experience.md) for more information about how to optimize pages using personalization.

## Appendix

### Developer control over where a Power App can be embedded

By default, users can embed Power Apps on any page, either under the Power Apps menu button or directly on the page as a tab, FastTab, blade or as a new section in a workspace. However, if required, developers can also configure this feature to only allow embedding of Power Apps on certain pages by implementing the following methods:

- **isPowerAppPersonalizationEnabled** – If this method returns false for a specific page, then the Power Apps menu button will not be shown, and users will not be able to embed Power Apps anywhere on this page, including as a tab.
- **isPowerAppTabPersonalizationEnabled** – If this method returns false for a specific page, then users will not be able to embed Power Apps directly on the page as a tab, FastTab, or panorama section. Users will still be able to embed Power Apps through the Power Apps menu button if embedding is allowed on the page.

The following example shows a new class with the two methods needed to configure where Power Apps can be embedded.

```
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
