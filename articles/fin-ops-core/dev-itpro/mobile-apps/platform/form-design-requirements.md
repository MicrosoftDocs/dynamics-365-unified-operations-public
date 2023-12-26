---
title: Form design requirements
description: This article provides form design requirements for mobile apps.
author: jasongre
ms.date: 05/26/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3
ms.collection: get-started
---

# Form design requirements

[!include [banner](../../includes/banner.md)]
[!include [mobile app deprecated](../../includes/mobile-app-deprecation-banner.md)]

This section provides valuable guidelines for building forms that work well with the mobile app.

-   Each form must have an associated Display Menu Item.
    -   The Display Menu Item's **Allow Root Navigation** property must be set to **Yes**. This setting enables the mobile framework to open the form that is referenced by the menu item.
-   Each form must be directly accessible via its Display Menu Item.
    -   To verify accessibility, open the menu item via a URL. Just append **&mi=** to the URL, where the value is the Application Object Tree (AOT) name of your menu item.
    -   If the form doesn't open or show data when you access it in this way, the form won't work with the mobile app.
-   Each form that shows data must have one Master Root Data Source.
    -   This data source must be the first data source on the form (top-most in the designer).
    -   This data source must not be joined to any other data sources.
-   Each form must work with the data source filters.
    -   After you open the form in the web client, open the filter pane by using the **Show filters** button. 
    
        ![Show filters button.](media/filterpane.png) 
        
        Then click **Add a filter field**, and verify that the Master Root Data Source appears as the table for fields in the list of available fields. Other tables can also appear, but the Master Root Data Source **must** appear in this list. Otherwise, the mobile app won't enable searches and navigation that uses context.
    -   Searching: The mobile app does online searches against data by using the Filters framework behind the scenes.
    -   Navigation that uses context: The mobile app enables list-to-details navigation (and other context-aware navigation) by first opening the target form via the menu item and then using the Filters framework to show only the specified record context.
    -   List-to-details navigation: The table that the grid is bound to on form A (the list form) must be the Master Root Data Source on the details form (form B). When a user selects a record in the list on form A, the mobile framework navigates with record context by applying filters on form B that uniquely identify the record.

### Design considerations

#### Using data methods

You can use display methods to show data on pages (both list type pages and detail type pages). However, there are two key points to remember when you use display methods:

-   **Searching** – When a user performs an “online” search (that is, a search that is run against data in the web client instead of locally cached data), the search won't match against display methods, because the Filtering framework in the web client doesn't support searches against data methods. However, when a user does a search against locally cached data, the search will match against display methods, provided that the records have been cached on the device.
-   **Offline** – If a user creates or updates data while their device isn’t connected to the server, temporary records are created in the local cache. Because these temporary records haven't yet been processed in the web client, if the records have any fields that are automatically populated or defaults by server-side business logic, these fields will remain empty until the records have been synced with the web client. Display methods fall into this category of fields that will be empty for a temporary record.

#### Designing for offline

Unlike the web client, which is highly connected to the server and maintains an open user session that has open forms on the server, the mobile app creates user sessions (and opens forms) only in short bursts while the app is being synced with the server (via data read for pages, or via data write/update for actions). If there are no actions to sync with the server, and if the local data cache is up to date, the mobile app won't communicate with the server as a user navigates around the app (unless the user triggers an explicit pull-to-refresh). It's important that you keep this data flow pattern in mind while you design pages and actions in the mobile app. You should not expect form logic to run every time that a page is loaded or an action is started. You should also never expect form logic to run while a user is completing an action. Form logic is run only when the action is being synced with the server. The following list describes the only times when you should expect Form logic to run. **Form logic runs right before a page is opened on the mobile app for the first time.**

1.  When a user first opens a page, the mobile app reaches out to the web client and opens the associated forms. *During this process, logic such as form init and data source init is all run in the usual manner.*
2.  The mobile app framework reads the required data directly from the controls on the forms and sends the data back to the mobile app.
3.  The mobile app caches the data and shows it in the page on the mobile app.
4.  Future attempts to open the page will load the cached data. *These attempts won't run the form logic again, unless the user explicitly refreshes the page or the cache expires. (Currently, the cache set to expire after 30 minutes.)*

**Processing an action that has been submitted to the server from the mobile app**

1.  When a user opens an action and fills in the data in that action, *no form logic is run*. A user can complete an action either offline or online. The system behaves the same way in both cases.
2.  After the user clicks **Done**/**Save** on the action, the mobile app queues a data synchronization operation. This operation will be synced with the server when the mobile app is connected to the Internet.
3.  When an Internet connection is detected (which can happen immediately after the action is completed) the mobile app sends the data synchronization operation to the server for processing.
4.  While the operation is processed on the server, the framework opens the associated forms and enters the data from the action by passing values into the form controls. *During this process, form logic is run in the usual manner (init, modified, clicked, and so on, are all run).* However, the mobile user might have moved to a different part of the app while this processing is occurring. *Any form logic that shows/hides controls will have no effect on the UI that is seen in the mobile app.* Therefore, to minimize synchronization times, it's best not to include any UI logic on the form.

#### Building mobile versions of existing forms

If you decide to modify existing forms so that they work with the mobile framework, instead of building new mobile-specific forms, you might have to conditionally change the form's behavior for mobile-specific scenarios. You can use the following static X++ application programming interfaces (APIs) in your X++ code to determine whether the code is being accessed during a session where a web client user is designing pages/actions or during a session that the mobile framework back end created to load pages/actions for a mobile user. **When a form is being used with the mobile designer**

```xpp
SysTaskRecorderController::isDesigningApp()
```

**When a form is being used by the mobile framework back end to load pages and run actions**

```xpp
SysTaskRecorderController::isExecutingApp()
```

#### Form control support

The form controls for the various base data types (strings, dates, and numbers) and grids are supported. However, a few common controls have limited support. **Reference groups** Fields from within Reference groups controls are compatible when you design pages. However, they aren't compatible when you design Actions. Although you might be able to select these fields without experience any issue, Reference groups have a fundamental incompatibility with the mobile framework. We recommend that you not use Reference groups. Instead, add a control directly to the form, and then bind the control directly to the surrogate foreign key (SFK) by using the property sheet.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
