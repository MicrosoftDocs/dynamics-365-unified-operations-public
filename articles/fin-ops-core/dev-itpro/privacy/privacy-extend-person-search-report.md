---
title: Extend the Person search report
description: This article walks you through the process of extending the Person search report for finance and operations.
author: josaw1
ms.date: 04/21/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: AX 7.0.0
---

# Extend the Person search report

[!include [banner](../includes/banner.md)]

The Person search report for finance and operations apps is backed by an intelligent search processor that is designed to manage a collection of entities for a single person. The Person search report searches finance and operations data and creates a set of resulting identifiers. Each result references a search category (for example, Customer) and a result record in a related table. For information about using the Person search report, refer the [Person search report](privacy-person-search-report.md) article.

> [!NOTE]
> The Person search is available for Dynamics 365 Finance, Supply Chain Management, Commerce, and Human Resources. The Person search report is not currently available for Microsoft Dynamics AX 2012.

## Add another entity to the default template

You can add any entity to the default Person search report template. Open the **Data management** workspace, and select **Templates**. Add the entity to the template. The entity that you add must include at least one of the fields that are used to filter the Person search report. 

## Create a new search category

1. Use the **PersonSearchResultCategory** enumeration to distinguish different categories of results, such as workers versus applicants.
2. Extend the **PersonSearchResultCategory** enumeration as needed to create new result types.

## Create search processing for the new search category

In this example, you will create a new processor class.

1. Extend the **PersonSearchModule** enumeration with a new search area.
2. Create a class that extends the **PersonSearchProcessor** class and includes the **PersonSearchProcessorFactoryAttribute** attribute, with the new person search module area as a parameter. 
3. In the **PersonSearchProcessor** extended class, override the **doSearch** method with your desired search logic. As shown in the following example, extend the **PersonSearchResult** table to create new table relationships.

    ```xpp
    PersonSearchResultCategory::Customer needs a relation:PersonSearchResult.ResultRecId = CustTable.RecId,PersonSearchResult.ResultTableId = CustTable.TableId
    ```

## Integrate with the Global address book (Optional)

If you want to integrate with the Global address book, insert any discovered party numbers into the **PersonSearchPartyNumberTmp** table. The **findPartyLink** method of **PersonSearchProcessor** tries to link party numbers to other search artifacts, such as users, customers, or vendors.

This method has a delegate, **onFindPartyLink**, that lets you specify additional artifacts to search, based on the party numbers.

The **PersonSearchCriteria** tables let end users specify the parameters by which to search the system for personal data.

## Create new search criteria

If you need new search criteria, follow these steps.

1. Extend the **PersonSearchCriteriaName**, **PersonSearchCriteriaAddress**, and **PersonSearchCriteriaKnownId** tables, or create your own tables.
2. Extend the **PersonSearchDialog** form to show these new data fields.
3. Use the new criteria during search processing.

The **PersonSearch** form shows the set of results that was discovered by a person search.

## Show the new search category in the PersonSearch form

1. Create a new view on the **PersonSearchResult** table. This view should restrict results to only your new **PersonSearchResultCategory**.
2. Join the view to your result record, and create the view fields that are needed (for example, **PersonSearchResultCustomerView**).
3. Extend the **PersonSearchResult** table to create a new relationship to the new view. This relationship should join on the person search ID.
4. Extend the **PersonSearch** form:

    1. Add the new view as a data source.
    2. Add a new tab to the results with the result grid and the **Include/Exclude** buttons.
    3. Create event handlers for the **Include/Exclude** buttons to update the **PersonSearchResult** records.

        The **PersonSearchEventHandler::updateMarkedOnButtonClicked()** method is provided for convenience.

> [!NOTE]
> If you want to see the record count in the result caption, create an event handler on the **OnQueryExecuted** view data source event. Next, call the **setResultCountOnGridCaption()** method on the **PersonSearch** form to update the count.

Each **PersonSearchEntityFilterRelation** record specifies the conditions when a filter should apply, and the filter table and field to apply.

The set of filter relations is compared to the template metadata when the package is built.

For a filter to be created, a **PersonSearchResult** record with the matching filter category must exist. After it's found, the **PersonSearchResult** references the table field where the filter value resides.

## Create new filters

1. Use the Chain of Command to extend the **PersonSearchEntityFilterRelation** table.
2. Decide on the type and source of the new filter:

    1. If the filter is an extended data type (EDT) or enumeration, set the **MetadataTypeId** to the data type ID.
    2. If the filter is a source table field, specify the source table and source field IDs.
    3. If the filter is an entity field, specify the entity field ID.

3. Decide on the filter table and filter field.

    The filter table must be available as a **PersonSearchResult** with a matching category. Otherwise, no filters will be created.

4. Insert the new filter record.

    The person search framework will automatically manage initialization of all exclusions when the form is first opened. Exclusions let you suppress the filter building functionality for specific entity fields.

## Create new exclusions

1. Use the Chain of Command (COC) to extend the **PersonSearchEntityExclusion** table.
2. In the **CoC method**, specify the entity, the entity field, and whether the exclusion is active.
3. Insert the new exclusion record.

    The person search framework will automatically manage initialization of all exclusions when the form is first opened.

### Disclaimer
(c)2018 Microsoft Corporation. All rights reserved. This document is provided "as-is." Information and views expressed in this document, including URL and other Internet Web site references, may change without notice. You bear the risk of using it. This document does not provide you with any legal rights to any intellectual property in any Microsoft product. You may copy and use this document for your internal, reference purposes. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
