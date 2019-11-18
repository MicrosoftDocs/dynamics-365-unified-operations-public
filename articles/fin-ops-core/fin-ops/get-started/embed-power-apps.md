---
# required metadata

title: Embed Power Apps apps
description: This topic describes how to embed Power Apps into the client to augment the product's functionality.
author: jasongre
manager: AnnBe
ms.date: 09/20/2019
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

# Embed Microsoft Power Apps apps

[!include [banner](../includes/banner.md)]

Platform update 14 supports integration with Microsoft Power Apps, a service for developers and non-technical users to build custom business apps for mobile devices, tablets, and the web without writing code. Power Apps developed by you, your organization, or the broader ecosystem can then be embedded in the Finance and Operations apps to augment the product's functionality. For example, you might build a PowerApp to supplement Finance and Operations apps with information retrieved from another system.

To learn more about embedding Power Apps, watch the short [How to embed Power Apps](https://www.youtube.com/watch?v=x3qyA1bH-NY) video.

## Adding an embedded PowerApp to a page

### Overview

Before embedding a PowerApp into the client, you first need to find or build a PowerApp with the desired visuals and/or functionality. We will not describe the detailed process for building a PowerApp here. The [Introduction to Power Apps](https://docs.microsoft.com/powerapps/getting-started) topic is a good starting point if you are new to Power Apps.

When you are ready to embed a specific PowerApp, you can choose between one of two ways of accessing the PowerApp on a page, whichever route better fits your scenario. The first way is through the Power Apps button that has been added to the standard Action Pane. Power Apps added using this mechanism will appear as menu items inside the Power Apps menu button. When selected, each of these menu items will open a side pane that contains the embedded PowerApp. Alternatively, you may choose to show a PowerApp directly on a page as a new tab, FastTab, blade, or as a new section in a workspace.

When configuring your embedded PowerApp, you can select a single field that you want to send as input to the PowerApp. This allows the PowerApp to be responsive based on the data that you are currently viewing.

### Details

The following instructions show how to embed a PowerApp into the web client.

1. Go to the page where you would like to embed the PowerApp. This will be the same page that contains any data that needs to be passed to the PowerApp as input.
2. Open the **Insert a PowerApp** pane:

    - Click **Options**, and then select **Personalize this form**. Under the **Insert** menu, choose **PowerApp**. Finally, select the region where you would like to add the PowerApp. If you want to embed the PowerApp under the Power Apps menu button, choose the Action Pane. If you want to embed the PowerApp directly onto the page, choose the appropriate tab, FastTab, blade, or section (if you're on a workspace).
    - If the PowerApp will be accessed using the Power Apps menu button, you can alternatively click the **Power Apps** menu button in the standard Action Pane, and then select **Insert a PowerApp**.

3. Configure the embedded PowerApp:

    - The **Name** field indicates the text shown for the button or tab that will contain the embedded PowerApp. Oftentimes, you may want to repeat the name of the PowerApp in this field.
    - **App ID** is the GUID for the PowerApp that you want to embed. To retrieve this value, find the PowerApp on [web.powerapps.com](https://web.powerapps.com) and then locate the **App ID** field under **Details**.
    - For **Input data for the PowerApp**, you can optionally select the field that contains the data that you want to pass to the PowerApp as input. See the section later in this topic titled [Building a PowerApp that leverages data from Finance and Operations apps](#building-a-powerapp-that-leverages-data-sent-from-finance-and-operations-apps) for details on how the PowerApp can access the data sent from Finance and Operations apps.
    - Choose the **Application size** that matches the type of PowerApp that you're embedding. Select **Thin** for Power Apps built for mobile devices, and **Wide** for Power Apps built for tablets. This ensures a sufficient amount of space is allotted for the embedded PowerApp.
    - The **Legal entities** FastTab provides the ability to choose which legal entities the PowerApp is available for. The default is to show the PowerApp in all legal entities.

4. After confirming that the configuration is correct, click **Insert** to embed the PowerApp on the page. You will be prompted to refresh the browser in order to see the embedded PowerApp.

## Sharing an embedded PowerApp

After you have embedded a PowerApp on a page and confirmed that it is working correctly with any data context passed from the page, you might want to share this embedded PowerApp with other users in the system. This can be accomplished in two different ways using the personalization capabilities of the product:

- The recommended scenario is through the system administrator, who can push a personalization to all users or a subset of users.
- Alternatively, you can export your page's personalizations, send them to one or more users, and have each of those users import those changes. The Manage option on the personalization toolbar enables you to export and import personalizations.

See [Personalize the user experience](personalize-user-experience.md) for more details about the personalization capabilities in the product and how to use them.

## Building a PowerApp that leverages data sent from Finance and Operations apps

An important part of building a PowerApp that will be embedded in Finance and Operations apps is utilizing the input data from Finance and Operations apps. Inside the PowerApp, that input data can be accessed using the Param("EntityId") variable.

For example, in the OnStart function of the PowerApp, you could set the input data from Finance and Operations apps to a variable like this:

```
If(!IsBlank(Param("EntityId")), Set(FinOpsInput, Param("EntityId")), Set(FinOpsInput, ""));
```

## Viewing an embedded PowerApp

To view an embedded PowerApp on a page in Finance and Operations apps, simply go to a page with an embedded PowerApp. Recall that Power Apps can be accessed through the Power Apps button in the standard Action Pane, or can appear directly on the page as a new tab, FastTab, blade, or as a new section in a workspace. When a user first attempts to load a PowerApp on a page, he or she will be prompted to sign in to Power Apps to ensure the user has the approrpiate permissions to use the PowerApp.

## Editing an embedded PowerApp

After a PowerApp has been embedded onto a page, you may need to make some changes to the configuration of that PowerApp. For example, perhaps you want to modify the label associated with the embedded PowerApp or a new version of a PowerApp has been created and you need to update the App ID to point at the latest PowerApp.

Follow these steps to edit the configuration of an embedded PowerApp:

1. Go to the **Edit a PowerApp** pane.

    - If the embedded PowerApp is accessed through the Power Apps menu button, right-click on the Power Apps menu button and select **Personalize**. Select the PowerApp that you want to configure from the **Select PowerApp** drop-down menu.
    - If the embedded PowerApp appears directly on the page, select **Options**, and then select **Personalize this form**. Using the **Select** tool, click the embedded PowerApp.

2. Make the needed modifications to the Power Apps configuration, and then click **Save**.

## Removing an embedded PowerApp

After a PowerApp has been embedded onto a page, there are two ways to remove it if needed:

- Go to the **Edit a PowerApp** pane using the instructions from the [Editing an embedded PowerApp](#editing-an-embedded-powerapp) section earlier in this topic. Confirm that the pane displays information for the embedded PowerApp that you would like to remove, and then click the **Delete** button.
- Because an embedded PowerApp is saved as personalization data, clearing your page's personalization will also remove any embedded Power Apps on that page. Note that clearing the page's personalization is permanent and cannot be undone. To remove your personalizations on a page, select **Options** and then click **Personalize this form**. Under the **Manage** menu, select the **Clear** button. After refreshing your browser, all the previous personalizations for this page will be removed. See [Personalize the user experience](personalize-user-experience.md) for more information about how to optimize pages using personalization.

## Appendix

### Developer control over where a PowerApp can be embedded

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
