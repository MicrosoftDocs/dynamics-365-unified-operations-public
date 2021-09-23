---
# required metadata

title: Application Connector
description: This topic provides information about the Application Connector for Microsoft Power Automate and Logic Apps.
author: peakerbl
ms.date: 03/08/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global for most topics. Set Country/Region name for localizations
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom:
ms.dyn365.ops.version: 2019-02-28
---

# Application Connector

[!include[banner](../includes/banner.md)]

The application connector allows Microsoft Power Automate, Power Apps, Data Integrator, and Logic Apps to integrate with Finance and Operations. An external application can use the available trigger and actions to integrate with them.

> [!IMPORTANT]
> The Application Connector cannot be used for integrations with Dynamics 365 Finance + Operations (on-premises) instances.

## Prerequisites
We recommend that you read the following topics as a prerequisite to familiarize yourself with connectors before proceeding further

- [Connectors](/connectors/) 
- [Data management package REST API](data-management-api.md)
- [Open Data Protocol (OData)](odata.md) 
- [Recurring integrations](recurring-integrations.md) 

## Triggers
Business events are exposed using the trigger *When a business event occurs*. For detailed information about business events, refer to [Business events in Microsoft Power Automate](../business-events/business-events-flow.md) and [Business events](../business-events/home-page.md).

## Actions

This section describes the actions that are available in the connector.

**Get a record**

This action can be used to fetch a record for a specific data entity from the target instance.

*Instance* refers to the URL of the target instance of the application to which the connector must connect. The expected value is to enter the URL without the ‘https://’ prefix or choose one from the drop-down menu. This lists of all the environments that are deployed in the Azure Active Directory tenant for the user account that was used to sign in to the specific client like Power Automate, Power Apps, or Logic App.

*Entity name* refers to the data entity from which the record must be fetched. The drop-down menu shows the list of data entities from the target environment.

*Object ID* refers to the primary keys fields that must be specified to uniquely identify the record that must be fetched. The values must be specified as a comma-separated list of values in the order that is defined in the entity.

**Create a record**

This action can be used to create data records for a data entity.

*Instance* refers to the URL of the target instance to which the connector must connect. The syntax for this value is to enter the URL without the ‘https://’ prefix or choose one from the drop- menu. This lists of all the environments that are deployed in the Azure Active Directory tenant for the user account that was used to sign in to the specific client like Power Automate, Power Apps, or Logic App.

*Entity name* refers to the data entity in which the record must be created. The dropdown menu shows the list of data entities from the target environment.

Based on the selected data entity, the list of fields displayed will be vary.

**Update a record**

This action can be used to update an existing data record for a data entity. The usage is the same as the create a record action.

**Delete a record**

This action can be used to delete an existing data record for a data entity. The usage is the same as the get a record action.

**Execute action**

This action can be used to invoke methods on a data entity to perform a business action.

*Instance* refers to the URL of the target instance to which the connector must connect. The syntax for this value is to enter the URL without the ‘https://’ prefix or choose one from the drop- menu. This lists of all the environments that are deployed in the Azure Active Directory tenant for the user account that was used to sign in to the specific client like Power Automate, Power Apps, or Logic App.

*Action* refers to the method on the data entity that must be executed. Based on the selected method, the list of fields displayed will be vary. These fields represent the parameters for the selected method.

**Get list of entities**

This action can be used to get the list of entities for further use in the app that is being developed.

*Instance* refers to the URL of the target instance to which the connector must connect. The syntax for this value is to enter the URL without the ‘https://’ prefix or choose one from the drop- menu. This lists of all the environments that are deployed in the Azure Active Directory tenant for the user account that was used to sign in to the specific client like Power Automate, Power Apps, or Logic App.

**List items present in the table**

This action can be used to get the list of records from an entity. This action supports cross-company reading of data.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
