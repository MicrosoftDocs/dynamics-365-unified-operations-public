---
# required metadata

title: Build forms that fully utilize saved views
description: This topic explains some of the technical aspects of saved views and describes considerations with form development to ensure forms work well with saved views.
author: jasongre
ms.date: 02/08/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysUserSetup, DefaultDashboard
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2019-07-31
ms.dyn365.ops.version: Platform update 28

---

# Build forms that fully utilize saved views

[!include [banner](../includes/banner.md)]

Saved views are an important expansion of personalization capabilities Finance and Operations applications. While the [Saved views](../../fin-ops/get-started/saved-views.md) topic provides general details about this feature, this topic focuses on the more technical elements of saved views as well as aspects of form development that may be impacted by views. 

## "User-perceived" pages
Traditionally, a set of personalizations has a 1:1 link to a modeled form. For many pages, this makes sense to the user, as the user's perception of the page matches the way in which the form is modeled. However, in some cases the 1:1 link of a modeled form to a set of personalizations is not intuitive or obvious because users do not see or care about the boundaries between modeled forms. 

Saved views try to eliminate this confusion by letting users create views on "user-perceived" pages. Therefore, users don't have to understand how forms are modeled to understand how and when personalizations are applied. Consider the following two scenarios:

- **More than one "user-perceived" page in a single modeled form:** The standard modeling of Master Details and Transaction Details forms (for example, the **CustTable** and **PurchTable** forms, respectively) consists of more than one "user-perceived" page: a grid page and a details page. 

    Because users are not aware when this transition from list to details crosses a form boundary (nor do they need to know this), view support in Details forms is handled differently to allow views to be defined separately for the grid and details portions. This means that the view selector for the "grid" and "details" can show different sets of available views. The special casing of view support on these forms also allows the "grid" views to allow filters in their view definitions, whereas the "details" view only need personalizations.

- **More than one modeled form in a single "user-perceived" page:** The ability to embed subforms into modeled forms (via FactBoxes or form parts) leads to situations where more than one modeled form corresponds to a single "user-perceived" page. For example, consider the details portion of the **All customers** page, which has a number of FactBoxes and two FastTabs whose contents come from form parts. With traditional personalization, contrary to a user's expectations, exporting the personalizations for the **CustTable** form would not include personalizations on any FactBox or any personalizations done inside the **Addresses** or **Contact information** FastTabs. Equally unexpected for users, any personalizations done on these subforms would also be reflected in other parts of the application where these form parts are used. For example, changes to the **Addresses** FastTab in the **All customers** page would also result in the same changes appearing in the **Addresses** FastTab in the **All vendors** page.

    With views, the personalization scope of form parts has been modified to match user expectations. In particular, subform personalizations are now tied to the base form where they are made. This means that exporting a view on the **All customers** details page will include personalizations from the base **CustTable** form as well as any personalizations in FactBoxes or form parts modeled in that portion of the form. Similarly, any personalizations done on the **Addresses** FastTab (form part) on the **All customers** page will not be reflected in other forms where that form part is used.

These are highly technical modifications to the personalization subsystem that are only available when view is enabled. These modifications are important for ensuring that users have a predictable and understandable experience with views.

## View support
The style of a form determines the level of support for views.

- Views include queries for these form types:

    - List pages (Design.Style = ListPage)
    - Simple lists (Design.Style = SimpleList)
    - Grid portions of Master Details and Transaction Details forms (Design.Style=ListPage)
    - Task single and Task double pages (Design.Style or Design.Pattern = TaskSingle or TaskDouble)

        As of version 10.0.25, the "Allow queries to be saved to views on Task Single and Task Double pages" feature adds query support for views that are defined on these form types.

- Views don't include queries for these form types:

    - Any other full-page form that wasn't listed earlier in this section
    - Workspaces

        As of version 10.0.25, the "Saved views support for workspaces" *preview* feature enables saved views to be defined and shared for both modeled workspaces and user-created workspaces.

    - Dialogs

        As of version 10.0.25, the "Saved views support for dialogs" feature enables saved views to be defined and shared for dialog pages.

    - Details portions of Master Details and Transaction Details forms

- Views aren't currently supported on these form types:

    - Dashboards
    - Secondary forms like drop-down dialogs, lookups, and enhanced previews

## Modifying forms to fully utilize views
While most forms will work well with saved views, there are some areas that may require changes to form logic so that views work as expected on these forms without causing confusion. Here are some key items to keep in mind during development of new forms.

### Custom filters
Custom filters are controls that are modeled on forms and that cause modifications to the query. Extra work is required to ensure that views are marked as having unsaved changes after a custom filter is used, and additional work might be required to ensure that the value of a custom filter is always aligned to the current view or query.

- Before version 10.0.25, only adjustments to the query (for example, filters and sorts) that were defined through the system-defined filtering mechanisms (Quick Filter, grid column headers, the Filter pane, or Advanced filter or sort) triggered a view to indicate that it had unsaved changes. If a custom filter was used to change the query, the view didn't appear to have unsaved changes (until the query was later modified by using one of the standard mechanisms). Additionally, if a view was loaded with a query modification that was related to a custom filter, the custom filter didn't reflect that modification. The result was a suboptimal user experience.
- As of version 10.0.25, form owners can provide better experiences with custom filters by taking advantage of the following two methods. These methods were introduced specifically to improve custom filter support with saved views.

    - **public void queryFiltersChanged():** This new method is called when the query is rerun by the system after changes to the query (for example, when a view loads or a system filtering mechanism is used). Therefore, the custom filter control has an opportunity to interrogate the mostly recently run query to find any relevant filter and update its value so that it appropriately reflects that query.
    - **element.formCustomFilterChanged():** This new API is called by the custom filter control when it has changed the query on the user's behalf. When it's called, the system marks the view definition as having unsaved changes. The recommendation is to call this API at the end of the control's **modified()** method if changes to the control immediately cause the query to be refreshed, or to call this API for a custom filter on a button click if the adjustment of one or more custom filters requires a button for the changes to take effect.

### Relative filter values
Forms might have to use relative filter conditions to retrieve the appropriate information when the page is loaded. For example, they often have to use filter conditions to restrict data for the current user, current date, and current legal entity. If a form hard-codes a filter to a specific value, any view that is saved with that filter might have issues showing the intended data or being shared with other users. For example, a form hard-codes a "current date" filter to a specific date, that query is saved to a view, and the view is shared with another user. In this case, the view might provide unexpected results, because it will still try to retrieve data from the hard-coded date in the past instead of the current date. Or a filter condition was intended to represent the current user but was hard-coded to a specific user. In this case, when the view is shared with another user, an error might occur when that user tries to load or import the view. 

To help avoid this situation, forms that have relative filter conditions should have filter values that use **SysQueryRangeUtil** methods in combination with the Finance and Operations [advanced filter syntax](../../fin-ops/get-started/advanced-filtering-query-options.md), specifically the syntax where a filter value is enclosed in parentheses. Evaluation of the filter method will then be deferred until the query is run. Therefore, relative filtering conditions can be used in views and passed between users without causing issues. Users in the user interface can use this same syntax in conjunction with the "matches" operator to achieve the same effect.  

As an explicit example, consider a form that has a filter condition on a **User** field. If the filter value is set to **currentUserId()**, the function will be evaluated immediately, and the hard-coded user name will be used in the query. If a simple change is made to the filter value, so that it's set to **(currentUserId())** instead, the function will be saved to the query definition. Therefore, a view that has this condition can be saved to views and passed to other users without causing issues.  

Here are some typical examples. 

| Description | Filter value |
|---|---|
| Current user | (currentUserId()) |
| Current legal entity | (currentCompany()) |
| Today | (Day(0)) |
| Yesterday | (Day(-1)) |

For more relative date queries, see [Advanced date queries that use SysQueryRangeUtil methods](../../fin-ops/get-started/advanced-filtering-query-options.md#advanced-date-queries-that-use-sysqueryrangeutil-methods).

### Opting forms out of views
Although this approach isn't generally recommended, as of version 10.0.25, developers can opt an individual form out of saved views support as required. In this case, no view selector will be available on the form, and there will be no publish capabilities.

To opt a form out of saved views support, put the following code before **super()** in the **init()** method of the form: 

this.disableSavedViewsOnForm();

### Code that can negatively affect views
X++ code late in the form startup cycle can interfere with the ability of views to work as users expect. In particular, be aware of the following items:

- Modifications of the query after **super()** of **executeQuery()** or after **super()** of **run()** can cause the query aspect of a view to be ignored.
- Form changes after **super()** of **run()** can cause some user personalizations to be incorrectly applied to the default view.

### Secondary list pages
In the long term, the plan is for views to replace modeled secondary list pages.

- Typically, secondary list pages, such as **Customers on hold**, are menu items that point to the same form but have a different query. Because menu items that pass in queries override any query that is defined on the default view, these entry points can cause confusion for users, because the default view query won't be run when users navigate to a form by using one of these menu items. The current long-term plan is to make secondary list pages obsolete (deprecated) and move them to views.
- To help prevent user confusion between the form caption (such as "All customers") and the view name (such as "My customers"), consider renaming form captions to the name of the corresponding entity. For example, instead of using "All customers" or "All sales orders" as a form caption, change the form caption to "Customers" or "Sales orders."

## Known issues
This section provides a list of known issues for saved views while the feature is in a preview state.

### Open issues
- [Resolved] A view isn't marked as having unsaved changes after custom filters are used. Custom filters are modeled filter controls above a grid (excluding the QuickFilter). If custom filter conditions have been saved to a view, the custom filter controls might not correctly reflect the current query. For more information about the resolution of this issue, see the [Modifying forms to fully utilize views](understanding-saved-views.md#modifying-forms-to-fully-utilize-views) section.
- [Resolved] View support for workspaces, dashboards, and dialog boxes. For more information about the resolution of this issue, see the [View support](understanding-saved-views.md#view-support) section.
- [Resolved] [KB 4582751] After fields (reference group fields) are added via personalization, the fields remain blank.
- If the Filter pane is open when switching to a different view, the Filter pane will not update to reflect the filters on the target view.
- Cannot move a view with a QuickFilter condition saved to it to another environment. The fix in release 10.0.13 more gracefully handles the situation, but does not allow these conditions to move between environments.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
