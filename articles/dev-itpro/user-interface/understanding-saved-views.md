---
# required metadata

title: Understanding saved views
description: This topic explains some more technical aspects of saved views and describes considerations with form development to ensure forms work well with saved views.   
author: jasongre
manager: AnnBe
ms.date: 06/04/2019
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

# Understanding saved views

[!include [banner](../includes/banner.md)]

Saved views are an important expansion of personalization capabilities in Finance and Operations. While the [!Saved views]() article provided general details about this feature, this article will focus on the more technical elements of saved views as well as aspects of form development that may be impacted by views. 

## “User-perceived” forms
Traditionally, a set of personalizations has a 1:1 link to a modeled form. In many forms, this makes sense to user, as the user’s perception of the form matches the way in which the form was modeled. In some cases, however, the 1:1 linkage of a modeled form to a set of personalizations is not intuitive or obvious to users, as users do not see or care about the boundaries between modeled forms. 

Saved views tries to eliminate this confusion by allowing users to create views on “user-perceived” forms, which eliminates the need to understand how forms are modeled to understand how and when personalizations are applied. Consider the following two scenarios:  

-    **More than one “user-perceived” form in a single modeled form**: The standard modeling of Master Details and Transaction Details forms (like the All customers and All purchase orders forms, respectively) consist of more than one “user-perceived” form: a grid “page” and a details “page”. 

     As users are not aware when this transition from list to details crosses a form boundary (nor do they need to know this), view support in Details forms is handled specially to allow views to be defined separately for the grid and details portions, meaning the view selector for the “grid” and “details” can show different sets of available views. Furthermore, the special casing of view support on these forms allows the “grid” views to allow filters in their view definitions, whereas the “details” view only need personalizations. 

-    **More than one modeled form in a single “user-perceived” form**: The ability to embed subforms into modeled forms (via fact boxes or form parts) leads to situations where more than one modeled form corresponds to a single “user-perceived” form. For example, consider the All customers form, which has a number of factboxes and also two fast tabs whose contents come from form parts. With traditional personalization, contrary to a user’s expectations, exporting the personalizations for the CustTable form would not include personalizations on any factbox or any personalizations done inside the Addresses or Contact Information fast tabs. Equally unexpected for users, any personalizations done to these subforms would be reflected in any other part of the application where these form parts were used (e.g. changes to the Address fast tab in the All customers form would also result in the same changes appearing in the Addresses fast tab in the All vendors form).  

     With views, the personalization scope of form parts was modified to match user expectations, specifically subform personalizations are now tied to the base form where they are made. This means that exporting a view on the All customers details page will include personalizations from the base CustTable form as well as any personalizations in fact boxes or form parts modeled in that portion of the form. Similarly, any personalizations done the Addresses fast tab (form part) on the All customers form will not be reflected in other forms where that form part is used.  

These are highly technical modifications to the personalization subsystem that are only available when view are enabled, and they are very important for ensuring users have a predictable and understandable experience with views.  

## View support
The style of a form determines the level of support for views. 
-    Views include queries for forms
     -    List pages
     -    Simple lists
     -    Grid portions of Master Details and Transaction Details forms

-    Views do not include queries
     -    Any other full-page form
     -    Details portions of Master Details and Transaction Details forms

-    Views are not currently supported
     -    Dashboard
     -    Workspaces
     -    Dialogs
     -    Secondary forms like drop dialogs, lookups, and enhanced previews

## Modifying forms to fully utilize views
While most forms will work well with saved views, there are some areas that may require changes to form logic so that views work as expected on these forms without causing confusion.  These items should be kept in mind during development of new forms as well.  

-    X++ code late in the form startup cycle can interfere with views working as users expect. In particular, be mindful of the following: 
     -    Modifications of the query post super() of executeQuery() or post super() of run() can cause the query aspect of a view to be ignored.  
     -    Form changes post super() of run() can result in some user personalizations appearing to not apply correctly.  

-    Extra work may be required to ensure the values of custom filters always align to the current view or query.  
     -    Forms may need to be instrumented to ensure the values of custom filters update based on the current query and aren’t just initialized to the same default value with each form load.  

-    Looking forward, in the long-term, views are meant to replace modeled secondary list pages.  
     -    Typically, secondary list pages (e.g. Customers on hold) are menu items that point at the same form but have a different query. Because menu items that pass in queries will override any query defined on the default view, these entry points can create confusion for users. Long-term, the current plan is to deprecate secondary list pages and move them to views instead.  

     -    To avoid user confusion between form caption (e.g. “All customers”) and view name (e.g. “My customers”), consider renaming form captions to simply be the name of the corresponding entity. For example, instead of a form caption of “All customers” or “All sales orders”, the form caption would be modified to “Customers” and “Sales orders”.  \

## Known issues
-    Publishing views that contain personalizations on subforms (factboxes or form parts) will currently not publish the subform portion of the view. 
-    While re-publishing the current view, an update of the name of the view creates a second view instead of replacing the original one.  
