---
title: Saved views
description: Learn about how to use the saved views features, including overviews on switching between views, changing default views, and creating and modifying views.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/27/2024
ms.reviewer: twheeloc
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-07-31
ms.search.form: DefaultDashboard
ms.custom: 
  - bap-template
---

# Saved views

[!include [banner](../../../finance/includes/banner.md)]

Personalization plays an important role in allowing users and organizations to optimize the user experience to meet their needs. For more information on personalization, see [Personalize the user experience](personalize-user-experience.md).

Traditional personalization allows users to only have one set of personalizations per page. *Saved view* features expand on personalization in several important ways:

- Views permit users to have multiple named sets of personalizations per form that they can quickly switch between as needed. This feature allows a user to create multiple optimized views of a page, where each view is tailored to fit the needs of performing a particular business task. 
- Views created for particular page types can also include user-added filters or sorts, which allows users to quickly return to commonly filtered datasets. For more information, see [What pages support views](#what-pages-support-views). 
- Views can be published to users in specific security roles and specific legal entities. Therefore, any user who has a specified role and access to a specified legal entity can access and use that view, even if that user doesn't have permission to personalize. This publish capability lets organizations define corporate, standard views that are optimized for their business. For more information, see the [Managing personalizations at an organizational level with views](#managing-personalizations-at-an-organizational-level-with-views) section.
- Unlike traditional personalization, views aren't automatically saved when a user performs personalizations or filters a list. Explicit saves are required to give users the flexibility to create a view before or after the changes that are associated with that view are made. This requirement also ensures that view definitions aren't unintentionally changed by filters or personalizations that aren't intended for long-term use. Items that the system automatically stores as part of typical page usage (for example, column widths, or the expanded or collapsed state of sections) are saved per view.
- Views can be added to workspaces as tiles, lists, or links. Therefore, a filtered data set can be surfaced in a workspace, and users can associate a set of personalizations that is relevant to that data set with a tile or link.

## Switching between views

After views are made available for an environment, the top of any page that supports views includes a collapsed view selector control that shows the name of the current view.

There are two size variations to the view selector: 

- **Large view selectors** – Pages that prominently feature a list have a larger view selector for a few reasons. Most importantly, the larger view selector indicates the pages where the view can include user-defined filters and sorts. Because filters and sorts are included in the views, the larger selector size is also warranted as the view names is often the best description of the data that is shown on the screen and the expectation is that users switch between views more often on these page types. Grouping in a grid can also be saved to views on a page with large view selectors. 
- **Small view selectors** – All other full-screen pages (except workspaces and the dashboard) have a smaller view selector that appears next to the page caption. Views on these pages include only personalizations, not user-defined filters. On these pages, the caption or record title is often the most important information at the top of the page. The smaller size of the view selector also reflects the lower frequency of view switching that is expected on these pages. 
 
If you select the view name, the view selector opens and shows the list of available views for the page in up to two sections. The first section shows any views that are specific to the current legal entity, and the second section shows views that are available to all legal entities. The first section is only visible if there are legal entity–specific views for the page.

- **Standard view** – The **Standard** view is the out-of-box view of the page, where no personalizations are applied.
- **Personal views** – The views without padlocks represent your personal views. These are views that you created or that an administrator has provided to you.
- **Locked views** – Some views (such as the **Standard** view and any views that are published to your role) have a padlock symbol next to them in the view selector. This symbol indicates that you can't edit those views. However, changes that reflect page usage are automatically saved. These changes include changes to the width of a grid column, and changes to the expanded or collapsed state of a FastTab. Nevertheless, if you have personalization privileges, you can use the **Save as** action to make a personal view that is based on a locked view.
- **New views** – Published views that haven't been opened have a spark symbol to the left of the view name.

To switch to a different view, first open the view selector and then select the view that you want to load. 

## Creating and modifying views

Unlike traditional personalization, views aren't automatically saved when a user personalizes the page, or when a user applies a filter to a list or sorts it. An explicit action is required to save these changes to a view. This requirement gives users the flexibility to create a view before or after the changes that are associated with that view are made. It also ensures that view definitions aren't unintentionally changed by one-time filters or personalizations. Typical page usage items (for example, column widths, or the expanded or collapsed state of sections) are automatically saved to the current view, even for locked views.

To ensure that the current state of the view is known, when you start to change a view by personalizing or filtering it, an asterisk (\*) appears next to the current view name. This symbol indicates that you're looking at an unsaved, modified version of that view.

If you want to save those changes, follow these steps.

1. Select the view name to open the view selector.
2. To modify the existing view, select **Save**. This action isn't available for locked views. 
3. To create a new view:

    1. Select **Save as**. 
    2. In the **Save view as** pane, enter a name and, optionally, a description for the view.
    3. If you want this view to be your default view, select **Pin as default**. For more information about default views, see [Changing the default view](#changing-the-default-view). 
    4. Optional: Select whether you want this view to be available for just a subset of legal entities. The default behavior is that views are saved as global views. 
    5. Select **Save**.

## Changing the default view

The default view is the view that the system tries to open when you first open the page. You should set the default view to the view that you expect to use most often. 

To change the default view for a page, follow these steps:

1. Switch to the view that you use as the default. 
2. Select the view name to open the view selector. 
3. Select **More** and then **Pin as default**.

> [!NOTE]
> - If the view is specific to one or more legal entities, it becomes the default view for those legal entities.
> - If the view is global, it becomes the default view for legal entities that don't have a legal-entity specific default view defined. 

Alternatively, when you create a new view (by using the **Save as** action), you can make that new view the default view by setting the **Pin as default** option before you save the view.

> [!WARNING]
> In some cases, the query that is associated with the default view isn't run when you first open a page. For example, if you open the page through a tile, the tile's query will be run, regardless of the query that is associated with the default view. Additionally, if you open a page that has a **standard** view that already has a defined query, the original query will be run instead of the default view's query. In this case, you receive an informational message when the view is loaded with an embedded action that lets you load the default view's query directly. If you switch views after the page has been loaded, the view query should be able to be run as expected. 

## Managing personal views

The **Manage my views** dialog box gives you basic maintenance capabilities over your personal views and the order of views in the view selector. To open this page, select the view name to open the view selector drop-down menu, select **More**, and then select **Manage my views**.

The **My views** section of the **Manage my views** dialog shows the available views for the page in sections. Any views that are specific to the current legal entity are displayed in their own section. The **Global views** section is always displayed so you can manage the available views for the page in all legal entities. 

For a list of available views for that page, the following set of actions are available.

- **Change the default view** – Use the **Pin as default** action to make the currently selected view the default view for the page. When you take this action on a view in the **Global views** section, you can choose to make the view the default view for either the current legal entity or all legal entities.
- **Reorder your views** – Use the **Move up** and **Move down** actions to rearrange your views in a specific order.
- **Rename a view** – Use the **Rename** action to change the name of the currently selected personal view. This action is turned off for locked views. 
- **Delete a view** – Use the **Delete** action to permanently delete the currently selected view from the page. There's no way to recover a view after you remove it.

Any changes made in this dialog box will take effect after you select the **Update** button.

## Managing personalizations at an organizational level with views

To help you understand how saved views help improve management of personalizations at an organizational level, this section describes some differences in personalization management for pages that do and don't support saved views.

When views aren't available, administrators can apply a set of personalizations for a page to a user or a group of users via the **Personalization** page. However, administrators have no ability to prevent users from further personalizing the page, which means the organization can't ensure that its users have a consistent user interface on that page. If new users are hired into an organization, administrators must manually load a set of personalizations for each new user because there's no automatic mechanism for specifying that a certain set of personalizations should be available for users in that role.

> [!NOTE]
> If the administrator applies personalizations to a user without personalization rights, the personalizations given to them aren't applied and don't impact the user interface.   

With saved views, organizational management of personalizations is easier because views can be published to groups of users. After a view is published, any user who has one of the defined security roles and access to one of the specified legal entities can see and use the view, even if that user doesn't have access to personalization. These published views can't be edited by users, although users with personalization rights can create their own personal views starting from a published view definition. If new users are assigned to roles in legal entities to which views were published, they automatically see the views associated with their roles and legal entities. No additional action is required by the administrator. Likewise, if users change roles in an organization or are given access to different legal entities, they may no longer be able to access the views that were previously published to them. Again, no additional action is required by the administrator.

Updates to a published view can easily be distributed to users by republishing the view to the appropriate security roles and legal entities.

The publish capability allows organizations to define corporate standard views that are optimized for their business, targeted at users in specific security roles.

## Publishing views

During the publishing process, views can be assigned to one or more security roles for one or more legal entities. Therefore, any user who has access to a legal entity and is assigned to one of those roles can access and use the views. However, the user can't edit the views. By default, system admins have access to the **Publish** action in the view selector drop-down menu. However, other trusted users in your organization can also be given access to view publishing via the new **Saved views administrator** role.

To publish a view, follow these steps:

1. Create and save a personal copy of the view that you want to publish. 
2. With that view currently loaded, select the view name to open the view selector drop-down menu. 
3. Select the **More** button and then select **Publish**. The **Publish** dialog box opens.
4. Enter a name for the view. The name that you enter is the name that users who receive this view see in their view selectors. The names of published views for a page must be unique. No duplicate names are allowed, even if the list of roles or legal entities that the views are applied to differ.
5. Optional: Add translations for your view name in as many languages as your organization requires by selecting the **Translations** button next to the **Name** field. The view name is then shown to users in their current language. You can also set the default language to specify the translation that is shown to users who are running languages that no translation is defined for.
5. Optional: Enter a description for the view, so that users who receive this view can understand its purpose. 
6. Determine whether the view should be published as the default view for the selected users. When a view is made the default view, users see it the next time that they open the target page. However, users can still change their default view after publishing has occurred.

    > [!NOTE]
    > Be aware of the following behavior when you publish a view as the default view:
    > - If you publish the view as the default for all legal entities, this overrides any legal entity default view a user has previously set. 
    > - If you publish the view to a subset of legal entities, the default view for those legal entities is changed for every targeted user.
    > - If a user has roles where multiple views are published as the default view, the last view that was published is used as the user's default view. 
    > - Publishing doesn't work for role assignments made using Microsoft Entra groups. 

8. Add the security roles that correspond to the users who are being targeted by this view. 
9. Determine whether you want to publish the view to the child roles of each security role that is selected. If you do, select the **Include child roles** checkbox in the row for the appropriate security roles. This checkbox isn't available for roles that don't have child roles.
10. Add the legal entities that this view should be available for. 
11. Select **Publish**.

In some environments, it may take up to an hour before users see the published view.

> [!NOTE]
> Published workspace views don't appear in the view selector for the original workspace. Instead, published workspace views follow the pattern of published embedded apps and appear as new tiles on the dashboard.

## Modifying a published view

After you publish a view, you might find that you want to change it. Although you can't make live changes to a published view, because these views are locked for editing for all users (including publishers), you can republish a view to update it.

If the changes that you want to make to a published view only involve the publish parameters (the name and description of the view, or the security roles the view is published to), follow these steps.

1. Switch to the published view for the parameters that you want to update. 
2. On the view selector drop-down menu, select **Republish**. If you're using version 10.0.12 or earlier, you must select **Publish** and then **Yes** to update the existing view.
3. Update the name, description, security roles, and legal entities for the view. 
4. Select **Publish**. If you originally selected this published view as the default view, it will be the default view for users again after you republish it. 

If the changes to the published view involve modifications of the personalizations or filters that are associated with the view, follow these steps.

1. Load the published view that you want to change. 
2. Make the required changes to the local draft.
3. On the view selector drop-down menu, select **Republish**.
4. Select **Yes** to indicate that you want to publish the view together with its unsaved changes. 
5. Adjust any publishing parameters that require adjustment, and then select **Publish**. 

## Managing published views

Like managing personal views, the **Manage my views** dialog box gives users with publish privileges basic maintenance capabilities over that page's published views (in addition to their own personal views). To open this page, select the view name to open the view selector drop-down menu, select **More**, and then select **Manage my views**.

Although all users have a **My views** tab that shows their personal views, users who have publish privileges also have an **Organization views** tab that shows all the published and unpublished views for that page. Because several users might be publishing views, it's important that you are able to manage the full list of published views, even if you aren't the user who published a given view.

For the list of all published views for the page, the following set of actions are available. 

- **Republish** – Use the **Republish** action to republish a view after publishing parameters (name, description, security roles, or legal entities) are changed.
- **Publish** – Use the **Publish** action to publish a view that is currently unpublished. 
- **Unpublish** – Use the **Unpublish** action to make a view inactive. The view is still available in the system, but users don't see it in the view selector until the view is published again.
- **Save as personal** – Use the **Save as personal** action to create a personal draft copy of the published view. This capability can help you understand the contents of a view that wasn't published to you or that hasn't been published. You can also use it to edit and then republish a view.
- **Delete** – Use the **Delete** action to permanently delete a published or unpublished view. This action also removes the view for all users in the system. The removal of published views takes effect after the **Save** button is selected. After a view is deleted, it can't be recovered. 

## Managing views globally

Although some management capabilities are surfaced on every page, as indicated in this article, **system administrators** and **saved view administrators** can manage views more holistically for the system via the **Personalization** page. In particular, this page has the following sections and capabilities: 

- **Published views** – This section lists all views that have been published for your organization. From here, you can republish a view after you adjust the security roles or legal entities that the view targets. You can also export, delete, or unpublish views. You can use the **Save as personal** action to create a personal copy of a view, so that you can update the view or gain a better understanding of its contents. 
- **Unpublished views** – This section lists all the organization views in your system that aren't currently published. These views most often come into the system through the import capability. You can publish, export, or delete these views. The **Quick publish** action that was added in version 10.0.12 enables multiple views from this section to be published in one action, by using the existing security role and legal entity configurations. You can use the **Save as personal** action to create personal copies of these views, so that you can gain a better understanding of their contents.
- **Personal views** – This section lists all views created by users in the system. From here, you can publish a personal view to the organization, or copy one or more of these views to other users. You can also export or delete these views as required.
- **User settings** – Select a user to view, or adjust the user's ability to use personalization either for the whole system or for specific pages that the user has visited. You can view and interact with the user's personalizations in the system. You can also delete all personalizations for that user or reset feature callouts for the user. If feature callouts are reset, any pop-up windows that introduced new features and that the user previously dismissed will appear again the next time that the user encounters those features.
- **System settings** – You can temporarily turn off personalization for all users in the system. In this case, no personalizations are applied for any user, and all pages are reset to their default state. If you turn personalization back on later, all personalizations are reapplied. You can also permanently delete all personalizations for all users in the system. Deleted personalizations can't be recovered. Therefore, before you perform this task, be sure to export any personalizations that you might want later.

Users who have access to the **Personalization** page can also import personal or organization views by using the **Import views** button on the Action Pane. For organization views, you can select **Publish immediately** to make the views available to users without an additional explicit publish.

## Frequently asked questions

### What pages support views? 

Views are available on most but not all pages. Specifically, views are currently available on all full-screen pages except dashboards. View support for workspaces is available through the **Saved views support for workspaces** feature. Most pages that aren't full screen (for example, drop-down dialogs, lookups, and enhanced previews) don't currently support views. 

### Who is allowed to publish views?

Only system admins and users who are assigned to the **Saved views administrator** role have the rights to publish views. 

### Why am I not able to save filters with this view? 

There are a few reasons why a filter may not appear to save with a view: 

- The page may not support saving filters as part of the view definition. Only pages with large view selectors allow personalizations and query modifications to be saved as a view. 
- The page in question may not properly support views, as it may ignore the view query completely or may operate on a temporary table whose data isn't persistent. 

### What data do I see when I visit a page?

For pages that have small view selectors (only personalizations can be saved to the view), you see the same data as you always have when you visit the page. 

For pages that have large view selectors (both personalizations and queries can be saved to the view), you typically see the data that is linked to the query that is associated with your default view. There are two main exceptions:

- If you navigate to a page from a tile, the tile query executes regardless of the query associated with the default view. If you created that tile after views are enabled, selecting a tile opens the page with the view associated with that tile.
- If you navigate to a page and that entry point includes a query, the original query executes instead of the default view's query. You should be alerted when this occurs via an informational message when the view is loading. You can also confirm by switching to this view after the page loads, as that should allow the view query to execute regardless.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
