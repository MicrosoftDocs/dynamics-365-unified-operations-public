---
# required metadata

title: Select a form pattern | Microsoft Docs
description: This article provides information that will help you select the best form pattern for the forms that you migrate. 
author: jasongre
manager: AnnBe
ms.date: 2015-12-23 00:57:30
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
ms.custom: 28681
ms.assetid: eb8f722c-ddd3-414e-b20a-6a20e8f9b24b
ms.region: Global
# ms.industry: 
ms.author: jasongre

---

# Select a form pattern

This article provides information that will help you select the best form pattern for the forms that you migrate. 

Introduction
------------

The selection of a form pattern is an important step in the process of migrating a form. A pattern that is a good fit for the target form reduces the amount of migration work that is required. By contrast, a pattern that isn't a good fit can cause wasted time and effort. Therefore, it's important that you do some investigation, so that you can select the best form pattern for the form that you're migrating. Here is some guidance and tips for determining the appropriate pattern for a form:

-   Investigate the form’s metadata in the form designer. Pay close attention to the following details:
    -   Form name
    -   **Form.Design.Style**
    -   Control names
    -   The way that the controls are organized
    -   The number and names of the data sources
-   Investigate the form’s visuals by running the form and looking at the way information is displayed.

## Selecting a form pattern via metadata
### Use Form.Design.Style for guidance

The **Form.Design.Style** property often contains the name of the pattern that was previously targeted for the form. If the **Style** property correctly matches the metadata, you can use the following table to find a pattern that is likely to be a good fit for the form.

| Form.Design.Style value                                                                          | Corresponding pattern                                                                                           |
|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| DetailsFormMaster                                                                                | [Details Master](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-master-form-pattern)                              |
| DetailsFormTransaction                                                                           | [Details Transaction](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-transaction-form-pattern)                    |
| Dialog                                                                                           | [Dialog](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/dialog-form-pattern)                                              |
| DropDialog                                                                                       | [Drop Dialog](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/drop-dialog-form-pattern)                                    |
| FormPart, where there are just fields                                                            | [Form Part FactBox Card](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/factbox-form-patterns)                            |
| FormPart, where there is a grid                                                                  | [Form Part FactBox Grid](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/factbox-form-patterns)                            |
| ListPage                                                                                         | [List Page](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/list-page-form-pattern)                                        |
| Lookup                                                                                           | [Lookup](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/lookup-form-pattern)                                              |
| SimpleList                                                                                       | [Simple List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-form-pattern)                                    |
| SimpleListDetails, where there are 2–3 fields in the navigation list (recommended)               | [Simple List Details – List Grid](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-and-details-form-pattern)    |
| SimpleListDetails, where there are and 4–5 fields in the navigation list                         | [Simple List Details – Tabular Grid](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-and-details-form-pattern) |
| SimpleListDetails, where there is a tree (rare)                                                  | [Simple List Details – Tree](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-and-details-form-pattern)         |
| TableOfContents                                                                                  | [Table of Contents](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/table-of-contents-form-pattern)                        |
| Auto, where there is an **Overview** tab, a **General **tab, and a single data source            | [Task Single](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/task-single-form-pattern)                                    |
| Auto, where there are two sets of **Overview **tabs, **General** tabs, and/or headers plus lines | [Task Double](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/task-double-form-pattern)                                    |
| Auto, where there is focus on a single record                                                    | [Simple Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-details-form-pattern)                              |
| Auto, where the form name ends in “Lookup”                                                       | [Lookup](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/lookup-form-pattern)                                              |
| Auto, where there is a single tab control and **Next**/**Previous** buttons                      | [Wizard](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/wizard-form-pattern)                                              |
| Auto, where the form name ends in “Wizard”                                                       | [Wizard](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/wizard-form-pattern)                                              |
| Auto, where there is just a grid and some buttons                                                | [Simple List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-form-pattern)                                    |

###  When a form doesn't match the Style property

Sometimes, a form has an incorrect **Form.Design.Style** property value.

| Form.Design.Style value | What the form might actually be                                                                                  |
|-------------------------|------------------------------------------------------------------------------------------------------------------|
| DetailsFormMaster       | DetailsFormTransaction, if there is lines detail, or if controls have names that contain “lines"                 |
| SimpleList              | SimpleListDetails, if there is more than just a grid and some custom filter fields                               |
| SimpleListDetails       | SimpleList, if there is just a grid and some custom filter fields                                                |
| SimpleList              | ListPage, if there are numerous FactBoxes in the **Parts** node, or if the form has a corresponding Details Form |

## Selecting a form pattern via visuals
Although this approach is less useful than looking at the form metadata, you can get a lot of information about a form by running and examining it. Use the form visuals as an additional data point to help you select a form pattern. Look through the screen shots of migrated forms to find a form that looks like the target form. Additionally, make sure that the description or intent of the pattern matches the description/intent of the form.

## Form pattern reference guide
### List of classes of top-level form patterns

| Form pattern                                                                                                        | What it's used for                                                                                                    |
|---------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| [Details Master](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-master-form-pattern) (two variants)                   | A form that displays the details of a complex entity                                                                  |
| [Details Transaction](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-transaction-form-pattern)                        | A form that displays the details of a complex transaction entity and its lines (for example, and order and its lines) |
| [Dialog](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/dialog-form-pattern) (six variants)                                   | A form that is used as a dialog to gather a set of information                                                        |
| [Drop Dialog](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/drop-dialog-form-pattern) (two variants)                         | A form that is used as a drop dialog to gather a small set of information to provide context for an action            |
| [FactBox](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/factbox-form-patterns) (two variants)                                | A Microsoft Dynamics AX 2012 FactBox that displays information about a related record or set of records               |
| [List Page](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/list-page-form-pattern)                                            | A Dynamics AX 2012 List Page                                                                                          |
| [Lookup](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/lookup-form-pattern) (three variants)                                 | A form that is used as a lookup                                                                                       |
| [Simple Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-details-form-pattern) (four variants)                  | A form that is focused on a single record                                                                             |
| [Simple List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-form-pattern)                                        | A form that displays details for a simple entity as a grid that has fewer than 10 fields per record                   |
| [Simple List & Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-and-details-form-pattern) (three variants) | A form that displays information about an entity of medium complexity                                                 |
| [Table of Contents](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/table-of-contents-form-pattern)                            | A form that displays setup information or loosely related information sets                                            |
| Task (two variants)                                                                                                 | A legacy form pattern that is used to display master or transaction entities                                          |
| [Wizard](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/wizard-form-pattern)                                                  | A form that displays a set of tab pages to the user to gather information in a predetermined order                    |
| [Operational Workspace](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/workspace-form-pattern)                                | A form that is used to display an overview of an activity and is meant to be a primary means of navigation            |
| Workspace Panorama Sections (three variants)                                                                        | A form that is used to show content for a panorama section (via a Form Part Control) in the Operational Workspace     |

### Finding forms that currently use a particular form pattern

For a full list of forms that are currently using a particular form pattern, generate the **Form Patterns** report from within Microsoft Visual Studio. On the **Dynamics 365 **menu, expand the **Add-ins** option, and click **Run form patterns report**. A background process generates the report. After several seconds, a message box appears in Visual Studio to indicate that the report has been generated and inform you about the location of the **Form Patterns** report file. You can filter this file by pattern to find forms that use a particular pattern.

### Form pattern visuals and descriptions

For each form pattern class, information is provided about each variant. This information includes a short description and an illustration of an example form.

###### **Details Master**

[**Details Master**](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-master-form-pattern)\[Default\] This form pattern is used to display the details of a complex entity on FastTabs. It includes a grid view and a details view.

Form: CustTable [![image001](./media/image001.jpg)](./media/image001.jpg)[![image002](./media/image002.jpg)](./media/image002.jpg)

**[Details Master w/ Standard Tabs](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-master-form-pattern)** Use this Details Master variant when your form has a large number of FastTabs (&gt;15) that can be grouped into categories.

Form: HcmWorker [![image003](./media/image003.jpg)](./media/image003.jpg)[![HowToSelectAFormPattern (31)](./media/howtoselectaformpattern-31.jpg)](./media/howtoselectaformpattern-31.jpg)

 

###### **Details Transaction**

**[Details Transaction](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-transaction-form-pattern)** Use this form patter to show the details of a complex transaction entity and its lines (for example, an order and its lines).

Form: SalesTable [![HowToSelectAFormPattern (32)](./media/howtoselectaformpattern-32.jpg)](./media/howtoselectaformpattern-32.jpg)[![HowToSelectAFormPattern (33)](./media/howtoselectaformpattern-33.jpg)](./media/howtoselectaformpattern-33.jpg)

 

###### **Dialog**

[**Dialog – Basic**](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/dialog-form-pattern)\[Default\] This form pattern is used to gather or show a set of information.

Form: ProjTableCreate[![HowToSelectAFormPattern (34)](./media/howtoselectaformpattern-34.jpg)](./media/howtoselectaformpattern-34.jpg)

**[Dialog – Read Only](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/dialog-form-pattern)** Use this Dialog variant when your Dialog just displays information that can't be edited. It has only a **Close** button.

Form: SalesTablePostings[![HowToSelectAFormPattern (35)](./media/howtoselectaformpattern-35.jpg)](./media/howtoselectaformpattern-35.jpg)

**[Dialog – FastTabs](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/dialog-form-pattern)** Use this Dialog variant when your Dialog content is grouped into FastTabs.

None currently in product.[![HowToSelectAFormPattern (36)](./media/howtoselectaformpattern-36.jpg)](./media/howtoselectaformpattern-36.jpg)

**[Dialog – Tabs](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/dialog-form-pattern)** Use this Dialog variant when your Dialog content must be grouped into tabs.

Form: CaseDetailCreate[![HowToSelectAFormPattern (37)](./media/howtoselectaformpattern-37.jpg)](./media/howtoselectaformpattern-37.jpg)

**[Dialog – Double Tabs](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/dialog-form-pattern)** Use this Dialog variant when your Dialog content has two tabs that are stacked on top of each other.

Form: PurchTableReferences[![HowToSelectAFormPattern (38)](./media/howtoselectaformpattern-38-300x286.jpg)](./media/howtoselectaformpattern-38.jpg)

 

###### **Drop Dialog**

[**Drop Dialog**](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/drop-dialog-form-pattern)\[Default\] This form pattern is used to initiate actions when the number of fields is small (less than five).

Form: CustCollectionsNewActivityAction[![HowToSelectAFormPattern (39)](./media/howtoselectaformpattern-39.jpg)](./media/howtoselectaformpattern-39.jpg)

**[Drop Dialog – Read Only](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/drop-dialog-form-pattern)** Use this Drop Dialog variant when the fields in the Drop Dialog aren't editable. No **OK**/**Close** button is modeled.

No example currently exists in the product.

 

###### **Factbox**

**[Factbox Grid](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/factbox-form-patterns)** Use this Factbox variant to show a child collection of related information.

Form: ContactsInfoPart[![HowToSelectAFormPattern (40)](./media/howtoselectaformpattern-40.jpg)](./media/howtoselectaformpattern-40.jpg)

**[Factbox Card](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/factbox-form-patterns)** Use this Factbox variant to show a set of related fields.

Form: CustStatisticsStatistics[![HowToSelectAFormPattern (41)](./media/howtoselectaformpattern-41.jpg)](./media/howtoselectaformpattern-41.jpg)

 

###### **List Page**

**[List Page](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/list-page-form-pattern)** The Dynamics AX 2012 list page that is just a grid that is optimized for browsing records and acting on those records.

Form: SalesTableListPage[![HowToSelectAFormPattern (42)](./media/howtoselectaformpattern-42.jpg)](./media/howtoselectaformpattern-42.jpg)

 

###### **Lookup**

[**Lookup Basic**](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/lookup-form-pattern)\[Default\] This form pattern is used if the lookup form is a grid or tree that has optional filters or buttons at the bottom.

Form: SysLanguageLookup[![HowToSelectAFormPattern (43)](./media/howtoselectaformpattern-43.jpg)](./media/howtoselectaformpattern-43.jpg)

**[Lookup w/Preview](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/lookup-form-pattern)** Use this Lookup variant when, in addition to the basic pattern,a preview of the current record is also shown.

Form: HcmWorkerLookup[![HowToSelectAFormPattern (44)](./media/howtoselectaformpattern-44-300x169.jpg)](./media/howtoselectaformpattern-44.jpg)

**[Lookup w/Tabs](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/lookup-form-pattern)** Use this Lookup variant when there are multiple views of a lookup (for example, a grid view/tree view or multiple filtered lists).

Form: CaseCategoryLookup[![HowToSelectAFormPattern (45)](./media/howtoselectaformpattern-45.jpg)](./media/howtoselectaformpattern-45.jpg)

 

###### **Panorama Section**

**[Form Part Section List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-list-form-pattern)** Use this form pattern to show a list in a workspace section. This should be modeled as a separate form and rendered in the workspace via a Form Part Control.

**[Form Part Section List - Double](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-list-form-pattern)** Use this variant when you must also show a secondary list. This secondary list isn't initially visible.

**[Hub Part Chart](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-chart-form-pattern)** Use this variant to show a chart in a workspace section. This should be modeled as a separate form and rendered in the workspace via a Form Part Control.

Form: VendInvoiceJourCountChart[![HowToSelectAFormPattern (1)](./media/howtoselectaformpattern-1.jpg)](./media/howtoselectaformpattern-1.jpg)

 

###### **Simple Details**

**[Simple Details w/Toolbar and Fields](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-details-form-pattern)** Use this form pattern tp show fields for a single base record.

Form: AgreementLine[![HowToSelectAFormPattern (2)](./media/howtoselectaformpattern-2-300x203.jpg)](./media/howtoselectaformpattern-2.jpg)

**[Simple Details w/FastTabs](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-details-form-pattern)** Use this Simple Details variant when the record’s information is organized into FastTabs.

Form: PlanActivityServiceDetails[![HowToSelectAFormPattern (3)](./media/howtoselectaformpattern-3-300x191.jpg)](./media/howtoselectaformpattern-3.jpg)

**[Simple Details w/Standard Tabs](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-details-form-pattern)** Use this Simple Details variant when the record’s information is organized into regular tabs.

Form: HcmEmploymentDateManager[![HowToSelectAFormPattern (4)](./media/howtoselectaformpattern-4-300x191.jpg)](./media/howtoselectaformpattern-4.jpg)

**[Simple Details w/Panorama](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-details-form-pattern)** Use this Simple Details variant to display a record’s information in a horizontally scrolling panorama.

Form: PdsMRCEventTracker[![HowToSelectAFormPattern (5)](./media/howtoselectaformpattern-5-300x191.jpg)](./media/howtoselectaformpattern-5.jpg)

 

###### **Simple List**

**[Simple List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-form-pattern)** This form pattern is used to maintain data for simple entities.

Form: CustGroup[![HowToSelectAFormPattern (6)](./media/howtoselectaformpattern-6.jpg)](./media/howtoselectaformpattern-6.jpg)

 

###### **Simple List and Details**

[**Simple List & Details – List Grid**](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-and-details-form-pattern)\[Default\] This form pattern is used to maintain data for entities of medium complexity. A list grid that has 2–3 fields in the navigation list is the preferred pattern for this form style in the current version.

Form: PaymTerm[![HowToSelectAFormPattern (7)](./media/howtoselectaformpattern-7.jpg)](./media/howtoselectaformpattern-7.jpg)

**[Simple List & Details – Tabular Grid](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-and-details-form-pattern)** Use this Simple List & Details variant if you require more than three fields in the list part of the form.

Form: ExchangeRate[![HowToSelectAFormPattern (8)](./media/howtoselectaformpattern-8.jpg)](./media/howtoselectaformpattern-8.jpg)

**[Simple List & Details – Tree](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-and-details-form-pattern)** Use this Simple List & Details variant if the list part of the form is a tree.

Form: FiscalCalendars[![HowToSelectAFormPattern (9)](./media/howtoselectaformpattern-9.jpg)](./media/howtoselectaformpattern-9.jpg)

 

###### **Table of Contents**

**[Table of Contents](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/table-of-contents-form-pattern)** Use this form pattern to show setup information or loosely related information sets.

Form: CustParameters[![HowToSelectAFormPattern (10)](./media/howtoselectaformpattern-10.jpg)](./media/howtoselectaformpattern-10.jpg)

 

###### **Task**

**[Task Single](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/task-single-form-pattern)** This legacy form pattern is used to display entities. It should be used only for migration, not for new forms.

Form: LedgerJournalTable[![HowToSelectAFormPattern (11)](./media/howtoselectaformpattern-11.jpg)](./media/howtoselectaformpattern-11.jpg)

**[Task Double](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/task-double-form-pattern)** This legacy form pattern is used to display transaction entities. It should be used only for migration, not for new forms.

Form: HRMAbsenceTableHistory[![HowToSelectAFormPattern (12)](./media/howtoselectaformpattern-12.jpg)](./media/howtoselectaformpattern-12.jpg)

 

###### **Wizard**

**[Wizard](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/wizard-form-pattern)** This form pattern is used to display a set of page views to the user to gather information in a predetermined order.

Form: WrkCtrBulkResReqEditWizard[![HowToSelectAFormPattern (13)](./media/howtoselectaformpattern-13.jpg)](./media/howtoselectaformpattern-13.jpg)

 

###### **Workspace**

[**Operational Workspace**](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/workspace-form-pattern)\[Default\] This is the preferred, performance-enhanced variant of the Workspace pattern.

Form: FmClerkWorkspace[![HowToSelectAFormPattern (1)](./media/howtoselectaformpattern-1.png)](./media/howtoselectaformpattern-1.png)

**Workspace** This is the old Workspace pattern. It will be removed soon, so don't use it. It is included here only for completeness.

 Do not use.

## Subpattern reference guide
### List of subpattern classes

| Form pattern                                                                                                     | What it's used for                                                                                  |
|------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| [Custom Filters](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/custom-filter-group-subpattern) (two variants)             | Containers that display QuickFilters and any other modeled custom filters                           |
| Fields (five variants)                                                                                           | Containers that primarily display individual fields                                                 |
| [Dimension Expression Builder](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/financial-dimensions/dimension-expression-builder-subpattern)     | Containers that include a Dimension Expression Builder control                                      |
| [Dimension Entry Control](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/financial-dimensions/dimension-entry-control-subpattern)               | Containers that include a Dimension Entry Control                                                   |
| [List Panel](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/list-panel-subpattern)                                         | Containers that display two lists that users move items between                                     |
| [Nested Simple List and Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/nested-simple-list-and-details-subpattern) | Containers that are used to embed a simpler Simple List and Details form inside a section in a form |
| [Toolbar and Fields](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/toolbar-and-fields-subpattern)                         | Containers that display actions above a set of fields                                               |
| [Toolbar and List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/toolbar-and-list-subpattern) (two variants)              | Containers that display actions above 1–2 grids                                                     |
| Workspace-related (eight variants)                                                                               | Containers that correspond to various sections inside an Operational Workspace                      |

### Finding containers that require that a subpattern be applied on a form

When a form is open in the Visual Studio designer, you can easily search for containers that must still have subpatterns applied by searching for “unspecified” in the control search box at the top of the designer (as shown in the following screen shot).[![HowToSelectAFormPattern (15)](./media/howtoselectaformpattern-15.jpg)](./media/howtoselectaformpattern-15.jpg)

### Subpattern visuals and descriptions

For each subpattern class, information is provided about each variant. This information includes a short description and an illustration of an example form.

###### **Custom Filters**

**[Custom Filters](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/custom-filter-group-subpattern)** Use this form pattern when custom filters are modeled. QuickFilter isn't required.

Form: LedgerJournalTable (TopFields)[![HowToSelectAFormPattern (16)](./media/howtoselectaformpattern-16.jpg)](./media/howtoselectaformpattern-16.jpg)

**[Custom and Quick Filters](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/financial-dimensions/dimension-entry-control-subpattern)** Use this variant when a QuickFilter is required.

Form: CustTable (CustomFilterGroup)[![HowToSelectAFormPattern (17)](./media/howtoselectaformpattern-17-300x132.jpg)](./media/howtoselectaformpattern-17.jpg)

 

###### **Fields**

**[Fields and Field Groups](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/fields-and-field-groups-subpattern)** Use this form pattern to get a responsive layout for containers that contain only fields.

Form: InventLocation (LocationNames)[![HowToSelectAFormPattern (18)](./media/howtoselectaformpattern-18.jpg)](./media/howtoselectaformpattern-18.jpg)

**[Tabular Fields](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/tabular-fields-subpattern)** Use this form pattern to get a structured layout of fields. It is intended primarily for totals.

Form: LedgerJournalTransVendPaym (Balances)[![HowToSelectAFormPattern (19)](./media/howtoselectaformpattern-19.jpg)](./media/howtoselectaformpattern-19.jpg)

**[Fill Text](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/fill-text-subpattern)** Use this form pattern when a single input control requires full width.

Form: FmRental (Notes)[![HowToSelectAFormPattern (20)](./media/howtoselectaformpattern-20.jpg)](./media/howtoselectaformpattern-20.jpg)

**[Horizontal Fields and Button Group](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/horizontal-fields-and-buttons-group-subpattern)** Use this form pattern when a field has an inline action.

Form: SalesTable (GroupHeaderAddressHeaderOverview)[![HowToSelectAFormPattern (21)](./media/howtoselectaformpattern-21.jpg)](./media/howtoselectaformpattern-21.jpg)

**[Image Preview](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/image-preview-subpattern)** Use this form pattern for containers that have image controls (and optional related fields).

Form: RetailVisualProfile (Login)[![HowToSelectAFormPattern (22)](./media/howtoselectaformpattern-22.jpg)](./media/howtoselectaformpattern-22.jpg)

 

###### **Toolbar and List**

**[Toolbar and List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/toolbar-and-list-subpattern)** Use this form pattern on containers that have only actions and a grid.

Form: VendTable (TabCommunication)[![HowToSelectAFormPattern (23)](./media/howtoselectaformpattern-23.jpg)](./media/howtoselectaformpattern-23.jpg)

**[Toolbar and List – Double](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/toolbar-and-list-subpattern)** Use this Toolbar and List variant when the containers have two grids.

Form: SalesQuickQuote (TabPageExistingItems)[![HowToSelectAFormPattern (24)](./media/howtoselectaformpattern-24.jpg)](./media/howtoselectaformpattern-24.jpg)

 

###### **Workspace Related**

**[Section Tiles](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-tiles-subpattern)** Use this variant to show a set of tiles/charts in a workspace section. This should be modeled in a tab page on the workspace form. Charts are defined by using Form Part Controls

Form: SalesOrderProcessingWorkspace[![HowToSelectAFormPattern (25)](./media/howtoselectaformpattern-25.jpg)](./media/howtoselectaformpattern-25.jpg)

**[Section Related Links](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-related-links-subpattern)** Use this variant to show a set of hyperlinks in a workspace section. This should be modeled in a tab page on the workspace form.

Form: SalesOrderProcessingWorkspace[![HowToSelectAFormPattern (26)](./media/howtoselectaformpattern-26.jpg)](./media/howtoselectaformpattern-26.jpg)

**[Section Tabbed List](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-tabbed-list-subpattern)** Use this variant when multiple list variants must be included. Only one is shown at a time.

**[Section Stacked Chart](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-stacked-chart-subpattern)** Use this variant when you must include up to two charts in an Operational Workspace.

**[Section PowerBI](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/section-powerbi-subpattern)** Use this variant when a PowerBI section must be included.

**[Workspace Page Filter Group](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/workspace-filter-group-subpattern)** Use this form pattern to add a single filter to your workspace.

**[Filters and Toolbar – Stacked](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/filters-and-toolbar-subpattern)** Use this subpattern in the Form Part Section List pattern, so that actions appear below filters.

**[Filters and Toolbar – Inline](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/filters-and-toolbar-subpattern)** Use this subpattern in the Form Part Section List pattern, so that filters and actions appear on the same line.

 

###### **Other**

**[Nested Simple List & Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/nested-simple-list-and-details-subpattern)** Use this form pattern to embed a simpler Simple List & Details form inside a tab or group.

Form: HcmJob (TaskTabPage)[![HowToSelectAFormPattern (27)](./media/howtoselectaformpattern-27.jpg)](./media/howtoselectaformpattern-27.jpg)

**[List Panel](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/list-panel-subpattern)** Use this form pattern when users must move items back and forth between two lists.

Form: CLIControls\_ListPanel (FormTabPageControl1)[![HowToSelectAFormPattern (28)](./media/howtoselectaformpattern-28.jpg)](./media/howtoselectaformpattern-28.jpg)

**[Toolbar and Fields](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/toolbar-and-fields-subpattern)** Use this form pattern on containers that have only actions and fields

Form: HcmPosition (WorkerAssignmentTabPage)[![HowToSelectAFormPattern (29)](./media/howtoselectaformpattern-29.jpg)](./media/howtoselectaformpattern-29.jpg)

**[Dimension Entry Control](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/financial-dimensions/dimension-entry-control-subpattern)** Use this form pattern on tab pages that have only a Dimension Entry Control.

Form: CustTable (TabFinancialDimensions)[![HowToSelectAFormPattern (30)](./media/howtoselectaformpattern-30.jpg)](./media/howtoselectaformpattern-30.jpg)

**[Dimension Expression Builder](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/financial-dimensions/dimension-expression-builder-subpattern)** Use this form pattern on containers that include a Dimension Expression Builder control.

