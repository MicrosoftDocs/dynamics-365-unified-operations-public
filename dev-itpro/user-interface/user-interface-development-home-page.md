---
# required metadata

title: User interface development home page | Microsoft Docs
description: This topic contains links to topics about developing user interface elements.
author: RobinARH
manager: AnnBe
ms.date: 2016-09-13 21:26:37
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 61
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 191453
ms.assetid: 757399c5-80d6-48d3-86e1-01ea15252b69
ms.region: Global
# ms.industry: 
ms.author: robinr

---

# User interface development home page

This topic contains links to topics about developing user interface elements.

The user interface for Microsoft Dynamics 365 for Operations differs significantly from the interface for Microsoft Dynamics AX 2012. The client in Dynamics AX 2012 is a Microsoft Win32 application that has extensions that use ActiveX, WinForm, or WPF controls. The X++ application logic runs on the client for the form and table methods, and some logic occurs on the server. For controls, both the X++ logic application programming interface (API) and the physical Win32 control are tightly connected on the client. The client in Dynamics 365 for Operations is an HTML web client that runs in all major browsers. These browsers include Microsoft Edge, Internet Explorer 11, Chrome, and Safari (see [Browser requirements](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/get-started/browser-requirements)). The move to a web client has produced the following changes to client forms and controls:

-   The physical presentation of forms and controls is now HTML, JavaScript, and CSS within the browser.
-   Form controls are split into logical and physical parts. The X++ logical API and related state run on the server.
-   The logical and physical parts are kept in sync through service calls that communicate changes from each side. For example, a user action on the client creates a service call to the server that is either sent immediately or queued so that it can be sent later.
-   The server tier keeps the form state in memory while the form is open.

The form metamodel continues to be used to define controls and application logic. This approach enables Dynamics 365 for Operations to support almost all the existing Form, Form DataSource, and Form Control metamodel and X++ override methods. However, some control types, properties, and override methods have been removed, either because of incompatibility with the new platform or for performance reasons. For example, ActiveX and ManagedHost controls can no longer be used to add custom controls, because they are incompatible with the HTML platform. Instead, a new extensible control framework has been added that lets you add additional controls.

## Tutorials
-   [CLI101: Building the rental charge type form](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/cli101-building-the-rental-charge-type-form)
-   [CLI102: Building the customer form](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/cli102-building-the-customer-form)
-   [BIR102: Add contextual BI to forms](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics-bi-reporting/adding-contextual-bi-to-forms)

## Forms
-   [Navigation concepts](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/navigation-concepts-in-dynamics-ax-7)
-   [The new user experience](https://mix.office.com/watch/1ohsrrpsd02e1)
-   [Layout](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/layout-in-microsoft-dynamics-ax-7)
-   [Symbol font](./media/dynamicssymbolfont20151201.pdf)
-   [Testing forms with custom patterns](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/how-to-testing-forms-with-custom-patterns)

## Controls
-   [Action controls](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/action-controls-in-dynamics-ax)
-   [Sizing for input controls and grid columns](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/sizing-for-input-controls-and-grid-columns)
-   [Check box support in tree controls](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/check-box-support-in-tree-controls)
-   [Filtering](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/filtering-in-dynamics-ax-7)
-   [Window management](https://docs.microsoft.com/en-us/dynamics365/operations/core/get-started/window-management)
-   [Form statistics addin (Office Mix)](https://mix.office.com/watch/1kuwpf3ooohty)
-   [Code migration - context menus](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/migration-upgrade/code-migration-context-menus)
-   [Code migration - mouse double click](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/migration-upgrade/code-migration-mouse-double-click)
-   [Contextual data entry for lookups](http://ax.help.dynamics.com/en/wiki/how-to-contextual-lookups/)
-   [HierarchyViewer control](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/hierarchy-viewer-control)
-   [Lookup controls](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/lookups-controls)
-   [File upload control](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/file-upload-control)
-   [How to: system-defined buttons](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/how-to-system-defined-buttons)
-   [Using images](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/using-images-on-your-form-on-in-a-grid)
-   [Specify the font and background colors for input, table, and grid controls](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/specifying-color-for-font-or-background-of-input-controls-using-the-color-picker-control)
-   [Support for right-to-left languages: A primer on bidirectional text](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/bidirectional-support)
-   [Creating icons for workspace tiles](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/creating-icons-for-workspace-tiles)
-   [Extensible controls – public JavaScript APIs](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/public-javascript-apis)

## Messaging
-   [Slider and MessageBox](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/slider-and-messagebox)
-   [Messaging API: Message center, Message bar, Message details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/new-messaging-api-message-center-message-bar-message-details)
-   [Messaging the user](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/messaging-the-user)

## Form pattern guidelines
-   [Selecting a form pattern](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/how-to-select-a-form-pattern)
-   [Form styles and patterns](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/form-styles-and-patterns)
-   [Apply subpatterns (Office Mix)](https://mix.office.com/watch/fq2k25dzomi3)
-   [Generating the form patterns report (Office Mix)](https://mix.office.com/watch/jqzesi1uuosz)

| Form patterns                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Support form patterns                                                                                                                                                                                                                                                                                                                                                           | Sub patterns                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Details Master](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-master-form-pattern) [Details Transaction](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-transaction-form-pattern) [Form Part Section List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-list-form-pattern) [List Page](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/list-page-form-pattern) [Simple Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-details-form-pattern) [Simple List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-form-pattern) [Simple List and Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-and-details-form-pattern) [Table Of Contents](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/table-of-contents-form-pattern) [Task Single](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/task-single-form-pattern) [Task Double](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/task-double-form-pattern) [Wizard](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/wizard-form-pattern) [Workspace](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/workspace-form-pattern) [General Form Guidelines](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/general-form-guidelines) | [Advanced Selection](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/advanced-selection-form-pattern) [Dialog](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/dialog-form-pattern) [Drop Dialog](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/drop-dialog-form-pattern) [Lookup](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/lookup-form-pattern) [Factbox](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/factbox-form-patterns) | [Custom Filter Group](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/custom-filter-group-subpattern) [Dimension Entry Control](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/financial-dimensions/dimension-entry-control-subpattern) [Dimension Expression Builder](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/financial-dimensions/dimension-expression-builder-subpattern) [Fields and Field Groups](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/fields-and-field-groups-subpattern) [Filters and Toolbar](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/filters-and-toolbar-subpattern) [Fill Text](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/fill-text-subpattern) [Horizontal Fields and Buttons Group](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/horizontal-fields-and-buttons-group-subpattern) [Image Preview](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/image-preview-subpattern) [List Panel](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/list-panel-subpattern) [Nested Simple List and Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/nested-simple-list-and-details-subpattern) [Section Chart](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-chart-form-pattern) [Section Power BI](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-powerbi-subpattern) [Section Related Links](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-related-links-subpattern) [Section Stacked Chart](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-stacked-chart-subpattern) [Section Tabbed List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-tabbed-list-subpattern) [Section Tiles](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-tiles-subpattern) [Tabular Fields](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/tabular-fields-subpattern) [Toolbar and List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/toolbar-and-list-subpattern) [Toolbar and Fields](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/toolbar-and-fields-subpattern) [Workspace Filter Group](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/workspace-filter-group-subpattern) |

## Control extensibility
-   [CLI103: Building an extensible control](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/building-an-extensible-control)
-   [Extensible control programming reference](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/extensible-control-programming-reference)
-   [Control extensibility](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/control-extensibility)
-   [Add localizable labels for an extensible control](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/create-and-use-localizable-labels-in-the-client)
-   [Guidelines for extensible controls layout](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/guidelines-for-extensible-controls-layout)
-   [Control the text that Task Recorder generates for a control](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/control-the-text-that-task-recorder-generates-for-a-control)

## Additional resources
-   Additional help is available as task guides inside Dynamics 365 for Operations. To access task guides, click the Help button on any page.
-   For information about Microsoft Dynamics 365 for Operations training, see [Microsoft eLearning](https://mbspartner.microsoft.com/AX/LearningPlans) (requires a CustomerSource account).


