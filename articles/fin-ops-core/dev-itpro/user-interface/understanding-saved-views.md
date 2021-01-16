---
# required metadata

title: Build forms that fully utilize saved views
description: This topic explains some of the technical aspects of saved views and describes considerations with form development to ensure forms work well with saved views.  
author: jasongre
manager: AnnBe
ms.date: 01/04/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SysUserSetup, DefaultDashboard
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
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

### Fixed in release 10.0.16

-  [KB 4590240] Grid resize does not work properly when switching views with the old grid
-  [KB 4600209] Personalizations of form parts are not reflected when switching views
-  [KB 4590224] Focus can start on the wrong control when saved views is enabled
-  [KB 4562254] Table permission error after accessing a shared custom workspace
-  [KB 4600210] Unexpected client error when switching to the Hide tool
-  [KB 4599871] Workspaces do not open if personalization is turned off for user / Unbound controls cannot be set as mandatory via personalization
-  [KB 4594453] Duplicate key exception for forms opening as full-page forms and dialogs

### Fixed in release 10.0.15

-  (Quality update) [KB 4599871] Workspaces do not open if personalization is turned off for user / Unbound controls cannot be set as mandatory via personalization
-  (Quality update) [KB 4600209] Personalizations of form parts are not reflected when switching views
-  [KB 4594452] Duplicate record error when interacting with some subforms (form parts)
-  [KB 4586310] Attachments page loses context after switching views
-  [Bug 494204] Error when deleting/clearing personalizations from User options > Personalization

### Fixed in release 10.0.14

-  (Quality update) [KB 4594452] Duplicate record error when interacting with some subforms (form parts)
-  (Quality update) [KB 4600209] Personalizations of form parts are not reflected when switching views
-  (Quality update) [KB 4584077] Error when exporting multiple views
-  (Quality update) [KB 4584775] Record position lost when switching between list and details
-  [Bug 481290] Error when trying to re-import personalizations to a set of users
-  [KB 4582745] Error triggered when importing user views from one environment to another

### Fixed in release 10.0.13

-  (Quality update) [KB 4594452] Duplicate record error when interacting with some subforms (form parts)
-  (Quality update) [KB 4600209] Personalizations of form parts are not reflected when switching views
-  (Quality update) [KB 4584077] Error when exporting multiple views
-  (Quality update) [KB 4582719 and KB 4578126] When multiple personalization records exist for a form, the wrong one can be selected and loaded
-  [Bug 481283] Error opening a form after moving a view with a QuickFilter condition between environments
-  [Bug 481608] Database sync fails because of a unique index violation on the FormRunConfigurationPublishedView table
-  [Bug 474817] User options > Personalization doesn't list all personalizations for the user 
-  [KB 4574781] Duplicate record exception on saving a view
-  [KB 4575278] Tiles, lists, and links lose their link to the published view if the view is republished
     > [!NOTE]
     > Because additional information is needed to restore the link, re-linking will not occur for any pinned elements from published views prior to 10.0.13. To mitigate, you will need to re-publish your views after updating to 10.0.13 and re-pin the elements to your workspace.
-  [KB 4575285] Publishing to an existing view name overwrites configuration changes already made
-  [KB 4574778] Pin and publish as default do not respect companies that the view was published to
-  [KB 4568154] View import flow doesn't surface if views apply to the grid or details aspect of Details pages
-  [KB 4568152] Users are able to export the Standard view
-  [KB 4568151] Published views recipients are not updated after republishing from a different legal entity
-  [KB 4562137] Views published to a parent security role are not applied to child roles
-  [KB 4564528] QuickFilter default field personalization isn't working as expected with views

### Fixed in release 10.0.12

-  (Quality update) [KB 4582719] When multiple personalization records exist for a form, the wrong one can be selected and loaded
-  [Bug 486275] Strange tooltip behavior for saved views 
-  [KB 4568122] Unexpected queries applied after enabling views
-  [KB 4562152] Migration of personalizations after enabling saved views throws exception in some cases 
-  [KB 4568121] Default view personalizations not applied for users without personalization rights
-  [KB 4568119] Error may occur when importing a workspace or adding a tile or list to a workspace with views enabled
-  [KB 4568118] Error when trying to open the view selector when user has a large number of views
-  [KB 4568148] Old custom user workspaces aren't shown in the Personalization form after enabling views

### Fixed in release 10.0.11

-  (Quality update) [KB 4562147] Importing personalizations to a large number of users is timing out 
-  [KB 4549735] Personalization form missing from security role 
-  [KB 4568116] Views are not marked as having unsaved changes after using Advanced filter or sort
-  [KB 4568117] Crash when attempting to import old personalization formats
-  [KB 4568115] Views can be published with no name
-  [KB 4564908] Unsaved filters and personalizations reflected in some views 

### Fixed in release 10.0.10/Platform update 34
-  (Quality update) [KB 4560406] Importing personalizations to a large number of users is timing out 
-  (Quality update) [KB 4564906] Personalization form doesn't load/Loading a published view for the first time takes a long time
-  [KB 4568114] Views can be published to a blank legal entity
-  [kB 4568113] "View query cannot be applied" message shown when loading a view that modifies existing filters
