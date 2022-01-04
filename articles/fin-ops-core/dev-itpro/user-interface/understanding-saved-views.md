---
# required metadata

title: Build forms that fully utilize saved views
description: This topic explains some of the technical aspects of saved views and describes considerations with form development to ensure forms work well with saved views.
author: jasongre
ms.date: 01/04/2021
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

-    Views include queries for forms, such as:
     -    List pages
     -    Simple lists
     -    Grid portions of Master Details and Transaction Details forms

-    Views do not include queries, such as:
     -    Any other full-page form
     -    Details portions of Master Details and Transaction Details forms

-    Views that are not currently supported include:
     -    Dashboards
     -    Workspaces
     -    Dialogs
     -    Secondary forms like drop-down dialogs, lookups, and enhanced previews

## Modifying forms to fully utilize views
While most forms will work well with saved views, there are some areas that may require changes to form logic so that views work as expected on these forms without causing confusion. Here are some key items to keep in mind during development of new forms.

-    X++ code late in the form startup cycle can interfere with views working as users expect. In particular, be aware of the following items: 
     -    Modifications of the query after **super()** of **executeQuery()** or after **super()** of **run()** can cause the query aspect of a view to be ignored.  
     -    Form changes after **super()** of **run()** can cause some user personalizations to be incorrectly applied to the default view.  

-    Extra work may be required to ensure the values of custom filters always align to the current view or query.  
     -    To make sure that custom filters work correctly with saved views, the platform still has additional work to better support these controls. Once that support is available, uptake will be required by any form that has custom filters. More information will be provided when the recommended approach has been finalized. 

-    Looking forward, in the long-term, views are meant to replace modeled secondary list pages.  
     -   Typically, secondary list pages, such as **Customers on hold**, are menu items that point to the same form but have a different query. Because menu items that pass in queries override any query that is defined on the default view, these entry points can cause confusion for users. The current long-term plan is to make secondary list pages obsolete (deprecated) and move them to views. However, that effort hasn't yet been started. 

     -  To avoid user confusion between form caption (such as "All customers") and view name (such as "My customers"), consider renaming form captions to be the name of the corresponding entity. For example, instead of a form caption of "All customers" or "All sales orders", the form caption would be modified to "Customers" and "Sales orders". 

## Known issues
This section provides a list of known issues for saved views while the feature is in a preview state.

### Open issues
-  A view does not get marked as having unsaved changes after using custom filters, which are the filters above a grid excluding the QuickFilter. If custom filter conditions have been saved to a view, the custom filter controls may not correctly reflect the current query.  
-  View support for workspaces, dashboards, and dialog boxes.
-  [KB 4553227] After adding (reference group) fields via personalization, the fields remain blank.
-  If the Filter pane is open when switching to a different view, the Filter pane will not update to reflect the filters on the target view.
-  Cannot move a view with a QuickFilter condition saved to it to another environment. The fix in release 10.0.13 more gracefully handles the situation, but does not allow these conditions to move between environments.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
