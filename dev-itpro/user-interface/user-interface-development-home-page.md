---
# required metadata

title: User interface development home page
description: This topic contains links to topics about developing user interface elements.
author: RobinARH
manager: AnnBe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 191453
ms.assetid: aea345a3-2302-4b72-9887-f23f72b911f1
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# User interface development home page

[!include[banner](../includes/banner.md)]


This topic contains links to topics about developing user interface elements.

The user interface for Microsoft Dynamics 365 for Operations differs significantly from the interface for Microsoft Dynamics AX 2012. The client in Dynamics AX 2012 is a Microsoft Win32 application that has extensions that use ActiveX, WinForm, or WPF controls. The X++ application logic runs on the client for the form and table methods, and some logic occurs on the server. For controls, both the X++ logic application programming interface (API) and the physical Win32 control are tightly connected on the client. The client in Dynamics 365 for Operations is an HTML web client that runs in all major browsers. These browsers include Microsoft Edge, Internet Explorer 11, Chrome, and Safari (see [System requirements](../get-started/system-requirements.md)). The move to a web client has produced the following changes to client forms and controls:

-   The physical presentation of forms and controls is now HTML, JavaScript, and CSS within the browser.
-   Form controls are split into logical and physical parts. The X++ logical API and related state run on the server.
-   The logical and physical parts are kept in sync through service calls that communicate changes from each side. For example, a user action on the client creates a service call to the server that is either sent immediately or queued so that it can be sent later.
-   The server tier keeps the form state in memory while the form is open.

The form metamodel continues to be used to define controls and application logic. This approach enables Dynamics 365 for Operations to support almost all the existing Form, Form DataSource, and Form Control metamodel and X++ override methods. However, some control types, properties, and override methods have been removed, either because of incompatibility with the new platform or for performance reasons. For example, ActiveX and ManagedHost controls can no longer be used to add custom controls, because they are incompatible with the HTML platform. Instead, a new extensible control framework has been added that lets you add additional controls.

## Tutorials
-   [Building the rental charge type form](build-rental-charge-type-form.md)
-   [Building the customer form](build-customer-form.md)
-   [Add contextual BI to forms](..\analytics\add-contextual-bi-forms.md)

## Forms
-   [Navigation concepts](page-navigation.md)
-   [The new user experience](https://mix.office.com/watch/1ohsrrpsd02e1)
-   [Layout](page-layout.md)
-   [Symbol font](symbol-font.md)
-   [Testing forms with custom patterns](testing-forms-custom-patterns.md)

## Controls
-   [Action controls](action-controls.md)
-   [Sizing for input controls and grid columns](sizing-input-controls-grid-columns.md)
-   [Check box support in tree controls](check-box-tree-controls.md)
-   [Filtering](filtering.md)
-   [Window management](/dynamics365/operations/get-started/window-management)
-   [Form statistics addin (Office Mix)](https://mix.office.com/watch/1kuwpf3ooohty)
-   [Code migration - context menus](..\migration-upgrade\code-migration-context-menus.md)
-   [Code migration - mouse double click](..\migration-upgrade\code-migration-double-click.md)
-   [Contextual data entry for lookups](contextual-data-entry-lookups.md)
-   [HierarchyViewer control](hierarchy-viewer-control.md)
-   [Lookup controls](lookups-controls.md)
-   [File upload control](file-upload-control.md)
-   [How to: system-defined buttons](system-defined-buttons.md)
-   [Using images](images-form-grid.md)
-   [Specify the font and background colors for input, table, and grid controls](specify-color-font-background-controls.md)
-   [Support for right-to-left languages: A primer on bidirectional text](bidirectional-support.md)
-   [Creating icons for workspace tiles](create-icons-workspace-tiles.md)
-   [Keyboard shortcuts for extensible controls](keyboard-shortcuts-controls.md)
-   [Extensible controls – public JavaScript APIs](public-javascript-apis.md)

## Messaging
-   [Slider and MessageBox](slider-messagebox.md)
-   [Messaging API: Message center, Message bar, Message details](messaging-api-center-bar-details.md)
-   [Messaging the user](messaging-user.md)

## Form pattern guidelines
-   [Selecting a form pattern](select-form-pattern.md)
-   [Form styles and patterns](form-styles-patterns.md)
-   [Apply subpatterns (Office Mix)](https://mix.office.com/watch/fq2k25dzomi3)
-   [Generating the form patterns report (Office Mix)](https://mix.office.com/watch/jqzesi1uuosz)

| Form patterns     | Support form patterns       | Sub patterns      |
|---|---|---|
| [Details Master](details-master-form-pattern.md)<br>[Details Transaction](details-transaction-form-pattern.md)<br>[Form Part Section List](section-list-form-pattern.md)<br>[List Page](list-page-form-pattern.md)<br>[Simple Details](simple-details-form-pattern.md)<br>[Simple List](simple-list-form-pattern.md)<br>[Simple List and Details](simple-list-details-form-pattern.md)<br>[Table Of Contents](table-of-contents-form-pattern.md)<br>[Task Single](task-single-form-pattern.md)<br>[Task Double](task-double-form-pattern.md)<br>[Wizard](wizard-form-pattern.md)<br>[Workspace](workspace-form-pattern.md)<br>[General Form Guidelines](general-form-guidelines.md) | [Advanced Selection](advanced-selection-form-pattern.md)<br>[Dialog](dialog-form-pattern.md)<br>[Drop Dialog](drop-dialog-form-pattern.md)<br>[Lookup](lookup-form-pattern.md)<br>[Factbox](factbox-form-patterns.md) | [Custom Filter Group](custom-filter-group-subpattern.md)<br>[Dimension Entry Control](..\financial\dimension-entry-control-subpattern.md)<br>[Dimension Expression Builder](..\financial\dimension-expression-builder-subpattern.md)<br>[Fields and Field Groups](fields-field-groups-subpattern.md)<br>[Filters and Toolbar](filters-toolbar-subpattern.md)<br>[Fill Text](fill-text-subpattern.md)<br>[Horizontal Fields and Buttons Group](horizontal-fields-buttons-group-subpattern.md)<br>[Image Preview](image-preview-subpattern.md)<br>[List Panel](list-panel-subpattern.md)<br>[Nested Simple List and Details](nested-simple-list-details-subpattern.md)<br>[Section Chart](section-chart-form-pattern.md)<br>[Section Power BI](section-powerbi-subpattern.md)<br>[Section Related Links](section-related-links-subpattern.md)<br>[Section Stacked Chart](section-stacked-chart-subpattern.md)<br>[Section Tabbed List](section-tabbed-list-subpattern.md)<br>[Section Tiles](section-tiles-subpattern.md) [Tabular Fields](tabular-fields-subpattern.md)<br>[Toolbar and List](toolbar-list-subpattern.md)<br>[Toolbar and Fields](toolbar-fields-subpattern.md)<br>[Workspace Filter Group](workspace-filter-group-subpattern.md) |

## Control extensibility
-   [Building an extensible control](build-extensible-control.md)
-   [Extensible control programming reference](extensible-control-programming-reference.md)
-   [Control extensibility](control-extensibility.md)
-   [Add localizable labels for an extensible control](create-localizable-labels-client.md)
-   [Guidelines for extensible controls layout](extensible-controls-layout.md)
-   [Control the text that Task Recorder generates for a control](task-recorder-control-text.md)






