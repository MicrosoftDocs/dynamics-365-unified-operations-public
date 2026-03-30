---
title: Extend the Person search report
description: Learn about the process of extending the Person search report for finance and operations, including an overview on adding another entity to the default template.
author: josaw1
ms.author: josaw
ms.topic: how-to
ms.date: 03/13/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: AX 7.0.0
---

# Extend the Person search report

[!include [banner](../includes/banner.md)]

The Person search report for finance and operations apps uses an intelligent search processor that manages a collection of entities for a single person. The Person search report searches finance and operations data and creates a set of resulting identifiers. Each result references a search category, such as Customer, and a result record in a related table. For information about using the Person search report, see [Person search report](privacy-person-search-report.md).

> [!NOTE]
> The Person search is available for Dynamics 365 Finance, Supply Chain Management, Commerce, and Human Resources. The Person search report isn't currently available for Microsoft Dynamics AX 2012.

## Add another entity to the default template

You can add any entity to the default Person search report template. Open the **Data management** workspace, and select **Templates**. Add the entity to the template. The entity that you add must include at least one of the fields that the Person search report uses for filtering. 

## Create a new search category

1. Use the **PersonSearchResultCategory** enumeration to distinguish different categories of results, such as workers versus applicants.
1. Extend the **PersonSearchResultCategory** enumeration as needed to create new result types.

## Create search processing for the new search category

In this example, you create a new processor class.

1. Extend the **PersonSearchModule** enumeration with a new search area.
1. Create a class that extends the **PersonSearchProcessor** class and includes the **PersonSearchProcessorFactoryAttribute** attribute, with the new person search module area as a parameter. 
1. In the **PersonSearchProcessor** extended class, override the **doSearch** method with your desired search logic. As shown in the following example, extend the **PersonSearchResult** table to create new table relationships.

    ```xpp
    PersonSearchResultCategory::Customer needs a relation:PersonSearchResult.ResultRecId = CustTable.RecId,PersonSearchResult.ResultTableId = CustTable.TableId
    ```

## Integrate with the global address book (optional)

To integrate with the global address book, insert any discovered party numbers into the **PersonSearchPartyNumberTmp** table. The **findPartyLink** method of **PersonSearchProcessor** tries to link party numbers to other search artifacts, such as users, customers, or vendors.

This method has a delegate, **onFindPartyLink**, that you can use to specify additional artifacts to search, based on the party numbers.

End users use the **PersonSearchCriteria** tables to specify the parameters for searching the system for personal data.

## Create new search criteria

To create new search criteria, follow these steps:

1. Extend the **PersonSearchCriteriaName**, **PersonSearchCriteriaAddress**, and **PersonSearchCriteriaKnownId** tables, or create your own tables.
1. Extend the **PersonSearchDialog** form to show these new data fields.
1. Use the new criteria during search processing.

The **PersonSearch** form shows the set of results that a person search discovers.

## Show the new search category in the PersonSearch form

1. Create a new view on the **PersonSearchResult** table. Restrict results to only your new **PersonSearchResultCategory**.
1. Join the view to your result record, and create the view fields that you need (for example, **PersonSearchResultCustomerView**).
1. Extend the **PersonSearchResult** table to create a new relationship to the new view. This relationship should join on the person search ID.
1. Extend the **PersonSearch** form:

    1. Add the new view as a data source.
    1. Add a new tab to the results with the result grid and the **Include/Exclude** buttons.
    1. Create event handlers for the **Include/Exclude** buttons to update the **PersonSearchResult** records.

        The **PersonSearchEventHandler::updateMarkedOnButtonClicked()** method is provided for convenience.

> [!NOTE]
> To see the record count in the result caption, create an event handler on the **OnQueryExecuted** view data source event. Next, call the **setResultCountOnGridCaption()** method on the **PersonSearch** form to update the count.

Each **PersonSearchEntityFilterRelation** record specifies the conditions when a filter should apply, and the filter table and field to apply.

The set of filter relations is compared to the template metadata when you build the package.

For a filter to be created, a **PersonSearchResult** record with the matching filter category must exist. After it's found, the **PersonSearchResult** references the table field where the filter value resides.

## Create new filters

1. Use the Chain of Command to extend the **PersonSearchEntityFilterRelation** table.
1. Decide on the type and source of the new filter:

    1. If the filter is an extended data type (EDT) or enumeration, set the **MetadataTypeId** to the data type ID.
    1. If the filter is a source table field, specify the source table and source field IDs.
    1. If the filter is an entity field, specify the entity field ID.

1. Decide on the filter table and filter field.

    The filter table must be available as a **PersonSearchResult** with a matching category. Otherwise, the process doesn't create filters.

1. Insert the new filter record.

    The person search framework automatically initializes all exclusions when you open the form.

## Create new exclusions

1. Use the Chain of Command (COC) to extend the **PersonSearchEntityExclusion** table.
1. In the **CoC method**, specify the entity, the entity field, and whether the exclusion is active.
1. Insert the new exclusion record.

    The person search framework automatically initializes all exclusions when you open the form.

### Disclaimer
(c) 2018 Microsoft Corporation. All rights reserved. This document is provided "as-is." Information and views expressed in this document, including URL and other Internet website references, might change without notice. You bear the risk of using it. This document doesn't provide you with any legal rights to any intellectual property in any Microsoft product. You can copy and use this document for your internal, reference purposes. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
