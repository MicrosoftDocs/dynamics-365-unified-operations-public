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

-    **More than one "user-perceived" page in a single modeled form:** The standard modeling of Master Details and Transaction Details forms (for example, the **CustTable** and **PurchTable** forms, respectively) consists of more than one "user-perceived" page: a grid page and a details page. 

     Because users are not aware when this transition from list to details crosses a form boundary (nor do they need to know this), view support in Details forms is handled differently to allow views to be defined separately for the grid and details portions. This means that the view selector for the "grid" and "details" can show different sets of available views. The special casing of view support on these forms also allows the "grid" views to allow filters in their view definitions, whereas the "details" view only need personalizations.

-    **More than one modeled form in a single "user-perceived" page:** The ability to embed subforms into modeled forms (via FactBoxes or form parts) leads to situations where more than one modeled form corresponds to a single "user-perceived" page. For example, consider the details portion of the **All customers** page, which has a number of FactBoxes and two FastTabs whose contents come from form parts. With traditional personalization, contrary to a user's expectations, exporting the personalizations for the **CustTable** form would not include personalizations on any FactBox or any personalizations done inside the **Addresses** or **Contact information** FastTabs. Equally unexpected for users, any personalizations done on these subforms would also be reflected in other parts of the application where these form parts are used. For example, changes to the **Addresses** FastTab in the **All customers** page would also result in the same changes appearing in the **Addresses** FastTab in the **All vendors** page.

     With views, the personalization scope of form parts has been modified to match user expectations. In particular, subform personalizations are now tied to the base form where they are made. This means that exporting a view on the **All customers** details page will include personalizations from the base **CustTable** form as well as any personalizations in FactBoxes or form parts modeled in that portion of the form. Similarly, any personalizations done on the **Addresses** FastTab (form part) on the **All customers** page will not be reflected in other forms where that form part is used.
     
These are highly technical modifications to the personalization subsystem that are only available when view is enabled. These modifications are important for ensuring that users have a predictable and understandable experience with views.

## View support
The style of a form determines the level of support for views. 

-    Views include queries for these form types:
     -    List pages (Design.Style = ListPage)
     -    Simple lists (Design.Style = SimpleList)
     -    Grid portions of Master Details and Transaction Details forms (Design.Style=ListPage)
     -    Task single and Task double pages (Design.Style or Design.Pattern is TaskSingle or TaskDouble)
          -  Starting in 10.0.25 / Platform update 49, the "Allow queries to be saved to views on Task Single and Task Double pages" feature adds query support to views defined on these form types.  

-    Views do not include queries for these form types:
     -    Any other full-page form not listed above
     -    Workspaces
          -  Starting in 10.0.25 / Platform update 49, the "Saved views support for workspaces" *preview* feature allows saved views to be defined and shared for both modeled and user-created workspaces.  
     -    Dialogs
          -  Starting in 10.0.25 / Platform update 49, the "Saved views support for dialogs" feature allows saved views to be defined and shared for dialog pages.  
     -    Details portions of Master Details and Transaction Details forms

-    Views are not currently supported on these form types:
     -    Dashboards
     -    Secondary forms like drop-down dialogs, lookups, and enhanced previews

## Modifying forms to fully utilize views
While most forms will work well with saved views, there are some areas that may require changes to form logic so that views work as expected on these forms without causing confusion. Here are some key items to keep in mind during development of new forms.

### Custom filters
Custom filters are controls modeled on forms that cause modifications to the query. Extra work is needed to ensure that view's are marked as having unsaved changes after using a custom filter, and additional work may beneeded to ensure that the value of a custom filter always aligns to the current view or query.  
-  Before version 10.0.25, only adjustments to the query (e.g. filters/sorts) defined through the system-defined filtering mechanisms (Quick Filter, grid column headers, the Filter pane, or Advanced filter or sort) would trigger a view to indicate it had unsaved changes. If a custom filter was used to change the query, the view would not appear to have unsaved changes (until the query was later modified using one of the standard mechanisms). Additionally, if a view was loaded with a query modification related to a custom filter, the custom filter would not reflect that modification, resulting in suboptimal user experience. 
-  Starting with version 10.0.25, form owners can provide better experiences with custom filters by taking advantage of the following two methods, which were introduced specifically for improving custom filter support with saved views.
    -  **public void queryFiltersChanged()**: This new method is called when the query is reexecuted by the system changes the query (e.g. when a view loads or when a system filtering mechanism is used), which gives the custom filter control an opportunity to interrogate the mostly recently executed query to find any relevant filter and update its value to appropriately reflect that query.  
    -  **element.formCustomFilterChanged()**: This is a new API for the custom filter control to call when it has changed the query on the user's behalf. When called, the system will mark the view definition as having unsaved changes. The recommendation is to call this API at the end of the control's modified() method if changes to the control immediately result in the query being refreshed, or call this API for a custom filter on button click if the adjustment of one or more custom filters requires a button for the changes to take effect.  

### Relative filter values
Forms may need to use relative filter conditions to retrieve the appropriate information when the page loads. This often includes filter conditions like restricting data for the current user, current date, current legal entity, etc. If a form hard codes a filter to a particular value, then any view saved with that filter may have issues showing the intended data or in sharing the view with other users. For example, if a form hard codes a "current date" filter to a particular date and that query is saved to a view and the view is shared with another user, it may provide unexpected results since it would still be attempting to retrieve data from the hard-coded date in the past (instead of today). Or if a filter condition was meant to represent the current user but was harded-coded to a particular user, sharing the view with another user could result in an error when trying to load or import the view. 

To avoid this situation, forms with relative filter conditions should have filter values that utilize SysQueryRangeUtil methods in combination with the Finance and Operations [advanced filter syntax](../../fin-ops/get-started/advanced-filtering-query-options.md), specifically the syntax where a filter value is enclosed by parentheses. Doing so will defer evaluation of the filter method until the query is executed, which allows relative filtering conditions to be used in views and passed between users without issue. This same syntax can be used in the user interface by users in conjunction with the "matches" operator for the same effect.  

As an explicit example, consider a form with a filter condition on a "User" field. Setting the filter value to be "currentUserId()" would result in evaluation of the function immediately with the hard-coded user name being in the query. A simple change to set the filter value to be "(currentUserId())" will save the function to the query definition, allowing a view with this condition to be saved to views and passed to other users without issue.  

Below are some common examples: 

| Description | Filter value  |
|--|--|
| Current user | (currentUserId()) |
| Current legal entity | (currentCompany())
| Today | (Day(0))   |
| Yesterday | (Day(-1))  |

For more relative date queries, see [Advanced date queries that use SysQueryRangeUtil methods](../../fin-ops/get-started/advanced-filtering-query-options.md#advanced-date-queries-that-use-sysqueryrangeutil-methods)

### Opting forms out of views
While generally not recommended, starting with version 10.0.25, developers can opt an individual form out of saved views support if needed. This will mean that no view selector is available on the form and there will be no publish capabilities.

To do this, place the following code pre-super() in the init() method of the form: 
     this.disableSavedViewsOnForm();

### Code that can negatively impact views 
X++ code late in the form startup cycle can interfere with views working as users expect. In particular, be aware of the following items: 
-    Modifications of the query after **super()** of **executeQuery()** or after **super()** of **run()** can cause the query aspect of a view to be ignored.  
-    Form changes after **super()** of **run()** can cause some user personalizations to be incorrectly applied to the default view.  

### Secondary list pages
Looking forward, views are meant to replace modeled secondary list pages in the long term.  
-   Typically, secondary list pages, such as **Customers on hold**, are menu items that point to the same form but have a different query. Because menu items that pass in queries override any query that is defined on the default view, these entry points can cause confusion for users as the default view query will not be executed when users navigate to a form using one of these menu items. The current long-term plan is to make secondary list pages obsolete (deprecated) and move them to views.  

-  To avoid user confusion between form caption (such as "All customers") and view name (such as "My customers"), consider renaming form captions to be the name of the corresponding entity. For example, instead of a form caption of "All customers" or "All sales orders", the form caption would be modified to "Customers" and "Sales orders". 

## Known issues
This section provides a list of known issues for saved views while the feature is in a preview state.

### Open issues
-  [Resolved] A view does not get marked as having unsaved changes after using custom filters, which are modeled filter controls above a grid (excluding the QuickFilter). If custom filter conditions have been saved to a view, the custom filter controls may not correctly reflect the current query. See the **Modifying forms to fully utilize views** section for more details of the resolution.  
-  [Resolved] View support for workspaces, dashboards, and dialog boxes. See the **View support** section for more details of the resolution. 
-  [Resolved] [KB 4582751] After adding (reference group) fields via personalization, the fields remain blank.
-  If the Filter pane is open when switching to a different view, the Filter pane will not update to reflect the filters on the target view.
-  Cannot move a view with a QuickFilter condition saved to it to another environment. The fix in release 10.0.13 more gracefully handles the situation, but does not allow these conditions to move between environments.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
