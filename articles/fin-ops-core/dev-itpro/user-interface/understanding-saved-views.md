---
title: Build forms that fully utilize saved views
description: This article explains some of the technical aspects of saved views and describes considerations with form development to ensure forms work well with saved views.
author: jasongre
ms.date: 01/30/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2019-07-31
ms.dyn365.ops.version: Platform update 28
ms.search.form: SysUserSetup, DefaultDashboard
---

# Build forms that fully utilize saved views

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Saved views are an important expansion of personalization capabilities finance and operations applications. While the [Saved views](../../fin-ops/get-started/saved-views.md) article provides general details about this feature, this article focuses on the more technical elements of saved views as well as aspects of form development that may be impacted by views. 

## "User-perceived" pages
Traditionally, a set of personalizations has a 1:1 link to a modeled form. For many pages, this makes sense to the user, as the user's perception of the page matches the way in which the form is modeled. However, in some cases the 1:1 link of a modeled form to a set of personalizations is not intuitive or obvious because users do not see or care about the boundaries between modeled forms. 

Saved views try to eliminate this confusion by letting users create views on "user-perceived" pages. Therefore, users don't have to understand how forms are modeled to understand how and when personalizations are applied. Consider the following two scenarios:

- **More than one "user-perceived" page in a single modeled form:** The standard modeling of Master Details and Transaction Details forms (for example, the **CustTable** and **PurchTable** forms, respectively) consists of more than one "user-perceived" page: a grid page and a details page. 

    Because users are not aware when this transition from list to details crosses a form boundary (nor do they need to know this), view support in Details forms is handled differently to allow views to be defined separately for the grid and details portions. This means that the view selector for the "grid" and "details" can show different sets of available views. The special casing of view support on these forms also allows the "grid" views to allow filters in their view definitions, whereas the "details" view only needs personalizations.

- **More than one modeled form in a single "user-perceived" page:** The ability to embed subforms into modeled forms (via FactBoxes or form parts) leads to situations where more than one modeled form corresponds to a single "user-perceived" page. For example, consider the details portion of the **All customers** page, which has a number of FactBoxes and two FastTabs whose contents come from form parts. With traditional personalization, contrary to a user's expectations, exporting the personalizations for the **CustTable** form would not include personalizations on any FactBox or any personalizations done inside the **Addresses** or **Contact information** FastTabs. Equally unexpected for users, any personalizations done on these subforms would also be reflected in other parts of the application where these form parts are used. For example, changes to the **Addresses** FastTab on the **All customers** page would also result in the same changes appearing on the **Addresses** FastTab on the **All vendors** page.

    With views, the personalization scope of form parts has been modified to match user expectations. In particular, subform personalizations are now tied to the base form where they are made. This means that exporting a view on the **All customers** details page will include personalizations from the base **CustTable** form as well as any personalizations in FactBoxes or form parts modeled in that portion of the form. Similarly, any personalizations done on the **Addresses** FastTab (form part) on the **All customers** page will not be reflected in other forms where that form part is used.

These are highly technical modifications to the personalization subsystem that are only available when view is enabled. These modifications are important for ensuring that users have a predictable and understandable experience with views.

## View support
The style of a form determines the level of support for views.

- Views include queries for these form types:

    - List pages (Design.Style = ListPage)
    - Simple lists (Design.Style = SimpleList)
    - Grid portions of Master Details and Transaction Details forms (Design.Style=ListPage)
    - Task single and Task double pages (Design.Style or Design.Pattern = TaskSingle or TaskDouble)

- Views don't include queries for these form types:

    - Any other full-page form that wasn't listed earlier in this section
    - Workspaces

        The "Saved views support for workspaces" feature enables saved views to be defined and shared for both modeled workspaces and user-created workspaces.

    - Dialogs
    - Details portions of Master Details and Transaction Details forms

- Views aren't currently supported on these form types:

    - Dashboards
    - Secondary forms like drop-down dialogs, lookups, and enhanced previews

## Modifying forms to fully utilize views
While most forms will work well with saved views, there are some areas that may require changes to form logic so that views work as expected on these forms without causing confusion. Here are some key items to keep in mind during development of new forms.

### Custom filters
Custom filters are controls that are modeled on forms and that cause modifications to the query. Users will have a suboptimal user experience if the integration between views and these custom filters isn't implemented. For example, the views might not be marked as having unsaved changes after a custom filter is used, or the custom filter value might not always be aligned to the current view or query.

Form owners can provide better experiences with custom filters by taking advantage of the following two methods. These methods were introduced specifically to improve custom filter support with saved views.

- **public void queryFiltersChanged():** This new method is called when the query is rerun by the system after changes to the query (for example, when a view loads or a system filtering mechanism is used). Therefore, the custom filter control has an opportunity to interrogate the mostly recently run query to find any relevant filter and update its value so that it appropriately reflects that query.
- **element.formCustomFilterChanged():** This new API is called by the custom filter control when it has changed the query on the user's behalf. When it's called, the system marks the view definition as having unsaved changes. The recommendation is to call this API at the end of the control's **modified()** method if changes to the control immediately cause the query to be refreshed, or to call this API for a custom filter on a button click if the adjustment of one or more custom filters requires a button for the changes to take effect.

### Relative filter values
Forms might have to use relative filter conditions to retrieve the appropriate information when the page is loaded. For example, they often have to use filter conditions to restrict data for the current user, current date, and current legal entity. If a form hard-codes a filter to a specific value, any view that is saved with that filter might have issues showing the intended data or being shared with other users. For example, a form hard-codes a "current date" filter to a specific date, that query is saved to a view, and the view is shared with another user. In this case, the view might provide unexpected results, because it will still try to retrieve data from the hard-coded date in the past instead of the current date. Or a filter condition was intended to represent the current user but was hard-coded to a specific user. In this case, when the view is shared with another user, an error might occur when that user tries to load or import the view. 

To help avoid this situation, forms that have relative filter conditions should have filter values that use **SysQueryRangeUtil** methods in combination with the finance and operations [advanced filter syntax](../../fin-ops/get-started/advanced-filtering-query-options.md), specifically the syntax where a filter value is enclosed in parentheses. Evaluation of the filter method will then be deferred until the query is run. Therefore, relative filtering conditions can be used in views and passed between users without causing issues. Users in the user interface can use this same syntax in conjunction with the "matches" operator to achieve the same effect.  

As an explicit example, consider a form that has a filter condition on a **User** field. If the filter value is set to **currentUserId()**, the function will be evaluated immediately, and the hard-coded user name will be used in the query. If a simple change is made to the filter value, so that it's set to **(currentUserId())** instead, the function will be saved to the query definition. Therefore, a view that has this condition can be saved to views and passed to other users without causing issues.  

Here are some typical examples. 

| Description | Filter value |
|---|---|
| Current user | (currentUserId()) |
| Current legal entity | (currentCompany()) |
| Today | (Day(0)) |
| Yesterday | (Day(-1)) |

For more relative date queries, see [Advanced date queries that use SysQueryRangeUtil methods](../../fin-ops/get-started/advanced-filtering-query-options.md#advanced-date-queries-that-use-sysqueryrangeutil-methods).

### Improved developer control over the handling of default queries with views

#### Giving the default view priority over a menu item query
By default, if a user navigates to a page by using a menu item that has an associated query, the system will run the menu item's query instead of the default view's query. In this case, the user is notified by an informational message that includes an action to force load the default view's query.

In version 10.0.32, a new extension point has been added to enable form developers to override this default system behavior for individual forms. Specifically, developers can call the **EnableSavedViewQueryPriority** method from the **FormRunPersonalizationSettings** class before **super()** of **init()** during the form lifecycle to give the default view's query priority over the menu item's query. 

When this behavior is enabled, the system will try to merge the default view's query with the menu item's query during the **run()** portion of the lifecycle. 

#### Manually handling query merge failures
As part of the default view rollout during form load, the query that's associated with the default view goes through a merge process with the default form's query (or the default menu item's query if the **EnableSavedViewQueryPriority** method has been invoked). A failure to merge the queries indicates an incompatibility, from the system perspective, between the view's query and the form's (or menu item's) query. This incompatibility can occur if, for example, the view adds a filter on a field that a hidden or locked filter is already applied to.

The form might have additional context that enables this incompatibility to be resolved, so that the view's query can be correctly merged as the user expects. In version 10.0.32, a new extension point has been added to give developers a fallback method for making these adjustments when they're required. Specifically, if the standard query merging fails, developers can replace the implementation of the **OnFailureQueryPersonalizationApply** method to make the required modifications to the target query. The `_sourceQuery` parameter provides the view's query, and the `_targetQuery` represents the query that will be run when the view that has a query personalization is loaded. 

```
[Replaceable]
public boolean OnFailureQueryPersonalizationApply(Query _sourceQuery, Query _targetQuery)
{
    return false;
}
```

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

## Improving form load performance

Traditionally, personalizations have been applied during the **super()** of **run()**, after the form query has been initially run. Because of this timing, if personalizations included an added field, the query might be rerun to ensure that the extra data was fetched. With saved views, personalizations that are related to the default view were applied at the same time as before. However, the possibility of at least one extra execution of the query during form load increased, because an extra execution occurred if the default view contained any personalizations that affected the query. These personalizations include added fields, modified filters, and modified sorting.

As of version 10.0.29, you can use the **Saved views performance enhancement** feature to help improve the performance of form load for default views that contain personalizations that affect the query. This feature changes when some parts of the default view are applied, so that all query-related changes (such as added fields, modified filters, and modified sorting) are in place when the form initially runs its query in **super()** of **run()**. Therefore, the system runs the form query only once during form load, instead of potentially multiple times. In this way, the feature can speed up the load time for forms.

However, because this feature changes when some personalizations that are associated with the default view are applied, the behavior on the page might change. In particular, any code that affects the query in the **OnPostRun** event handler of the form will now be run after the view query is run, not before. Therefore, before you enable the feature, you should evaluate any query-affecting code in the **OnPostRun** event handler in forms.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

