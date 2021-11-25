---
title: Form patterns for migrated forms
description: This topic provides information that will help you select the best form pattern for the forms that you migrate. 
author: jasongre
ms.date: 11/09/2017
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Form patterns for migrated forms

[!include [banner](../includes/banner.md)]

This topic provides information that will help you select the best form pattern for the forms that you migrate. 

## Introduction

The selection of a form pattern is an important step in the process of migrating a form. A pattern that is a good fit for the target form reduces the amount of migration work that is required. By contrast, a pattern that isn't a good fit can cause wasted time and effort. Therefore, it's important that you do some investigation, so that you can select the best form pattern for the form that you're migrating. Here is some guidance and tips for determining the appropriate pattern for a form:

-   Investigate the form’s metadata in the form designer. Pay close attention to the following details:
    -   Form name
    -   Form.Design.Style
    -   Control names
    -   The way that the controls are organized
    -   The number and names of the data sources
-   Investigate the form’s visuals by running the form and looking at the way information is displayed.

## Selecting a form pattern via metadata
### Use Form.Design.Style for guidance

The **Form.Design.Style** property often contains the name of the pattern that was previously targeted for the form. If the **Style** property correctly matches the metadata, you can use the following table to find a pattern that is likely to be a good fit for the form.

| Form.Design.Style value                                                                          | Corresponding pattern                                                                                           |
|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| DetailsFormMaster                                                                                | [Details Master](details-master-form-pattern.md)                              |
| DetailsFormTransaction                                                                           | [Details Transaction](details-transaction-form-pattern.md)                    |
| Dialog                                                                                           | [Dialog](dialog-form-pattern.md)                                              |
| DropDialog                                                                                       | [Drop Dialog](drop-dialog-form-pattern.md)                                    |
| FormPart, where there are just fields                                                            | [Form Part FactBox Card](factbox-form-patterns.md)                            |
| FormPart, where there is a grid                                                                  | [Form Part FactBox Grid](factbox-form-patterns.md)                            |
| ListPage                                                                                         | [List Page](list-page-form-pattern.md)                                        |
| Lookup                                                                                           | [Lookup](lookup-form-pattern.md)                                              |
| SimpleList                                                                                       | [Simple List](simple-list-form-pattern.md)                                    |
| SimpleListDetails, where there are 2–3 fields in the navigation list (recommended)               | [Simple List Details – List Grid](simple-list-details-form-pattern.md)    |
| SimpleListDetails, where there are and 4–5 fields in the navigation list                         | [Simple List Details – Tabular Grid](simple-list-details-form-pattern.md) |
| SimpleListDetails, where there is a tree (rare)                                                  | [Simple List Details – Tree](simple-list-details-form-pattern.md)         |
| TableOfContents                                                                                  | [Table of Contents](table-of-contents-form-pattern.md)                        |
| Auto, where there is an **Overview** tab, a **General** tab, and a single data source            | [Task Single](task-single-form-pattern.md)                                    |
| Auto, where there are two sets of **Overview** tabs, **General** tabs, and/or headers plus lines | [Task Double](task-double-form-pattern.md)                                    |
| Auto, where there is focus on a single record                                                    | [Simple Details](simple-details-form-pattern.md)                              |
| Auto, where the form name ends in “Lookup”                                                       | [Lookup](lookup-form-pattern.md)                                              |
| Auto, where there is a single tab control and **Next**/**Previous** buttons                      | [Wizard](wizard-form-pattern.md)                                              |
| Auto, where the form name ends in “Wizard”                                                       | [Wizard](wizard-form-pattern.md)                                              |
| Auto, where there is just a grid and some buttons                                                | [Simple List](simple-list-form-pattern.md)                                    |

###  When a form doesn't match the Style property

Sometimes, a form has an incorrect **Form.Design.Style** property value.

| Form.Design.Style value | What the form might actually be                                                                                  |
|-------------------------|------------------------------------------------------------------------------------------------------------------|
| DetailsFormMaster       | DetailsFormTransaction, if there is lines detail, or if controls have names that contain “lines"                 |
| SimpleList              | SimpleListDetails, if there is more than just a grid and some custom filter fields                               |
| SimpleListDetails       | SimpleList, if there is just a grid and some custom filter fields                                                |
| SimpleList              | ListPage, if there are numerous FactBoxes in the **Parts** node, or if the form has a corresponding Details Form |

## Selecting a form pattern via visuals
Although this approach is less useful than looking at the form metadata, you can get a lot of information about a form by running and examining it. Use the form visuals as an additional data point to help you select a form pattern. Look through the screen shots of migrated forms to find a form that looks like the target form. Additionally, make sure that the description or intent of the pattern matches the description/intent of the form.

## Selecting a form pattern via the designer

Right-click the **Design** node of the target form, select **Apply pattern**, and then click the pattern to apply.

## Form pattern reference guide
### List of classes of top-level form patterns

| Form pattern                                                                                                        | What it's used for                                                                                                    |
|---------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| [Details Master](details-master-form-pattern.md) (two variants)                   | A form that displays the details of a complex entity                                                                  |
| [Details Transaction](details-transaction-form-pattern.md)                        | A form that displays the details of a complex transaction entity and its lines (for example, and order and its lines) |
| [Dialog](dialog-form-pattern.md) (six variants)                                   | A form that is used as a dialog to gather a set of information                                                        |
| [Drop Dialog](drop-dialog-form-pattern.md) (two variants)                         | A form that is used as a drop dialog to gather a small set of information to provide context for an action            |
| [FactBox](factbox-form-patterns.md) (two variants)                                | A Microsoft Dynamics AX 2012 FactBox that displays information about a related record or set of records               |
| [List Page](list-page-form-pattern.md)                                            | A Dynamics AX 2012 List Page                                                                                          |
| [Lookup](lookup-form-pattern.md) (three variants)                                 | A form that is used as a lookup                                                                                       |
| [Simple Details](simple-details-form-pattern.md) (four variants)                  | A form that is focused on a single record                                                                             |
| [Simple List](simple-list-form-pattern.md)                                        | A form that displays details for a simple entity as a grid that has fewer than 10 fields per record                   |
| [Simple List & Details](simple-list-details-form-pattern.md) (three variants) | A form that displays information about an entity of medium complexity                                                 |
| [Table of Contents](table-of-contents-form-pattern.md)                            | A form that displays setup information or loosely related information sets                                            |
| Task (two variants)                                                                                                 | A legacy form pattern that is used to display master or transaction entities                                          |
| [Wizard](wizard-form-pattern.md)                                                  | A form that displays a set of tab pages to the user to gather information in a predetermined order                    |
| [Operational Workspace](workspace-form-pattern.md)                                | A form that is used to display an overview of an activity and is meant to be a primary means of navigation            |
| Workspace Panorama Sections (three variants)                                                                        | A form that is used to show content for a panorama section (via a Form Part Control) in the Operational Workspace     |

### Finding forms that currently use a particular form pattern

For a full list of forms that are currently using a particular form pattern, generate the **Form Patterns** report from within Microsoft Visual Studio. For information on running the report, see [Form pattern add-ins](form-pattern-add-ins.md). You can filter the report in Excel to find forms that use a particular pattern.

### Form pattern visuals and descriptions

For each form pattern class, information is provided about each variant. This information includes a short description and an illustration of an example form.

#### Details Master

[Details Master](details-master-form-pattern.md)\[Default\] This form pattern is used to display the details of a complex entity on FastTabs. It includes a grid view and a details view.

Form: CustTable 

![Details view of CustTable.](./media/image001.jpg)

![Grid view of CustTable.](./media/image002.jpg)

[Details Master w/ Standard Tabs](details-master-form-pattern.md) Use this Details Master variant when your form has a large number of FastTabs (>15) that can be grouped into categories.

Form: HcmWorker 

[![Details view of HcmWorker.](./media/image003.jpg)](./media/image003.jpg)

[![Table view of HcmWorker.](./media/howtoselectaformpattern-31.jpg)](./media/howtoselectaformpattern-31.jpg)



#### Details Transaction

[Details Transaction](details-transaction-form-pattern.md) Use this form patter to show the details of a complex transaction entity and its lines (for example, an order and its lines).

Form: SalesTable 

[![Details view of Details Transaction.](./media/howtoselectaformpattern-32.jpg)](./media/howtoselectaformpattern-32.jpg)

[![Grid view of Details Transaction.](./media/howtoselectaformpattern-33.jpg)](./media/howtoselectaformpattern-33.jpg)



#### Dialog

[Dialog – Basic](dialog-form-pattern.md)\[Default\] This form pattern is used to gather or show a set of information.

Form: ProjTableCreate

[![Dialog - Basic form.](./media/howtoselectaformpattern-34.jpg)](./media/howtoselectaformpattern-34.jpg)

[Dialog – Read Only](dialog-form-pattern.md) Use this Dialog variant when your Dialog just displays information that can't be edited. It has only a **Close** button.

Form: SalesTablePostings

[![Dialog - Read Only form.](./media/howtoselectaformpattern-35.jpg)](./media/howtoselectaformpattern-35.jpg)

[Dialog – FastTabs](dialog-form-pattern.md) Use this Dialog variant when your Dialog content is grouped into FastTabs.

None currently in product.

[![Dialog - FastTabs form.](./media/howtoselectaformpattern-36.jpg)](./media/howtoselectaformpattern-36.jpg)

[Dialog – Tabs](dialog-form-pattern.md) Use this Dialog variant when your Dialog content must be grouped into tabs.

Form: CaseDetailCreate

![Dialog - Tabs form.](./media/howtoselectaformpattern-37.jpg)

[Dialog – Double Tabs](dialog-form-pattern.md) Use this Dialog variant when your Dialog content has two tabs that are stacked on top of each other.

Form: PurchTableReferences

![Dialog - Double Tabs form.](./media/howtoselectaformpattern-38.jpg)



#### Drop Dialog

[Drop Dialog](drop-dialog-form-pattern.md)\[Default\] This form pattern is used to initiate actions when the number of fields is small (less than five).

Form: CustCollectionsNewActivityAction

[![Drop Dialog form.](./media/howtoselectaformpattern-39.jpg)](./media/howtoselectaformpattern-39.jpg)

[Drop Dialog – Read Only](drop-dialog-form-pattern.md) Use this Drop Dialog variant when the fields in the Drop Dialog aren't editable. No **OK**/**Close** button is modeled.

No example currently exists in the product.

#### FactBox

[FactBox Grid](factbox-form-patterns.md) Use this FactBox variant to show a child collection of related information.

Form: ContactsInfoPart

![FactBox form.](./media/howtoselectaformpattern-40.jpg)

[FactBox Card](factbox-form-patterns.md) Use this FactBox variant to show a set of related fields.

Form: CustStatisticsStatistics

![FactBox Card.](./media/howtoselectaformpattern-41.jpg)

#### List Page

[List Page](list-page-form-pattern.md) The Dynamics AX 2012 list page that is just a grid that is optimized for browsing records and acting on those records.

Form: SalesTableListPage

![List Page form.](./media/howtoselectaformpattern-42.jpg)

#### Lookup

[Lookup Basic](lookup-form-pattern.md)\[Default\] This form pattern is used if the lookup form is a grid or tree that has optional filters or buttons at the bottom.

Form: SysLanguageLookup

[![Lookup Basic form.](./media/howtoselectaformpattern-43.jpg)](./media/howtoselectaformpattern-43.jpg)

[Lookup w/Preview](lookup-form-pattern.md) Use this Lookup variant when, in addition to the basic pattern, a preview of the current record is also shown.

Form: HcmWorkerLookup

![Lookup with Preview form.](./media/howtoselectaformpattern-44.jpg)

[Lookup w/Tabs](lookup-form-pattern.md) Use this Lookup variant when there are multiple views of a lookup (for example, a grid view/tree view or multiple filtered lists).

Form: CaseCategoryLookup

![Lookup with Tabs form.](./media/howtoselectaformpattern-45.jpg)



#### Panorama Section

[Form Part Section List](section-list-form-pattern.md) Use this form pattern to show a list in a workspace section. This should be modeled as a separate form and rendered in the workspace via a Form Part Control.

[Form Part Section List - Double](section-list-form-pattern.md) Use this variant when you must also show a secondary list. This secondary list isn't initially visible.

[Hub Part Chart](section-chart-form-pattern.md) Use this variant to show a chart in a workspace section. This should be modeled as a separate form and rendered in the workspace via a Form Part Control.

Form: VendInvoiceJourCountChart

[![Example.](./media/howtoselectaformpattern-1.jpg)](./media/howtoselectaformpattern-1.jpg)



#### Simple Details

[Simple Details w/Toolbar and Fields](simple-details-form-pattern.md) Use this form pattern to show fields for a single base record.

Form: AgreementLine

![Simple Details with Toolbar and Fields form.](./media/howtoselectaformpattern-2.jpg)

[Simple Details w/FastTabs](simple-details-form-pattern.md) Use this Simple Details variant when the record’s information is organized into FastTabs.

Form: PlanActivityServiceDetails

![Simple Details with FastTabs form.](./media/howtoselectaformpattern-3.jpg)

[Simple Details w/Standard Tabs](simple-details-form-pattern.md) Use this Simple Details variant when the record’s information is organized into regular tabs.

Form: HcmEmploymentDateManager

![Simple Details with Standard Tabs form.](./media/howtoselectaformpattern-4.jpg)

[Simple Details w/Panorama](simple-details-form-pattern.md) Use this Simple Details variant to display a record’s information in a horizontally scrolling panorama.

Form: PdsMRCEventTracker

![Simple Details with Panorama form.](./media/howtoselectaformpattern-5.jpg)


#### Simple List

[Simple List](simple-list-form-pattern.md) This form pattern is used to maintain data for simple entities.

Form: CustGroup

![Simple List form.](./media/howtoselectaformpattern-6.jpg)



#### Simple List and Details

[Simple List & Details – List Grid](simple-list-details-form-pattern.md)\[Default\] This form pattern is used to maintain data for entities of medium complexity. A list grid that has 2–3 fields in the navigation list is the preferred pattern for this form style in the current version.

Form: PaymTerm

![HowToSelectAFormPattern (7).](./media/howtoselectaformpattern-7.jpg)

[Simple List & Details – Tabular Grid](simple-list-details-form-pattern.md) Use this Simple List & Details variant if you require more than three fields in the list part of the form.

Form: ExchangeRate

![Simple List and Details - Tabular Grid form.](./media/howtoselectaformpattern-8.jpg)

[Simple List & Details – Tree](simple-list-details-form-pattern.md) Use this Simple List & Details variant if the list part of the form is a tree.

Form: FiscalCalendars

![Simple List and Details - Tree form.](./media/howtoselectaformpattern-9.jpg)



#### Table of Contents

[Table of Contents](table-of-contents-form-pattern.md) Use this form pattern to show setup information or loosely related information sets.

Form: CustParameters

![Table of Contents form.](./media/howtoselectaformpattern-10.jpg)



#### Task

[Task Single](task-single-form-pattern.md) This legacy form pattern is used to display entities. It should be used only for migration, not for new forms.

Form: LedgerJournalTable

![Task Single form.](./media/howtoselectaformpattern-11.jpg)

[Task Double](task-double-form-pattern.md) This legacy form pattern is used to display transaction entities. It should be used only for migration, not for new forms.

Form: HRMAbsenceTableHistory

![Task Double form.](./media/howtoselectaformpattern-12.jpg)



#### Wizard

[Wizard](wizard-form-pattern.md) This form pattern is used to display a set of page views to the user to gather information in a predetermined order.

Form: WrkCtrBulkResReqEditWizard

![Wizard form.](./media/howtoselectaformpattern-13.jpg)



#### Workspace

[Operational Workspace](workspace-form-pattern.md)\[Default\] This is the preferred, performance-enhanced variant of the Workspace pattern.

Form: FmClerkWorkspace

![Operational Workspace form.](./media/howtoselectaformpattern-1.png)

Workspace: This is the old Workspace pattern. It will be removed soon, so don't use it. It is included here only for completeness.

Do not use.

## Subpattern reference guide
### List of subpattern classes

| Form pattern                                                                                                     | What it's used for                                                                                  |
|------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| [Custom Filters](custom-filter-group-subpattern.md) (two variants)             | Containers that display QuickFilters and any other modeled custom filters                           |
| Fields (five variants)                                                                                           | Containers that primarily display individual fields                                                 |
| [Dimension Expression Builder](../financial/dimension-expression-builder-subpattern.md)     | Containers that include a Dimension Expression Builder control                                      |
| [Dimension Entry Control](../financial/dimension-entry-control-subpattern.md)               | Containers that include a Dimension Entry Control                                                   |
| [List Panel](list-panel-subpattern.md)                                         | Containers that display two lists that users move items between                                     |
| [Nested Simple List and Details](nested-simple-list-details-subpattern.md) | Containers that are used to embed a simpler Simple List and Details form inside a section in a form |
| [Toolbar and Fields](toolbar-fields-subpattern.md)                         | Containers that display actions above a set of fields                                               |
| [Toolbar and List](toolbar-list-subpattern.md) (two variants)              | Containers that display actions above 1–2 grids                                                     |
| Workspace-related (eight variants)                                                                               | Containers that correspond to various sections inside an Operational Workspace                      |

### Finding containers that require that a subpattern be applied on a form

When a form is open in the Visual Studio designer, you can easily search for containers that must still have subpatterns applied by searching for “unspecified” in the control search box at the top of the designer (as shown in the following screen shot).

[![Search for containers.](./media/howtoselectaformpattern-15.jpg)](./media/howtoselectaformpattern-15.jpg)

### Subpattern visuals and descriptions

For each subpattern class, information is provided about each variant. This information includes a short description and an illustration of an example form.

#### Custom Filters

[Custom Filters](custom-filter-group-subpattern.md) Use this form pattern when custom filters are modeled. QuickFilter isn't required.

Form: LedgerJournalTable (TopFields)

![Custom Filters form.](./media/howtoselectaformpattern-16.jpg)

[Custom and Quick Filters](../financial/dimension-entry-control-subpattern.md) Use this variant when a QuickFilter is required.

Form: CustTable (CustomFilterGroup)

![Custom and Quick Filters form.](./media/howtoselectaformpattern-17.jpg)



#### Fields

[Fields and Field Groups](fields-field-groups-subpattern.md) Use this form pattern to get a responsive layout for containers that contain only fields.

Form: InventLocation (LocationNames)

![Fields and Field Groups form.](./media/howtoselectaformpattern-18.jpg)

[Tabular Fields](tabular-fields-subpattern.md) Use this form pattern to get a structured layout of fields. It is intended primarily for totals.

Form: LedgerJournalTransVendPaym (Balances)

![Tabular Fields form.](./media/howtoselectaformpattern-19.jpg)

[Fill Text](fill-text-subpattern.md) Use this form pattern when a single input control requires full width.

Form: FmRental (Notes)

![Fill Text form.](./media/howtoselectaformpattern-20.jpg)

[Horizontal Fields and Button Group](horizontal-fields-buttons-group-subpattern.md) Use this form pattern when a field has an inline action.

Form: SalesTable (GroupHeaderAddressHeaderOverview)

![Horizontal Fields and Button Group form.](./media/howtoselectaformpattern-21.jpg)

[Image Preview](image-preview-subpattern.md) Use this form pattern for containers that have image controls (and optional related fields).

Form: RetailVisualProfile (Login)

![Image Preview form.](./media/howtoselectaformpattern-22.jpg)



#### Toolbar and List

[Toolbar and List](toolbar-list-subpattern.md) Use this form pattern on containers that have only actions and a grid.

Form: VendTable (TabCommunication)

![Toolbar and List form.](./media/howtoselectaformpattern-23.jpg)

[Toolbar and List – Double](toolbar-list-subpattern.md) Use this Toolbar and List variant when the containers have two grids.

Form: SalesQuickQuote (TabPageExistingItems)

![Toolbar and List - Double form.](./media/howtoselectaformpattern-24.jpg)



#### Workspace Related

[Section Tiles](section-tiles-subpattern.md) Use this variant to show a set of tiles/charts in a workspace section. This should be modeled in a tab page on the workspace form. Charts are defined by using Form Part Controls

Form: SalesOrderProcessingWorkspace

![Section Tiles form.](./media/howtoselectaformpattern-25.jpg)

[Section Related Links](section-related-links-subpattern.md) Use this variant to show a set of hyperlinks in a workspace section. This should be modeled in a tab page on the workspace form.

Form: SalesOrderProcessingWorkspace

![Section Related Links form.](./media/howtoselectaformpattern-26.jpg)

[Section Tabbed List](section-tabbed-list-subpattern.md) Use this variant when multiple list variants must be included. Only one is shown at a time.

[Section Stacked Chart](section-stacked-chart-subpattern.md) Use this variant when you must include up to two charts in an Operational Workspace.

[Section PowerBI](section-powerbi-subpattern.md) Use this variant when a Power BI section must be included.

[Workspace Page Filter Group](workspace-filter-group-subpattern.md) Use this form pattern to add a single filter to your workspace.

[Filters and Toolbar – Stacked](filters-toolbar-subpattern.md) Use this subpattern in the Form Part Section List pattern, so that actions appear below filters.

[Filters and Toolbar – Inline](filters-toolbar-subpattern.md) Use this subpattern in the Form Part Section List pattern, so that filters and actions appear on the same line.



#### Other

[Nested Simple List & Details](nested-simple-list-details-subpattern.md) Use this form pattern to embed a simpler Simple List & Details form inside a tab or group.

Form: HcmJob (TaskTabPage)

![Nested Simple List and Details form.](./media/howtoselectaformpattern-27.jpg)

[List Panel](list-panel-subpattern.md) Use this form pattern when users must move items back and forth between two lists.

Form: CLIControls\_ListPanel (FormTabPageControl1)

![List Panel form.](./media/howtoselectaformpattern-28.jpg)

[Toolbar and Fields](toolbar-fields-subpattern.md) Use this form pattern on containers that have only actions and fields

Form: HcmPosition (WorkerAssignmentTabPage)

![Toolbar and Fields form.](./media/howtoselectaformpattern-29.jpg)

[Dimension Entry Control](../financial/dimension-entry-control-subpattern.md) Use this form pattern on tab pages that have only a Dimension Entry Control.

Form: CustTable (TabFinancialDimensions)

![Dimension Entry Control form.](./media/howtoselectaformpattern-30.jpg)

[Dimension Expression Builder](../financial/dimension-expression-builder-subpattern.md) Use this form pattern on containers that include a Dimension Expression Builder control.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]