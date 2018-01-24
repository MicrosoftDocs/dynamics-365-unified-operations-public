---
# required metadata

title: Embed PowerApps
description: This topic describes how to embed PowerApps into the Finance and Operations client to augment the product's functionality.
author: jasongre
manager: AnnBe
ms.date: 01/24/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form:  FormRunConfigurationAddPAControl
audience: Application User, Developer, IT Pro
# ms.devlang: 
# ms.reviewer: sericks
ms.search.scope: Operations, Core 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jasongre
ms.search.validFrom: 2018-02-28
ms.dyn365.ops.version: Platform update 14
---

# Embed PowerApps

[!include[banner](../includes/banner.md)]

[!include[banner](../includes/pre-release.md)] 

Microsoft Dynamics 365 for Finance and Operations, Enterprise edition supports integration with Microsoft PowerApps, a service for developers and non-technical users to build custom business apps for mobile devices, tablets, and the web without writing code. PowerApps developed by you, your organization, or the broader ecosystem can then be embedded in the Finance and Operations client to augment the product's functionality. For example, you might build a PowerApp to supplement Finance and Operations with information retrieved from another system.  

## Adding an embedded PowerApp to a page
### Overview
Before embedding a PowerApp into the Finance and Operations client, you first need to find or build a PowerApp with the desired visuals and/or functionality. We will not describe the detailed process for building a PowerApp here. The [Introduction to PowerApps](https://docs.microsoft.com/en-us/powerapps/getting-started) topic is a good starting point if you are new to PowerApps.

When you are ready to embed a specific PowerApp, you can choose between one of two ways of accessing the PowerApp on a page, whichever route better fits your scenario. The first way is through the PowerApps button that has been added to the standard Action Pane. PowerApps added using this mechanism will appear as menu items inside the PowerApps menu button. When selected, each of these menu items will open a dialog box that contains the embedded PowerApp. Alternatively, you may choose to show a PowerApp directly on a page inside a pivot tab, vertical tab, FastTab, or panorama section. 

When configuring your embedded PowerApp in Finance and Operations, you can select a single field that you want to send as input to the PowerApp. This allows the PowerApp to be responsive based on the data that you are currently viewing in Finance and Operations.  

### Details
The following instructions show how to embed a PowerApp into the Finance and Operations web client.  

1. Go to the page where you would like to embed the PowerApp. This will be the same page that contains any data that needs to be passed to the PowerApp as input.  
2. Open the **Insert a PowerApp** dialog box:
   - Click **Options**, and then select **Personalize this form**. Under the **Insert** menu, choose **PowerApp**. Finally, select the region where you would like to add a PowerApp. If you want to embed the PowerApp under the PowerApps menu button, choose the Action Pane. If you want to embed the PowerApp directly onto the page, choose the appropriate pivot tab, vertical tab, FastTab, or panorama section.   
   - If the PowerApp will be accessed using the PowerApps menu button, you can alternatively click the **PowerApps** menu button in the standard Action Pane, and then select **Insert a PowerApp**.  
3. Configure the embedded PowerApp:
   - The **Name** field indicates the text shown for the button or tab that will contain the embedded PowerApp. Oftentimes, you may want to repeat the name of the PowerApp in this field.  
   - **App ID** is the GUID for the PowerApp that you want to embed. To retrieve this value, find the PowerApp on [web.powerapps.com](https://web.powerapps.com) and then locate the **App ID** field under **Details**.  
   - For **Input data for the PowerApp**, you can optionally select the field that contains the data that you want to pass to the PowerApp as input. See the section later in this topic titled "Building a PowerApp that leverages data from Finance and Operations" for details on how the PowerApp can access the data sent from Finance and Operations.  
   - Choose the **Application size** that matches the type of PowerApp that you're embedding. Select **Thin** for PowerApps built for mobile devices, and **Wide** for PowerApps built for tablets. This ensures a sufficient amount of space is allotted for the embedded PowerApp.
   - The **Legal entities** FastTab provides the ability to choose which legal entities the PowerApp is available for. The default is to show the PowerApp in all legal entities.  
4. After confirming that the configuration is correct, click **Insert** to embed the PowerApp on the page. You will be prompted to refresh the browser in order to see the embedded PowerApp. 

## Sharing an embedded PowerApp
After you have embedded a PowerApp on a page and confirmed that it is working correctly with any data context passed from the page, you might want to share this embedded PowerApp with other users in the system. This can be accomplished in two different ways using the personalization capabilities of the product:

- The recommended scenario is through the system administrator, who can push a personalization to all users or a subset of users. 

- Alternatively, you can export your page's personalizations, send them to one or more users, and have each of those users import those changes. The Manage option on the personalization toolbar enables you to export and import personalizations.

See [Personalize the user experience](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/personalize-user-experience) for more details about the personalization capabilities in the product and how to use them.

## Building a PowerApp that leverages data sent from Finance and Operations
An important part of building a PowerApp that will be embedded in Finance and Operations is utilizing the input data from Finance and Operations. Inside the PowerApp, that input data can be accessed using the Param("EntityId") variable.  

For example, in the OnStart function of the PowerApp, you could set the input data from Finance and Operations to a variable like this:

If(!IsBlank(Param("EntityId")), Set(FinOpsInput, Param("EntityId")), Set(FinOpsInput, "")); 

## Viewing an embedded PowerApp
To view an embedded PowerApp on a page in Finance and Operations, simply go to a page with an embedded PowerApp. Recall that PowerApps can be accessed through the PowerApps button in the standard Action Pane, or can appear directly on the form as a pivot tab, vertical tab, FastTab, or panorama section. When a user first attempts to load a PowerApp on a form, he or she will be prompted to sign in to PowerApps to ensure the user has the approrpiate permissions to use the PowerApp.   

## Editing an embedded PowerApp
After a PowerApp has been embedded onto a page, you may need to make some changes to the configuration of that PowerApp. For example, perhaps you want to modify the label associated with the embedded PowerApp or a new version of a PowerApp has been created and you need to update the App ID to point at the latest PowerApp. 

Follow these steps to edit the configuration of an embedded PowerApp:
1. Go to the **Edit a PowerApp** dialog box. 
   - If the embedded PowerApp is accessed through the PowerApps menu button, right-click on the PowerApps menu button and select **Personalize**. Select the PowerApp that you want to configure from the **Select PowerApp** drop-down menu.  
   - If the embedded PowerApp appears directly on the page, select **Options**, and then select **Personalize this form**. Using the **Select** tool, click the embedded PowerApp.  
2. Make the needed modifications to the PowerApps configuration, and then click **Save**.  

## Removing an embedded PowerApp
After a PowerApp has been embedded onto a page, there are two ways to remove it if needed: 

- Go to the **Edit a PowerApp** dialog box using the instructions from the "Editing an embedded PowerApp" section earlier in this topic. Confirm that the dialog box displays information for the embedded PowerApp that you would like to remove, and then click the **Delete** button. 

- Because an embedded PowerApp is saved as personalization data, clearing your page's personalization will also remove any embedded PowerApps on that form. Note that clearing the page's personalization is permanent and cannot be undone. To remove your personalizations on a page, select **Options** and then click **Personalize this form**. Under the **Manage** menu, select the **Clear** button. After refreshing your browser, all the previous personalizations for this page will be removed. See [Personalization the user experience](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/personalize-user-experience) for more information about how to optimize pages using personalization.  

## Appendix 
### Developer control over where a PowerApp can be embedded
By default, users can embed PowerApps on any page, either under the PowerApps menu button or directly on the page as a pivot tab, vertical tab, FastTab, or panorama section. However, if required, developers can also configure this feature to only allow embedding of PowerApps on certain pages by implementing the following methods: 

- **isPowerAppPersonalizationEnabled** - If this method returns false for a specific page, then the PowerApps menu button will not be shown, and users will not be able to embed PowerApps anywhere on this page, including as a tab. 

- **isPowerAppTabPersonalizationEnabled** - If this method returns false for a specific page, then users will not be able to embed PowerApps directly on the page as a pivot tab, vertical tab, FastTab, or panorama section. Users will still be able to embed PowerApps through the PowerApps menu button if embedding is allowed on the form.  

The following example shows a new class with the two methods needed to configure where PowerApps can be embedded.  

```
[ExtensionOf(classStr(FormRunConfigurationPowerAppsConfiguration))]

public final class ClassTest_Extension
{

    public static boolean isPowerAppPresonalizationEnabled(str pageName)
    {
        var result = next isPowerAppPresonalizationEnabled(pageName);
        return true;
    }

    public static boolean isPowerAppTabPresonalizationEnabled(str pageName)   
    {
        var result = next isPowerAppTabPresonalizationEnabled(pageName);
        return true;
    }
    ```

}

