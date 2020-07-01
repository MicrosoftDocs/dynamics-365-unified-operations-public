---
# required metadata

title: Saved views
description: This topic describes how to use the saved views features.   
author: jasongre
manager: AnnBe
ms.date: 05/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: DefaultDashboard
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2019-07-31
ms.dyn365.ops.version: Platform update 28

---

# Saved views

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

## Introduction
Personalization plays an important role in allowing users and organizations to optimize the user experience to meet their needs. For more details on personalization, see [Personalize the user experience](personalize-user-experience.md).

With traditional personalization, users could only have a single set of personalizations per page. Saved views expands on personalization in several important ways:

-    Views permit users to have multiple named sets of personalizations per form, which they can quickly switch between as needed. This allows a user to create multiple optimized views of a page, where each view has been tailored to fit the needs of performing a particular business task. 

-    Views created for particular page types can also include user-added filters or sorts, which allows users to quickly return to commonly filtered datasets. See the [What pages support views](saved-views.md#what-pages-support-views) section for more details. 

-    Views can be published to users in specific security roles and specific legal entities. Therefore, any user who has a specified role and access to a specified legal entity can access and use that view, notably including users who do not have permission to personalize. This publish capability lets organizations define corporate, standard views that are optimized for their business. For more information, see the [Managing personalizations at an organizational level with views](saved-views.md#managing-personalizations-at-an-organizational-level-with-views) section.

-    Unlike traditional personalization, views are not automatically saved when a user performs personalizations or filters a list. Explicit saves are required to provide flexibility in creating a view before or after the changes associated with that view have been made and to ensure that view definitions are not unintentionally altered by filters or personalizations that are not intended for long-term use. Items the system automatically remembers as part of typical page usage (e.g. column widths, expand/collapse state of sections) will be remembered per view.  

-    Views can be added to workspaces as tiles, lists, or links. Therefore, a filtered data set can be surfaced in a workspace, and users can associate a set of personalizations that are relevant to that data set with a tile or link.

## Switching between views
After views have been enabled for an environment, any page that supports views will include a collapsed view selector control at the top of the page that shows the name of the current view.  

There are two size variations to the view selector: 

-   **Large view selectors**: Pages that prominently feature a list will have a larger view selector for a few reasons. Most importantly, the larger view selector indicates the pages where the view can include user-defined filters. Because filters are included in the views, the larger selector size is also warranted as the view names will often be the best description of the data shown on the screen and the expectation is that users will switch between views more often on these page types.  
 
-   **Small view selectors**: All other full-screen pages (with the exception of workspaces and the dashboard) have a smaller view selector that appears next to the page caption. Views on these pages only include personalizations (and not user-defined filters). On these pages, the caption or record title is often the most important information at the top of the page. The smaller size of the view selector also reflects a lower expected frequency of view switching on these pages. 
 
If you click on the view name, the view selector opens and shows the list of available views for this page.

-    **Standard view**: The **Standard** view is the out-of-box view of the page, where no personalizations are applied.
-    **Personal views**: The views without padlocks represent your personal views. These are views that either you have created or that an administrator has given to you.  
-    **Locked views**: Some views (such as the **Standard** view and any views that are published to your role) have a padlock symbol next to them in the view selector. This symbol indicates that you can't edit those views. However, changes that reflect page usage are automatically saved, including changing the width of a grid column, or expanding or collapsing a FastTab. Nevertheless, if you have personalization privileges, you can use the **Save as** action to make a personal view that is based on a locked view.
-    **New views**: Published views that have not yet been opened are delineated with a spark icon to the left of the view name.  

To switch to a different view, first open the view selector and then select the view that you want to load. 

## Creating and modifying views
Unlike traditional personalization, views are not automatically saved when a user personalizes the page (or applies a filter or sort to a list). An explicit action is required to save these changes to a view. This provides user flexibility in creating a view before or after the changes associated with that view have been made and also ensures that view definitions are not unintentionally altered by one-time filters or personalizations. Note that typical page usage items (such as expanding or collapsing a FastTab or changing the width of a grid column) are automatically saved to the current view, even for locked views. 

To ensure that the current state of the view is known, when you start making changes to a view by personalizing or filtering, an asterisk will appear next to the current view name indicating that you are looking at an unsaved, modified version of that view.

If you want to save those changes, follow these steps.
1.	Select the view name to open the view selector.
2.	To modify the existing view:
     1.    Select **Save**. Note that this action will not be enabled for locked views. 
3.	To create a new view:
     1.    Select **Save as**. 
     2.    Enter a view name and (optionally) a description.
     3.    Select **Save**.

## Changing the default view
The default view is the view that the system will try to open when you first navigate to the page. You should set this to the view that you expect to use most often.  

To change the default view for a page, follow these steps: 
1.	Switch to the view that you use as the default. 
2.	Select the view name to open the view selector. 
3.	Select **More** and then **Pin as default**.  

Alternatively, when you create a new view (by using the **Save as** action), you can make that new view the default view by setting the **Pin as default** option before you save the view.

Note that in some cases, the query associated with the default view does not execute when you first navigate to a page. For example, if you navigate through a tile to a page, the tile's query will be executed regardless of the query associated with the default view. Also, if you navigate to a page with a Standard view that already has a defined query, the original query will execute in place of the default view's query. When this happens, you will be alerted by an informational message when the view is loading. Switching views after the page has loaded should allow the view query to execute as expected. Starting in version 10.0.10 / Platform update 34, the informational message will have an embedded action allowing you to load the default view's query directly.

## Managing personal views 
The **Manage my views** dialog box gives you basic maintenance capabilities over your personal views and the order of views in the view selector. To open this page, click the view name to open the view selector drop-down menu, select **More**, and then select **Manage my views**.  

For a list of available views for that page, the following set of actions are available.  
-    **Change the default view**: Use the **Pin as default** action to make the currently highlighted view the default view for this page.  
-    **Reorder your views**: Use the **Move up** and **Move down** actions to rearrange your views in a specific order.  
-    **Rename a view**: Use the **Rename** action to change the name of the currently highlighted personal view. This action is turned off for locked views. 
-    **Delete a view**: Use the **Delete** action to permanently delete the currently highlighted view from the page. There is no way to recover a view after you remove it.  

Any changes made in this dialog box will take effect after you select the **Save** button.

## Managing personalizations at an organizational level with views
To help you understand how saved views help improve management of personalizations at an organizational level, this section describes some differences in personalization management with and without the saved views feature.

Without views, administrators would apply a set of personalizations for a page to a user or a group of users via the Personalization page. If those users had personalization rights, the personalizations would be applied to that page. However, there was no ability to prevent users from further personalizing the page, which meant the organization could not ensure that its users had a consistent user interface. If any of those users didn't have personalization rights, the personalizations given to them by an administrator were not loaded. Further, if new users were hired into an organization, administrators needed to manually load a set of personalizations for the user. There was no automatic mechanism for specifying that a certain set of personalizations should be available for users in that role.

The saved views feature makes organizational management of personalizations significantly easier, primarily because views can be published to groups of users. After a view has been published, any user who has one of the defined security roles and has access to one the specified legal entities will be able to see and use the view, even users without access to personalization. Although each user has a copy of the published view where page usage are automatically applied, no user can save personalizations or query updates to a published view; in other words, published views are locked. Additionally, if new users are given roles in legal entities that views were published to, they will automatically see the views that are associated with their roles and legal entities. No additional action is required by the administrator. Likewise, if users change roles in an organization or are given access to different legal entities, they may no longer be able to access the views that were previously published to them. Again, no additional action is required by the admin.

Updates to a published view can easily be distributed to users by republishing the view to the appropriate security roles and legal entities.

The publish capability allows organizations to define corporate standard views that are optimized for their business, targeted at users in specific security roles.  

## Publishing views
During the publish process, views can be assigned to one or more security roles for one or more legal entities. Therefore, any user who has access to a legal entity and who is assigned to one of those roles can access and use the views, although they can't edit them. By default, system admins have access to the **Publish** action in the view selector drop-down menu; however, other trusted users in your organization can also be given access to view publishing via the new **Saved views administrator** role.

To publish a view, follow these steps: 
1.	Create and save a personal copy of the view that you want to publish. 
2.	With that view currently loaded, select the view name to open the view selector drop-down menu. 
3.	Select the **More** button and then select **Publish**. The Publish dialog box will open.  
4.	Enter a name and (optionally) a description for the view. The name that you enter is the name that users who receive this view will see in their view selectors. The names of published views for a page must be unique. No duplicate names are allowed, even if the list of roles or legal entities that the views are applied to differ.
5. [10.0.9 / Platform update 33 or later] Determine if the view should be published as the default view for the selected users. Making a view the default means that this is the view users will see the next time they open the target page. This will modify the default view for these users; however, users can still change their default view after the publish has occurred.    
6.	Add the security roles that correspond to the users being targeted by this view. 
7. [10.0.13 / Platform update 37 or later] For each security role selected, determine if you want to publish the view to the child roles of that security role. If so, mark the "Include child roles" checkbox in the appropriate rows. Note this checkbox is disabled for roles without child roles.   
7. Add the legal entities that this view should be available for. 
8.	Select **Publish**.

Note that in some environments, it may take some time (up to an hour) before users see the published view.

## Modifying a published view
After publishing a view, you may discover that you want to make changes to a published view. While you cannot make live changes to a published view because these views are locked for editing for all users (including publishers), you can re-publish a view to make updates.  

If the changes that you want to make to a published view only involve the publish parameters (the name and description of the view, or the security roles the view is published to), do the following: 
1.	Switch to the published view for the parameters that you want to update. 
2.	Select **Republish** from the view selector drop-down menu. If you are on an older version (10.0.12 / Platform update 36 or earlier), you will need to select **Publish** and then **Yes** to update the existing view.
4.	Update the name, description, security roles, and legal entities for the view. 
5.	Select **Publish**. 
6.	[10.0.8 / Platform update 32 or prior] If you updated the name of the published view, you'll also need to delete the published view with the old name (see the **Managing published views** section for more details). 
7. [10.0.9 / Platform update 33 or later] If you had originally chosen this published view to be the default view, it will be the default view for these users again after the re-publish.  

If the changes to the published view involve modifying the personalizations or filters associated with the view, follow these steps: 

[10.0.13 / Platform update 13 or later] Make the view with needed changes directly. You should see an asterisk next to the view name
1.	Load the published view that you want to modify. 
2.	Modify the local draft with the needed changes.
3. Select **Republish** from the view selector 
4. Select Yes to indicate you want to published the view with its unsaved changes. 
5.	Adjust any publish parameters and select **Publish**. 

[10.0.12 / Platform update 12 or prior]
1.	Load the published view that you want to modify. 
2.	Save a copy of the published view to create a local draft of the published view. 
3.	Modify the local draft with the needed changes.
4.	Publish the view with the original name. 

## Managing published views
Like managing personal views, the **Manage my views** dialog box gives users with publish privileges basic maintenance capabilities over that page's published views (in addition to their own personal views). To open this page, select the view name to open the view selector drop-down menu, select **More**, and then select **Manage my views**.

While all users see a **My views** tab showing their personal views, users with publish privileges also see an **Organization views** tab that shows all the published (and unpublished) views for that page. Because there may be several users publishing views, it is important to be able to manage the full list of published views, regardless of whether you were the user who actually published the view.

For the list of all published views for the page, the following set of actions are available. 

-    **Republish** – Use the **Republish** action to republish a view after publish parameters (name, description, security roles, or legal entities) are changed.
-    **Publish** - Use the **Publish** action to publish a view that's currently unpublished. 
-    **Unpublish** - Use the **Unpublish** action to make a view inactive. The view will still be available in the system, but users will not see it in the view selector until the view is published again.  
-    **Save as personal** – Use the **Save as personal** action to create a personal draft copy of the published view. This capability can help you understand the contents of a view that wasn't published to you or that hasn't yet been published. You can also use it to edit and then republish a view. This capability is introduced in version 10.0.12.  
-    **Delete** – Use the **Delete** action to permanently delete a published or unpublished view. This action also removes the view for all users in the system. Removing published views will take effect after the **Save** button is selected. Once deleted, the view cannot be recovered. 

## Managing views globally
Although some management capabilities are surfaced on every page, as indicated in this topic, **system administrators** and **saved view administrators** can manage views more holistically for the system via the **Personalization** page. In particular, this page has the following sections and capabilities: 

- **Published views** – This section lists all views that have been published for your organization. From here, you can republish a view after you adjust the security roles or legal entities that the view targets. You can also export, delete, or unpublish views. In version 10.0.12 and later, you can use the **Save as personal** action to create a personal copy of the view, so that you can update the view or gain a better understanding of its contents. 
- **Unpublished views** – This section lists all the organization views in your system that are not currently published. These most often come into the system by the import capability. You can publish, export, or delete these views. The **Quick publish** action that was added in version 10.0.12 enables multiple views from this section to be published in one action, by using the existing security role and legal entity configurations. In version 10.0.12 and later, you can use the **Save as personal** action to create personal copies of these views, so that you can gain a better understand their contents.   
- **Personal views** – This section lists all views that have been created by users in the system. From here, you can publish a personal view to the organization, or copy one or more of these views to other users. You can also export or delete these views as required.
- **User settings** – Select a user to view or adjust the user's ability to use personalization for the whole system, or for specific pages that user has visited. You can view and interact with that user's personalizations in the system. You can also delete all personalizations for that user or reset feature callouts for the user. If feature callouts are reset, any pop-up windows that introduced new features that were previously dismissed by the user will appear again the next time that the user encounters those features.
- **System settings** – You can temporarily turn off personalization for all users in the system. In this case, no personalizations are applied for any user, and all pages are reset to their default state. If you turn personalization back on later, all personalizations are reapplied. You can also permanently delete all personalizations for all users in the system. Personalizations that have been deleted can't be recovered. Therefore, before you perform this task, be sure to export any personalizations that you might want later.

Users who have access to the **Personalization** page can also import personal or organization views by using the **Import views** button on the Action Pane. In version 10.0.12 and later, a mechanism has been added for immediately publishing views when they are imported.  

## Frequently asked questions
### How do I enable saved views in my environment? 
> [!NOTE]
> The **Saved views** feature requires the Personalization system in Finance and Operations to be enabled. If personalization is turned off for the entire environment, views will be disabled even if you follow steps below. 

**10.0.13 / Platform update 37 and later**
The **Saved views** feature is no longer in preview and is available directly in Feature management in any environment.

**10.0.9 / Platform update 33 through 10.0.12 / Platform update 36**
The **Saved views** feature is available directly in Feature management in any environment. As for other preview features, enabling this feature in production is subject to the [Supplemental Terms of Use Agreement](https://go.microsoft.com/fwlink/?linkid=2105274).  

**10.0.8 / Platform update 32 and prior**
The **Saved views** feature can be enabled in Tier 1 (Dev/Test) and Tier 2 (Sandbox) environments in order to provide additional testing and design changes by following the steps below.

1.	**Enable the flight**: Execute the following SQL statement: 

    `INSERT INTO SYSFLIGHTING (FLIGHTNAME, enabled, FLIGHTSERVICEID, PARTITION) VALUES('CLISavedViewsEnableFeature', 1, 0, 5637144576);`

2. **Reset IIS** to flush the static flighting cache. 

3.	**Find the feature**: Go to the **Feature management** workspace. If **Saved views** does not appear in the list, select **Check for updates**.   

4.	**Enable the feature**: Find the **Saved views** feature in the list of features, and select **Enable now** on the details pane.

All subsequent user sessions will start with saved views enabled.


### What happens to existing personalizations when views are enabled? 
When views are enabled, any existing personalizations for a user and form are saved into a new view called **My view** that is automatically set as the default view. This is meant to ensure that there is a consistent user experience before and after views are enabled, except for the view selector control appearing on forms.  

### What pages support views? 
Views are available on most, but not all pages. Specifically, views are currently available on all full-screen pages except for dashboards and workspaces. Non-full-screen pages, which include dialog boxes, drop-down dialogs, lookups, enhanced previews, currently do not support views. View support for additional page types, such as workspaces and dialog boxes, may be considered for a future update.   

### Who is allowed to publish views?
Only system admins and users who have been assigned to the **Saved views administrator** role have the rights to publish views. 

### Why am I not able to save filters with this view? 
There are a few reasons why a filter may not appear to save with a view: 

- The page may not support saving filters as part of the view definition. Note that only pages with large view selectors allow personalizations and query modifications to be saved as a view. See the **Switching views** section for more information. 

- The page in question may not properly support views, as it may ignore the view query completely or may operate on a temporary table whose data is not persistent. 

### What data will I see when I visit a page? 
For pages with small view selectors (only personalizations can be saved to the view), you will see the same data as you always have when you visit the page. 

For pages with large view selectors (personalizations and queries can be saved to the view), you will typically see the data linked to the query associated with your default view. There are two main exceptions to this: 
     - If you navigate to a page from a tile, the tile query will execute regardless of the query associated with the default view. If you created that tile after views have been enabled, selecting a tile will open the page with the view associated with that tile.   
     - If you navigate to a page and that entry point includes a query, the original query will execute originally in place of the default view's query. You should be alerted when this occurs via an informational message when the view is loading. You can also confirm by switching to this view after the page loads, as that should allow the view query to execute regardless.  


