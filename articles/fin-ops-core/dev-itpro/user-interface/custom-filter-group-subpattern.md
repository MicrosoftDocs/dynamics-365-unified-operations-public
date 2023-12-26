---
title: Custom Filter Group subpattern
description: This article provides information about the Custom Filter Group subpattern.
author: jasongre
ms.date: 04/22/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 1838c10d-9172-4853-aa49-17710adf8bc1
---

# Custom Filter Group subpattern

[!include [banner](../includes/banner.md)]

## Usage

This subpattern is used to show a small collection of input controls (no more than five) that apply a custom filter to a grid or form section. Fields in the Custom Filter Group should be limited to the following field types, which have constrained inputs and can be applied to the query:

-   StringEdits with Lookups
-   Date fields
-   ReferenceGroup
-   Comboboxes
-   Checkboxes
-   Quick Filter

Two patterns are described in this document. The only difference between these patterns is whether the Quick Filter control is mandatory or optional:

-   **Custom Filters** – In this subpattern, the QuickFilter control is optional.
-   **Custom and Quick Filters** – In this subpattern, the QuickFilter control is mandatory.

## Wireframes
### Custom Filters

[![Custom filters group 1.](./media/customfiltergroup1.png)](./media/customfiltergroup1.png)

### Custom and Quick Filters

![Custom and quick filters group 2.](./media/customfiltergroup2.png)

## Model
### Custom Filters – High-level structure

- CustomFilter (Group)

    - *QuickFilter (QuickFilter) \[Optional\]*
    - *FieldGroups (Group) \[0..N\]*

        - Fields ($Field) \[1..N\]

    - *Fields ($Fields) \[0..N\]*

### Custom and Quick Filters – High-level structure

- CustomFilter (Group)

    - QuickFilter (QuickFilter)
    - *FieldGroups (Group) \[0..N\]*

        - Fields ($Field) \[1..N\]

    - *Fields ($Fields) \[0..N\]*

### Core components

-   Apply a custom filter-container pattern to a Group control.
-   Address BP Warnings:
    -   Input controls within the CustomFilterGroup should not have a DataSource or DataField assigned.

### Related container patterns

None

### Related modeling

Use QueryFilter, not QueryBuildRange, for all custom filters. QueryBuildRange doesn't work correctly with outer-joined fields.

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in a browser, and walk through these steps.

-   **Standard form guidelines:**
    -   [General form guidelines](general-form-guidelines.md)
-   **Custom Filter Group guidelines:**
    -   All controls (except QuickFilter) are constrained input controls. Open-ended controls, such as strings, integers, and reals, should not be used.
    -   Field labels are turned off to save space. For example, no label is needed for a combobox that has the values **Open**, **Closed**, **Posted**, and All.
        -   Show labels when the filter values do not provide sufficient context for the user to understand what the filter does. For example, a date field provides no context, and the user requires a label to understand what type of date is specified (for example, **Created date**).
        -   Either all labels are turned off, or all labels are turned on. Don't mix unlabeled filters and labeled filters.
        -   **Exception:** When you use a check box–style Boolean, the label can be left on, even though other fields don't show a label.
    -   There should not be more than five controls in the custom filter group.

## Examples
### Custom Filters

Form: **LedgerJournalTable (TopFields)** 

![Custom filters group 3.](./media/customfiltergroup3.png)

### Custom and Quick Filters

Form: **CustTable** **(CustomFilterGroup)** 

[![Custom and quick filters group 4.](./media/customfiltergroup4.png)](./media/customfiltergroup4.png)

## Resources
### Typically used by form patterns

-   Simple List
-   Details Master
-   Details Transaction
-   List Page

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

-   **What do I do with the legal entity?**
    -   “Legal entity” is a typical custom filter that belongs in the Custom Filter Group.
-   **Should the custom filter be above the toolbar of a list?**
    -   We think that the custom filter belongs as close to the grid as possible, because it more directly affects the list, just as the commands in the toolbar do. Additionally, this position makes the logical order of the elements consistent across different page patterns.

### Open issues

-   **Do we allow Show More/Less in the Custom Filter Group? An example is BudgetAnalysisInquiry\_PSN.**
    -   No, that will currently be a custom container. If we have enough examples, we might add a new container subpattern.
-   **Does the pattern limit the possible input types to those that allow constrained input values?**
    -   The pattern currently allows any input, but it's against guidelines to have inputs that have unconstrained values.
-   **Do we allow groups to be used as custom filter groups?**
    -   We do allow them now, to make migration easier and to identify Custom Filter group locations. However, we encourage you to use only a small set of fields in these situations (and we might eventually enforce this).

### AX 2012 content

#### AX 2012 links

-   [MSDN AX 2012 How to Add Controls to the Filter Pane](/dynamicsax-2012/developer/how-to-add-controls-to-the-filter-pane)
-   [MSDN AX 2012 List Page Overview – section Filter Pane](/dynamicsax-2012/developer/list-page-overview)

#### AX 2012 example

[![Example.](./media/customfiltergroup5.png)](./media/customfiltergroup5.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
