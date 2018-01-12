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
audience: [Pick one: Application User
# ms.devlang: 
# ms.reviewer: sericks
ms.search.scope: Operations Platform 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jasongre
ms.search.validFrom: 2017-11-30
ms.dyn365.ops.version: Platform update 13
---

# Embed PowerApps

[!include[banner](../includes/banner.md)]


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
