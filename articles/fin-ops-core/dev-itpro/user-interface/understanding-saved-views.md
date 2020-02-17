---
# required metadata

title: Build forms that fully utilize saved views
description: This topic explains some of the technical aspects of saved views and describes considerations with form development to ensure forms work well with saved views.  
author: jasongre
manager: AnnBe
ms.date: 10/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SysUserSetup, DefaultDashboard
audience: Developer
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

# Build forms that fully utilize saved views

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Saved views are an important expansion of personalization capabilities Finance and Operations applications. While the [Saved views](../../fin-ops/get-started/saved-views.md) topic provides general details about this feature, this topic focuses on the more technical elements of saved views as well as aspects of form development that may be impacted by views. 

## “User-perceived” pages
Traditionally, a set of personalizations has a 1:1 link to a modeled form. For many pages, this makes sense to the user, as the user’s perception of the page matches the way in which the form is modeled. However, in some cases the 1:1 link of a modeled form to a set of personalizations is not intuitive or obvious because users do not see or care about the boundaries between modeled forms. 

Saved views tries to eliminate this confusion by allowing users to create views on “user-perceived” pages, which eliminates the need to understand how forms are modeled to understand how and when personalizations are applied. Consider the following two scenarios:  

-    **More than one “user-perceived” page in a single modeled form**: The standard modeling of Master Details and Transaction Details forms (like the **CustTable** and **PurchTable** forms, respectively) consist of more than one “user-perceived” page: a grid page and a details page. 

     Because users are not aware when this transition from list to details crosses a form boundary (nor do they need to know this), view support in Details forms is handled differently to allow views to be defined separately for the grid and details portions. This means that the view selector for the “grid” and “details” can show different sets of available views. The special casing of view support on these forms also allows the “grid” views to allow filters in their view definitions, whereas the “details” view only need personalizations.

-    **More than one modeled form in a single “user-perceived” page**: The ability to embed subforms into modeled forms (via FactBoxes or form parts) leads to situations where more than one modeled form corresponds to a single “user-perceived” page. For example, consider the details portion of the **All customers** page, which has a number of FactBoxes and two FastTabs whose contents come from form parts. With traditional personalization, contrary to a user’s expectations, exporting the personalizations for the **CustTable** form would not include personalizations on any FactBox or any personalizations done inside the **Addresses** or **Contact information** FastTabs. Equally unexpected for users, any personalizations done on these subforms would also be reflected in other parts of the application where these form parts are used. For example, changes to the **Addresses** FastTab in the **All customers** page would also result in the same changes appearing in the **Addresses** FastTab in the **All vendors** page.

     With views, the personalization scope of form parts has been modified to match user expectations. In particular, subform personalizations are now tied to the base form where they are made. This means that exporting a view on the **All customers** details page will include personalizations from the base **CustTable** form as well as any personalizations in FactBoxes or form parts modeled in that portion of the form. Similarly, any personalizations done on the **Addresses** FastTab (form part) on the **All customers** page will not be reflected in other forms where that form part is used.
     
These are highly technical modifications to the personalization subsystem that are only available when view is enabled. These modifications are very important for ensuring that users have a predictable and understandable experience with views.

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

-    X++ code late in the form startup cycle can interfere with views working as users expect. In particular, be aware of the following: 
     -    Modifications of the query post super() of executeQuery() or post super() of run() can cause the query aspect of a view to be ignored.  
     -    Form changes post super() of run() can result in some user personalizations not applying correctly.  

-    Extra work may be required to ensure the values of custom filters always align to the current view or query.  
     -    To make sure custom filters work properly with saved views, additional work needs to be done by the platform and there will likely be uptake by forms with custom filters. More information will be provided in the future.  

-    Looking forward, in the long-term, views are meant to replace modeled secondary list pages.  
     -   Typically, secondary list pages, such as Customers on hold, are menu items that point at the same form but have a different query. Because menu items that pass in queries will override any query defined on the default view, these entry points can create confusion for users. Long-term, the current plan is to deprecate secondary list pages and move them to views.

     -  To avoid user confusion between form caption (such as “All customers”) and view name (such as “My customers”), consider renaming form captions to simply be the name of the corresponding entity. For example, instead of a form caption of “All customers” or “All sales orders”, the form caption would be modified to “Customers” and “Sales orders”. 

## Known issues
- Filtering done via custom filters, advanced filters, or sort (on pages where filters are supported on views) will not currently cause the view to appear dirty. However, if you filter via the grid column header or Filter pane, or if you perform an explicit personalization and then save your view, the custom filter, advanced filter, or sort query conditions will be saved to the view.  
