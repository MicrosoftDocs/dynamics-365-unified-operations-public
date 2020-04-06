---
# required metadata

title: Personalize the user experience
description: This topic explains how you can personalize the app.
author: jasongre
manager: AnnBe
ms.date: 02/05/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SysUserSetup, DefaultDashboard
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 62363
ms.assetid: 57b445d7-3e9e-4228-8728-f63b9dbd77a3
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Personalize the user experience

[!include [banner](../includes/banner.md)]

This topic explains how you can personalize the app.

There are three basic classes of personalizations.

- Personalizations that are made on a setup page. Examples include the color theme and time zone.
- Personalizations that are related to page usage. These personalizations are known as *implicit* personalizations. For example, the system keeps track of the width of grid columns if you adjust them, and the expanded or collapsed state of FastTabs.
- Personalizations that a user makes to the appearance of a page by changing the way that an element appears or acts on that page, often through an interactive personalization mode. These personalizations are known as *explicit* personalizations. For example, the user might add, hide, or rearrange elements on the page.

Every personalization that a user makes is for that user only, regardless of type of personalization or the company that the user is currently interacting with. The changes that one user makes to a page don't affect other users in the system.

## System-wide options for the current user

The **User options** page contains several system-wide settings for the current user. To open the **User options** page, select the **Settings** button (the gear symbol) on the navigation bar, and then select **User options**. The **User options** page has four tabs that contain various user settings:

- **Visual** – Select a color theme and the default size of elements on pages.
- **Preferences** – Select default values that are used every time that you open the system. These values include the company, the initial page, and the default view/edit mode. (The view/edit mode determines whether a page is locked for viewing or opened for editing every time that you open it.) This tab also includes options for the language, the time zone, and date, time, and number formats. Finally, this tab includes several miscellaneous preferences that vary from release to release.
- **Account** – Adjust your user name and other account-related options.
- **Workflow** – Select workflow-related options.

In addition to changing your user settings, you can also use the **User options** page to view and delete your usage data and personalizations. Just select **Usage data** on the Action Pane.

As you use the app, many of your selections are stored to make the system easier for you to use in the future. On the **Personalization** tab, you can view and manage the personal changes that you've made to pages in the system. On this tab, you can also reset feature callouts (that is, the pop-up windows that introduce new system features). You will then be alerted again about previously encountered features.

> [!NOTE]
> If the [Saved views](saved-views.md) feature is turned on, you can view and manage your personalizations by selecting **Personalization** on Action Pane on the **User options** page.

## Implicit personalizations

Implicit personalizations are personalizations that you make just by interacting with controls that store their current visible state.

- **Grid column widths** – You can adjust the width of a column in a grid by selecting the sizing bar to the left or right of the column header, and then sliding it left or right until the column is the desired width. The app stores the width that you set for a column. Then, the next time that you open the page that includes that grid, the column will be resized to that width.
- **Grid column totals** - (Only available with the new grid control enabled) You can decide whether or not a total should be shown at the bottom of any numeric column in a grid as well as whether the grid footer is visible. The app stores this data so that these preferences are remembered the next time you open the page. See the [Grid capabilities](grid-capabilities.md) topic for more information. 
- **FastTabs** – Some pages have expandable sections that are known as *FastTabs*. The app stores information about the FastTabs that you've expanded and collapsed. Then, the next time that you open the page, the same FastTabs will be either expanded or collapsed, based on your last interaction with the page. In some cases, you can help improve system performance by collapsing a FastTab, because the app doesn't have to retrieve the information for FastTabs until they are expanded. As is explained later this topic, you can also change the order of the FastTabs on a page.
- **Fact Boxes** – Some pages have a **Related information** pane that shows read-only information that is related to the current subject of the page. Each section in the **Related information** pane is known as a *Fact Box*. You can expand or collapse the **Related information** pane, and you can also expand or collapse individual Fact Boxes. The app stores these preferences. Then, the next time that you open the page, the **Related information** pane and the individual Fact Boxes will be either expanded or collapsed, based on your last interaction with the page. In some cases, you can help improve system performance by collapsing a FactBox, because the app doesn't have to retrieve the information for FactBoxes until they are expanded.
- **Action Panes** – An *Action Pane* appears near the top of most pages. The Action Pane contains buttons for many of the actions that you can perform on the current page. These buttons are often organized on tabs. You can "pin" the whole Action Pane open, or you can have it collapsed by default. Then, the next time that you open the page, the Action Pane will be either open or collapsed, based on your last interaction with the page. If you pinned the Action Pane open, the last tab that you used will be shown.
- **QuickFilters** – A *QuickFilter* appears above many grids. The QuickFilter lets you filter the grid, based on a column that you select. The app stores the column that you filtered on. Then, the next time that you open the page that includes that grid, the grid will be filtered on the same column. However, you can then select a different column to filter the grid on.
- **Column header filters** – When you filter a grid by using the *column header filters*, you can change the filter operator as you require to find the data that you want. For example, you can change the operator from **begins with** to **is exactly**. Every time that you use a column header filter and change the filter operator, the app stores the change. Then, the next time that you filter on that column, the filter operator will be restored.
- **Navigation pane** – You can open the *navigation pane* by selecting the **Expand the navigation pane** button in the upper left of any page. (This button is sometimes referred to as the _**Menu** button_, *hamburger*, *hamburger menu*, or *hamburger button*.) You can pin the navigation pane open, or you can have it collapsed by default. After you pin the navigation pane open, the app will keep it open until you collapse it.

## Explicit personalizations

Different people and companies have a different perspective on the data that is most important to them, and the data that they don't require for the way that they run their business. You can tailor the way that your information is ordered and interacted with. You can also specify that some information should be hidden. These capabilities are key to a personal and productive experience, and are examples of explicit personalizations. Explicit personalizations are personalizations that you explicitly make because you want to change the appearance or behavior of an element or page.

### Shortcut menu options

Shortcut menus provide a few ways to explicitly change a page so that it better meets your requirements or the requirements of your company. (A shortcut menu is also known as a *right-click menu* or *context menu*.)

Some of the most typical and important changes that can be made to a page are available directly as options on a shortcut menu. For example, starting in Platform update 17, if you want to add or hide columns in a grid, just right-click a column header, and then select **Add columns** or **Hide this column**.

Additionally, the most basic types of explicit personalization are available by right-clicking an element and then selecting **Personalize**. (Note that not all elements on your page can be personalized.) When you use this personalization method, the element's property window appears.

![Personalizing an element's properties](./media/cli-element-property-window.png)

You can use the property window to personalize an element in the following ways:

- Change the element's label.
- Hide the element so that it isn't shown on the page. The data in the field isn't deleted or modified. The information just doesn't appear on the page any longer.
- Include the information in the FastTab's summary section (if the element is on a FastTab).
- Skip the field so that it never receives focus when you tab through the page.
- Prevent data in the field from being edited (for any record).
- Designate a field to be required for data entry. If no value has been entered into this field, it will appear with a red border and an asterisk to indicate this state. This option is only available starting in 10.0.9 / Platforom update 35 when the [Saved views](saved-views.md) and **Designate fields as required using personalization**  features are enabled.

The property window might include other personalization capabilities, depending on the element. For example, the property window for a tile might let you promote that tile to a dashboard, and the property window for a dashboard might let you create a new workspace on that dashboard.

### The Personalization toolbar

If you want to make multiple changes to a page, or changes that aren't available through other mechanism (for example, if you want to reorder elements), you can use the **Personalization** toolbar. To open the **Personalization** toolbar, follow one of these steps:

- Select **Personalize this page** in an element's property window.
- Select **Personalize this page** in the **Personalize** group on the **Options** tab of any page's Action Pane.
- Select the **Settings** button (the gear symbol) on the navigation bar, and then select **Personalize**.

[![Personalization toolbar](./media/restyledPersonalizationToolbar.png)](./media/restyledPersonalizationToolbar.png)

#### Navigating the page

When the **Personalization** toolbar is open, the underlying page is read-only (in other words, you can't edit data), but it's still interactive. Specifically, you can expand or collapse the **Related information** pane, switch tabs, and expand or collapse sections, just as you usually perform those actions on the page. To apply a personalization to a collapsible section or tab (for example, to hide a FastTab), you just have to select the button that appears next to that section or tab when it gains keyboard focus or when you hover over it.

#### Personalization tools

The following tools are available on the **Personalization** toolbar:

- Use the **Select** tool to select and change the properties of an element. To use this tool, select the **Select** button on the toolbar, and then select the desired element. The element's property window appears, and you can change any of the properties of that element. You can repeat the process for other elements that can be personalized on the page. Note that some personalization properties might not be available in some scenarios. For example, you can't lock a field that is required.
- Use the **Hide** tool to hide an element on the page. To use this tool, select the **Hide** button on the toolbar, and then select the element to hide. When you use the **Hide** tool, all elements that are currently hidden are made visible but are shown in a shaded container. You can then make an element visible by selecting it. To see how the page will look when elements are hidden, switch to another personalization tool.
- Use the **Add a field** tool to add a field to your page. When you use this tool, you can add only fields that are part of the page definition. For information about how to create new fields that aren't part of the current page definition, see [Create and work with custom fields](user-defined-fields.md). After you select the **Add a field** button on the toolbar, you must first select the group or area where you want to add a field. A dialog box will show the list of fields that are related to the selected group or area. In the dialog box, select one or more fields to add, and then select **Insert**. To remove a field that you previously added, repeat the process, but clear the selection of the field in the dialog box.
- Use the **Move** tool to move an element to a different location in the current group of elements. Note that you can't move an element outside its parent group. To use this tool, select the **Move** button on the toolbar, and then select the element to move. When you select an element, the app determines the locations where the element is allowed to be moved. These locations are known as *drop zones*. As you drag the element around in the current group, each drop zone is shown as a colored, bold line next to the area where the element can be dropped.
- Use the **Skip** tool to remove an element from the page's keyboard tab sequence. When you select the **Skip** button on the toolbar, all elements that are currently skipped are shown in a shaded container. You can interactively remove or add fields to the tab sequence.
- Use the **Show in header** tool when you want a field to appear in the FastTab's summary section. When you select the **Show in header** button on the toolbar, all fields that have been selected as summary fields are shown in a shaded container. You can interactively add fields to the FastTab summary and remove fields from it by selecting the fields.
- Use the "Require" tool to designate an element as required for data entry. When you select the **Require** button on the toolbar, all elements that have been personalized to be required are shown in a shaded container. You can then make them not required again. This option is only available starting in 10.0.9 / Platforom update 35 when the [Saved views](saved-views.md) and **Designate fields as required using personalization**  features are enabled.
- Use the **Lock** tool to mark an element as either editable or noneditable. When you select the **Lock** button on the toolbar, all elements that are currently noneditable are shown in a shaded container. You can then make them editable again. Note that some fields are required and can't be made noneditable. A padlock symbol appears next to those fields.
- Use the **Add an app from Power Apps** button to embed an app that was created by using Microsoft Power Apps into the page. For detailed information about how to embed an app from Power Apps into a page, see [Embed apps from Power Apps](embed-power-apps.md). This option is only available when the [Saved views](saved-views.md) feature is disabled.  
- Use the **Add an app** button to embed an app, either one created from Microsoft Power Apps or a third-party, into the page. This option is only available when the [Saved views](saved-views.md) feature is enabled. 
- Use the **Clear** tool to reset the page to its default, installed state. All personalizations on the current page will be cleared. There is no undo action. Therefore, use this tool only if you're sure that you want to reset the page.
- Use the **Import** tool to load a personalization from a file that you or someone else previously created. When you import personalizations for a page, you can choose whether they should be added to or replace all your existing personalizations for the page. There is no undo action. Therefore, after you import personalizations, you must manually clear or undo any changes that you don't want.
- Use the **Export** tool to save your personalizations for the page to a file. You can then share your personalizations with other users. Those users just have to import the file that contains your personalizations for the page.
- Select the **Close** button to close the **Personalization** toolbar and return the page to its previous interactive state.

Traditionally, when the **Personalization** toolbar is used, your personalizations take effect as soon as you make them. However, if the [Saved views](saved-views.md) feature is turned on, you must explicitly save personalizations to a view that you choose.

In some cases, when you select a tool, a padlock symbol appears next to an element. This symbol indicates that you can't modify the element properties that are related to the selected tool, because changes to those properties will prevent the page from working correctly.

### Adding a tile, list, or link to a workspace

For some pages that include lists, the **Add to workspace** personalization feature is available in the **Personalize** group on the **Options** tab of the Action Pane. This feature lets you push relevant information from the current list to a specific workspace. The information that appears in the workspace can be based on either the whole list, or a filtered and sorted version of the list. You can also specify whether the information appears in the workspace as a list, a summary tile that can show the number of items in the list, or a link.

> [!NOTE]
> If the [Saved views](saved-views.md) feature is turned on, the content that you push to a workspace is directly linked to a view. The view's query is used to fetch data in the workspace, and the corresponding tile or link in the workspace opens the page to that view, so that the view's query and personalizations are applied to it.

[![Add to workspace](./media/personalization-addtoworkspace.png)](./media/personalization-addtoworkspace.png)

- To add a list to a workspace, first sort or filter the list on the page so that it shows the information as you want it to appear in the workspace. (If the Saved views feature is turned on, you can't continue until you save a view that has these conditions.) Then select **Add to workspace**. Select a workspace, and then, in the **Presentation** field, select **List**. After you select **Configure**, a dialog box appears, where you can select the columns that should appear in the list in the workspace. You can also specify the label that is used for the list in the workspace.
- To add a tile to a workspace, first filter the list on the page so that it shows the data that should be summarized, or that you want quick access to. (If the Saved views feature is turned on, you can't continue until you save a view that has these conditions.) Then select **Add to workspace**. Select a workspace, and then, in the **Presentation** field, select **Tile**. After you select **Configure**, a dialog box appears, where you can specify the label that should be used for the tile in the workspace. You can also specify whether the tile should show a count. After the tile is added to the workspace, you can select it to open the current page from the workspace. You can then view the filtered list that is associated with the tile.
- To add a link to a workspace, first filter the list on the page so that it shows the data that you're interested in. (If the Saved views feature is turned on, you can't continue until you save a view that has these conditions.) Then select **Add to workspace**. Select a workspace, and then, in the **Presentation** field, select **Link**. After you select **Configure**, a dialog box appears, where you can specify the label that should be used for the link. You can also optionally specify a label for a new section that contains this link.

After you've added a list, tile, or link to a workspace, you can open that workspace and rearrange the elements in it as you want.

### Adding a summary from a workspace to a dashboard

Some workspaces contain count tiles (that is, tiles that have numbers on them), and you might want those tiles to appear on your dashboard too. In a workspace, right-click a count tile, select **Personalize**, and then, in the tile's property window, select **Pin to dashboard**. Then, the next time that you open and refresh the selected dashboard, the count will appear below the navigation tile for that workspace. You can select that count to go directly to the data that it represents.

### Personalizing your dashboard

The dashboard is often the first page that you see when you open the app. You can personalize the dashboard so that it shows only the workspace tiles that you want to see. You can also rearrange the tiles so that they appear in the order that you prefer to see them in, rename your workspace navigation tiles, or add a new workspace tile.

To personalize the dashboard, right-click any tile, and then select **Personalize** to open the tile's property window.

- If you want to hide or rename the selected tile, you can make that change directly in the property window.
- To reorder the workspace tiles, in property window, select **Personalize this page** to open the **Personalization** toolbar. You can then use the **Move** tool to rearrange the tiles as you want.
- To add a new workspace tile, in the property window, select **Add a workspace**. A new workspace tile is created at the bottom of the dashboard. You can rename this new workspace tile as you want. You can also add lists, tiles, and links to the workspace as described in the [Adding lists, tiles, or links to workspaces](#adding-a-tile-list-or-link-to-a-workspace) section of this topic.

## Administration of personalizations

After you personalize a page, you can share your personalizations with other users by exporting the personalized page. You can then ask other users to open the personalized page and import the personalization file that you created. Alternatively, you can give your personalizations to a user who has admin privileges. That user can then apply your personalization file to many users at the same time.

Users who have admin privileges can also manage personalizations for other users on the **Personalization** page.

For customers who haven't turned on the [Saved views](saved-views.md) feature, this page has four tabs:

- **Apply** – You can import or select a personalization for one or more users. To apply a personalization to one or more users, first select a role and users who have that role. Then either select an existing personalization to apply to the selected users, or import a personalization file. The personalization is validated and will be applied to all the selected users the next time that they open the selected page.
- **Clear** – You can clear all personalizations for a page or workspace for one or more users. First select a page or workspace to see a list of the users who have personalized it. Then select the users who should have personalizations for that page or workspace cleared, and select **Clear**. All personalizations that the selected users have applied to the selected page or workspace are deleted. This action can't be undone. However, if a personalization was saved for the page or workspace, that personalization can be reimported.
- **Users** – Select a user to see a list of the pages that the user has personalized. You can then turn that user's ability to use personalizations for specific pages, or for the whole system, on or off. You can also import, export, or clear a personalization for the user. In addition, you can reset feature callouts for the user. In this case, if the user previously dismissed any pop-up windows that introduce new features, they will appear again the next time that the user encounters those features.
- **System** – You can temporarily turn off personalization for all users in the system. In this case, all personalizations are deleted for all users, and all pages are reset to their default state. If you turn personalization back on later, all personalizations are reapplied. You can also permanently delete all personalizations for all users in the system. Personalizations that have been deleted can't be recovered. Therefore, before you perform this task, be sure to export any personalizations that you might want later.

For customers who have turned on the [Saved views](saved-views.md) feature, the **Personalization** page has five tabs:

- **Published views** – These views have been published to your organization. To change the users who are targeted by these views, you can change the security roles or legal entities that are associated with each view. You can also export or delete one or more published views.
- **Unpublished views** – These views are template views that have been imported into your system but haven't yet been published. You can publish, export, or delete these views.
- **Personal views** – These views have been created by users in the system. You can publish a personal view to the organization, or copy one or more of these views to other users. You can also export or delete these views as required.
- **Users** – Select a user to see a list of the pages that the user has personalized. You can then turn that user's ability to use personalizations for specific pages, or for the whole system, on or off. You can also import, export, or clear a personalization for the user. In addition, you can reset feature callouts for the user. In this case, if the user previously dismissed any pop-up windows that introduce new features, they will appear again the next time that the user encounters those features.
- **System** – You can temporarily turn off personalization for all users in the system. In this case, all personalizations are deleted for all users, and all pages are reset to their default state. If you turn personalization back on later, all personalizations are reapplied. You can also permanently delete all personalizations for all users in the system. Personalizations that have been deleted can't be recovered. Therefore, before you perform this task, be sure to export any personalizations that you might want later.

Users who have access to the **Personalization** page can also import personal or template views by using the **Import views** button on the Action Pane.

## Personalizing inventory dimensions

When you personalize the setup of inventory dimensions on a page, consider the settings that have been created by using the **Display dimension** option. For example, you use personalization to hide a column for the Batch number inventory dimension, but the column appears the next time that the page is opened. This behavior occurs because the **Dimension display** settings control the inventory dimension columns that are shown. The **Dimension display** settings apply across all pages and override any personalized setup of inventory dimension fields on individual pages.

Therefore, in the preceding example, if you don't want the column for the Batch number inventory dimension to appear on a page, you must clear that dimension as part of the **Display dimensions** option for that page.
