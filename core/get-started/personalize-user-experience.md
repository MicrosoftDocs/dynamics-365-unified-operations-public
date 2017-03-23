---
# required metadata

title: Personalize the user experience
description: This article explains how you can personalize Microsoft Dynamics 365 for Operations.
author: RobinARH
manager: AnnBe
ms.date: 2016-03-08 19 - 56 - 24
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: SysUserSetup
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 62363
ms.assetid: 57b445d7-3e9e-4228-8728-f63b9dbd77a3
ms.search.region: Global
# ms.search.industry: 
ms.author: tlefor
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Personalize the user experience

This article explains how you can personalize Microsoft Dynamics 365 for Operations.

There are many types of personalizations in Microsoft Dynamics 365 for Operations. Some personalizations are selections that you make in a list of options on a setup page. Some personalizations are implicit, for  example, Dynamics 365 for Operations keeps track of the widths of grid columns if you adjust them, and the expanded/collapsed state of FastTabs. Other personalizations are explicit. For explicit personalizations, you enter an interactive personalization mode and modify the appearance of a page by directly managing the way that elements appear or act on the page. 

All personalizations, of any type, that a user makes in Dynamics 365 for Operations are for that user only, regardless of the company that the user interacts with. Changes that a user makes to a page don't affect other users in the system.

## Systemwide options for the current user
In the Navigation bar you'll find a gear image that is called the **Settings** menu button. Opening the **Settings** menu will show a number of choices. Selecting **Options** will open the user **Options** page. There you'll find four option tabs: **Visual**, **Preferences**, **Account**, and **Workflow**.

-   **Visual:** Use to choose a color theme and the default size of the elements on your pages.
-   **Preferences:** Here you can choose defaults for each time you open Dynamics 365 for Operations, including the company, initial page, and default view/edit mode (which determines if a page is locked for viewing or opened for editing each time you open it). You'll also find language, time zone, and date, time, and number format options. Lastly this page contains a number of miscellaneous preferences that will vary from release to release.
-   **Account:** Use to provide your user ID and other account-related options.
-   **Workflow:** This where you can choose workflow-related options.

## Implicit personalizations
Implicit personalizations are those personalizations that you perform simply by interacting with certain controls that remember their current visible state. 

**Grid columns:** You can adjust the width of a column in a list by selecting the sizing bar to the left or right of the column header and sliding it left or right to the desired width. Dynamics 365 for Operations will store the width that you'd like and show that column with that width every time you open the page with that list. 

**FastTabs:** Some pages have expandable sections called FastTabs. Dynamics 365 for Operations will store which FastTabs you have expanded, and which FastTabs you have collapsed. Each time you return to the page, those same FastTabs will be expanded or collapsed based on the last time you used them. In this article, we'll explain how to change the order of your FastTab sections. In some cases, collapsing a FastTab may improve performance because Dynamics 365 for Operations will not need to retrieve the information for that FastTab until the FastTab is expanded. 

**Fact Boxes:** Some pages have a section called a Fact Box pane. This pane contains read-only information related to the current subject of the page. Each section in the Fact Box Pane is called a Fact Box. You can expand or collapse a Fact Box and Dynamics 365 for Operations will store your preference. In some cases, collapsing a Fact Box may improve performance because Dynamics 365 for Operations will not need to retrieve the information for that Fact Box until the Fact Box is expanded.

## Explicit personalizations using the Personalization toolbar
Every person and company has a different perspective on which data is most important to them, or which data isn’t needed for the way they run their business. The ability to tailor the way your information is ordered, interacted with, or even hidden is key to making Dynamics 365 for Operations a personal and productive experience. 

Explicit personalizations are those personalizations that you perform explicitly with the intent to change the appearance or behavior of an element or page, by choosing a personalization menu. The most basic type of explicit personalization is where you right-click an element and select **Personalize**. (Note that not all elements on your page can be personalized.) When you select this method of personalization, you'll see the element's property window. 

[![Personalizing an element's properties](./media/personalization-element-properties.jpg)](./media/personalization-element-properties.jpg) 

You’ll personalize an element on your page in this manner if you simply want to change the element's label, hide the element so that it isn’t shown on the page (this doesn’t change any data, it simply doesn’t show you the information), include the information in the FastTab summary section (if the element is in a FastTab), skip the field when tabbing, or make it so that data cannot be changed by marking it as “Don’t Edit." 

When you want to move or hide elements or make several changes, you can use the Personalization toolbar, available from the elements Property window by choosing **Personalize this form**. The Personalization toolbar is also available on the form's Action pane, under the Personalize group of the **Options** tab. Select **Personalize this form** and you'll see the Personalization toolbar. 

[![Personalization toolbar](./media/personalization-personalizationtoolbar.jpg)](./media/personalization-personalizationtoolbar.jpg)

The Personalization toolbar has a number of personalization actions. Choose the **Select** tool when you want to select and change the properties of many elements, one at a time. First, click the Select tool, and then click the element whose properties that you want to modify. When you select an element, the element's property window will open and you can modify any of the properties for that element. You can repeat the process for other elements on your form that are personalizable. In some cases, you'll select an element and see that some of the properties are not modifiable. This means that based on the way the current element is used, Dynamics 365 for Operations cannot let you change that property. For example, you cannot hide a field that is required. 

Choose the **Move** tool when you want to select and move an element to a different location within the current group of elements. (You cannot move an element outside of its parent group). First, click the Move tool and then click the element that you want to move. When you click the element that you want to move, Dynamics 365 for Operations will scan the form to understand where this element can be moved and create a series of "drop zones" that show as a colored, bold line next to the area where the element can be dropped as you drag the element around within the current group. 

Choose the **Hide** tool to select and hide an element. To hide an element, simply choose the Hide tool and click the element that you'd like to hide. When you choose the Hide tool, all currently hidden elements will be made visible and shown in a shaded container so that you can choose the element to unhide it. Choose the Select tool to see how he page will look with the selected elements hidden. Choose the **Summary** tool when you want a numeric or string field to show in the FastTab summary area. The Summary tool will only apply to fields that are contained within a FastTab section. When you choose the Summary tool, Dynamics 365 for Operations will show all fields that have been selected as summary fields by enclosing them in a shaded container. You can interactively add and remove fields from a FastTab summary by clicking the field. 

Choose the **Skip** tool to remove an element from the page's keyboard tab sequence. When you choose the Skip tool, all currently skipped elements will be shown in a shaded container so that you can choose them again to make them part of the tab sequence by selecting a skipped element. 

Choose the **Edit** tool when you want to mark an element as Editable or Not Editable. When you choose the Edit tool, all currently non-editable elements will be shown in a shaded container so that you can choose them to make them editable. Note, some fields are required and cannot be made non-editable. Those fields will appear with a padlock icon next to them. 

Choose the **Add** tool to add a field to your page. With the add tool, you cannot create a new field, but you can add fields that are part of the current page definition, but not shown on the page. When you choose the Add tool, you'll first need to select the group or area where you'd like to add a field. A dialog box will display the list of fields related to the section that you've selected. From that dialog box, you can select one or more fields to add and click Insert. If you later want to remove a field that you've previously added, repeat the process, but simply clear the field that you previously added. 

Choose the **Manage** button to see a list of management options related to all personalizations for the current page. 

Choose **Clear** to reset the page to its default, installed state. All personalizations on the current page will be cleared. There is no undo action, so only use this option when you are certain that you want to reset your page. 

Choose **Import** to use a personalization from a personalization file that you or someone else previously created for this page. Importing a personalization will clear any personalizations that you've performed on the entire page and instead use all of the personalizations from the selected file. If you want to save or share a personalization, then you'll select the **Export** option to save the personalizations to a file. 

Choose the **Close** button to close the toolbar and return the page to it's previously interactive state. 

With the Personalization toolbar, saving is implicit. Your personalizations take effect immediately as you make them and there is no need to click a **Save** button. In some cases, you'll see a padlock icon next to an element when you select a tool. This means that in order for the page to work as correctly, you cannot modify the properties related to the selected tool. When the Personalization toolbar is opened, the page becomes non-interactive. You cannot enter data or expand or collapse sections.

## Explicit personalization: Adding a tile or list to a workspace
Some pages with lists will have an additional personalization feature available within its Action Pane, under the Personalize group of the Options tab. Select **Add to Workspace** to open the drop-down list that gives you the ability to show the information in the current list (filtered and sorted or default) on a Workspace as a list or a summary tile (that can be used to show the number of items in the list). 

[![Add to workspace](./media/personalization-addtoworkspace.png)](./media/personalization-addtoworkspace.png) 

To add a list to a workspace, first sort or filter the list with the information as you'd like to see it on your workspace, then select the Add to Workspace dialog. Next, select the desired workspace and select **List** from the Presentation drop-down list. When you select **List** a dialog will open allowing you to pick the columns you'd like to see in the list, and the label for the list as it will appear on the workspace. 

To add a tile to a workspace, first filter the list to represent the data you want summarized (or want quick access to). Then, open the Add to Workspace drop dialog. Next, select the desired workspace and select **Tile** from the Presentation drop down. When you select **Tile**, a dialog will open allowing you to provide a tile label and decide if the tile will show a count. When placed on a workspace, the tile will allow you to open the current page from the workspace, and show the list of information related to the tile. 

When your list or tile is added to a workspace, you can then open that workspace and re-order the list or tile within the group it was placed.

## Explicit personalization: Adding a summary from a workspace to a dashboard
Some workspaces contain count tiles (tiles with numbers on them) that you'd also like to see on your dashboard. In a workspace, right-click a count tile and select **Personalize**. Select **Pin to Dashboard**. The next time you navigate to (and refresh) the selected dashboard, you'll see that count below that workspace's navigation tile on the dashboard.

## Explicit personalization: Personalizing your dashboard
The dashboard is often the first page you'll see when you open Dynamics 365 for Operations. You can personalize the dashboard to rename your workspace navigation tiles, to show only the tiles that you'd like to see, rename the tiles, or to arrange the tiles in the order you'd prefer to see them. To personalize the dashboard, select any tile and right-click to open a context menu. On the context menu, select **Personalize**. If the selected tile is one that  you'd like to hide or rename or skip, you can make that change directly on the Property window that has appeared. If you'd like to arrange tiles, then select **Personalize this form** in the Property window to open the Personalization toolbar. You can then use the Move Tool to arrange the tiles.

## Administration of personalization
It is possible to personalize a page and share it with other users by simply exporting the personalized page and asking the other users to navigate to the personalized page and import the personalization file that you've created. If a user has admin privileges, they can also manage personalizations for other users in the **Personalization Setup** page. Navigate to the b page. In the **Personalization** page, you'll find two tabs, one labeled **System** and one labeled **Users**. 

**System:** This is where you can temporarily disable or "turn off" all personalizations in the system. This doesn't delete personalizations, instead it resets all forms to their default state. You can later re-enable personalization to have all personalizations re-applyed to each users forms. You can also delete all personalizations for all users. Note that when you delete personalizations, there is no way to automatically re-enable personalizations from the system. Make sure you have exported personalizations that you may want to later import before performing this step. 

**Users:** This is where you can decide for each user if they can perform either implicit or explicit personalization. You can also decide if each user can perform implicit or explicit personalization on a specific form. Lastly, you can import or export or delete a personalization for each user. 

**Note:** In its initial release, personalization administration allows only management on a user by user basis.

