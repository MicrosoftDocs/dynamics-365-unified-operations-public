---
# required metadata

title: Embed PowerApps
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: jasongre
manager: AnnBe
ms.date: 10/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer: sericks
ms.search.scope: Operations Platform 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jasongre
ms.search.validFrom: 2017-11-30
ms.dyn365.ops.version: Platform update 15
---

# Embed PowerApps

[!include[banner](../includes/banner.md)]


[!Note] This feature is supported in Dynamics 365 for Finance and Operations, Enterprise edition platform update 15 or later.

## Introduction
Microsoft Dynamics 365 for Finance and Operations, Enterprise edition supports integration with Microsoft PowerApps, a service for developers and nontechnical users to build custom business apps for mobile devices, tablets, and the web without writing code. PowerApps developed by you, your organization, or the broader ecosystem can then be embedded in the Finance and Operations client to augment the product's functionality. For example, you might build a PowerApp to supplement Finance and Operations with information retrieved from another system.  

## Adding an embedded PowerApp to a page
### Overview
Before embedding a PowerApp into the Finance and Operations client, you first need to find or build a PowerApp with the desired visuals and/or functionality. We will not describe the detailed process for building a PowerApp here; however, the Introduction to PowerApps article is a good starting point for those who are new to PowerApps.

Once you are ready to embed a particular PowerApp, you can choose between one of two ways of accessing the PowerApp on a page, whichever route better fits your scenario. The first way is through the new PowerApps button that has been added to the standard Action Pane. PowerApps added via this mechanism will appear as menu items inside the PowerApps menu button. When selected, each of these menu items will open a dialog containing the embedded PowerApp. Alternatively, you may choose to show a PowerApp directly on a page inside a pivot tab, fast tab, vertical tab, or panorama section. 

When configuring your embedded PowerApp in Finance and Operations, you can select a single field you want to send as input to the PowerApp. This allows the PowerApp to be responsive based on the data you are currently viewing in Finance and Operations.  

### Details
Follow the instructions below to embed a PowerApp into the Finance and Operations web client.  

1. Navigate to the page where you would like to embed the PowerApp. This will be the same page that contains any data that needs to be passed to the PowerApp as input.  
2. Open the **Insert a PowerApp** dialog
   - Click **Options** then select **Personalize this form**. Under the **Insert** menu, choose **PowerApp**. Finally, select the region where you would like to add a PowerApp. If you want to embed the PowerApp under the PowerApps menu button, choose the Action Pane. If you want to embed the PowerApp directly onto the page, choose the appropriate pivot tab, fast tab, vertical tab, or panorama section.   
   - If the PowerApp will be accessed via the PowerApps menu button, you can alternatively click the **PowerApps** menu button in the standard Action Pane and then select **Insert a PowerApp**.  
3. Configure the embedded PowerApp
   - **Name** field indicates the text shown for the button or tab that will contain the embedded PowerApp. Oftentimes, you may want to repeat the name of the PowerApp in this field.  
   - **App ID** is the GUID for the PowerApp you want to embed. To retrieve this value, find the PowerApp on web.powerapps.com, its Details, and find the App ID field.  
   - For **Input data for the PowerApp**, you can optionally select the field that contains the data you want to pass to the PowerApp as input. See the section on Building a PowerApp that leverages data from Finance and Operations for details on how the PowerApp can access the data sent from Finance and Operations.  
   - Choose the **Application size** that matches the type of PowerApp you are embedding. Select **Thin** for PowerApps built for mobile devices, and **Wide** for PowerApps built for tablets. This ensures a sufficient amount of space is allotted for the embedded PowerApp.
   - The **Legal entities** fast tab provides the ability to choose which legal entities the PowerApp is available for. The default is to show the PowerApp in all legal entities.  
4. After confirming the configuration is correct, click **Insert** to embed the PowerApp on the page. A message will appear prompting you to refresh the browser in order to see the embedded PowerApp.  

## Building a PowerApp that leverages data sent from Finance and Operations
An important part of building a PowerApp that will be embedded in Finance and Operations is utilizing the input data from Finance and Operations. Inside the PowerApp, that input data can be accessed via the Param("EntityId") variable.  

As an example, in the OnStart function of the PowerApp, you could set the input data from Finance and Operations to a variable like this:

If(!IsBlank(Param("EntityId")), Set(FinOpsInput, Param("EntityId")), Set(FinOpsInput, "")); 

## Viewing an embedded PowerApp

   
   
## Editing an embedded PowerApp
After a PowerApp has been embedded onto a page in the system, you may need to make some changes to the configuration of that PowerApp. For example, perhaps you want to modify the label associated with the embedded PowerApp or you or your organization have created a new version of a PowerApp, and you need to update the App ID to point at the latest PowerApp. 

Follow these steps to edit the configuration of an embedded PowerApp:
1. Navigate to the **Edit a PowerApp** dialog. 
   - If the embedded PowerApp is accessed through the PowerApps menu button, right-click on the PowerApps menu button and select Personalize. Select the PowerApp you are you interested in from the **Select PowerApp** dropdown.  
   - If the embedded PowerApp appears directly on the page, select **Options** and then **Personalize this form**. Using the **Select** tool, click on the embedded PowerApp.  
2. Make the needed modifications to the PowerApps configuration, and then click Save.  

## Removing an embedded PowerApp
Once a PowerApp has been embedded onto a page in the system, there are two ways to remove it if desired: 
1. Navigate to the **Edit a PowerApp** dialog using the instructions from the [Editing an embedded PowerApp]. After confirming the dialog is showing information for the embedded PowerApp you would like to remove, simply click the **Delete** button. 
2. Since an embedded PowerApp is saved as personalization data, clearing your page's personalization will also remove any embedded PowerApps on that form. Note that clearing the page's personalization is permanent and cannot be undone. To remove your personalizations on a page, select **Options** and then click **Personalize this form**. Under the **Manage** menu, select the **Clear** button. After refreshing your browser, all the previous personalizations for this page will be removed. See Personalization the user experience for more information about how to optimize pages in Finance and Operations using personalization.  

## Sharing an embedded PowerApp
After you have embedded a PowerApp on a page and confirmed it is working correctly with any data context passed from the form, you may want to share this embedded PowerApp with other users in the system. This can be accomplished in two different ways using the personalization capabilities of the product:

- The recommended route is through the system administrator, who has the ability to push a personalization to all users or a subset of users. 

- Alternatively, you can export your changes (called personalizations), send them to one or more users, and have each of those users import your changes. The Manage option on the personalization toolbar enables you to export and import personalizations.

See Personalize the user experience for more details on how to use .
