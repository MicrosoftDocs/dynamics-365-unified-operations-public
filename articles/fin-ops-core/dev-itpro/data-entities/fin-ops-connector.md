---
title: Application Connector
description: Learn about the Application Connector for Microsoft Power Automate and Logic Apps, including prerequisites, triggers, and actions.
author: pnghub
ms.author: johnmichalak
ms.topic: article
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global for most topics. Set Country/Region name for localizations
ms.search.validFrom:
ms.search.form:
ms.dyn365.ops.version: 2019-02-28
---

# Application Connector

[!include[banner](../includes/banner.md)]

The application connector enables Microsoft Power Automate, Power Apps, Data Integrator, and Logic Apps to integrate with finance and operations. An external application can use the available trigger and actions to integrate with them.

> [!IMPORTANT]
> You can't use the Application Connector for integrations with Dynamics 365 Finance + Operations (on-premises) instances.

## Prerequisites

To familiarize yourself with connectors, see the following articles before proceeding further:

- [Connectors](/connectors/)
- [Data management package REST API](data-management-api.md)
- [Open Data Protocol (OData)](odata.md)
- [Recurring integrations](recurring-integrations.md)

## Triggers

The trigger *When a business event occurs* exposes business events. For detailed information about business events, see [Business events in Microsoft Power Automate](../business-events/business-events-flow.md) and [Business events](../business-events/home-page.md).

## Actions

This section describes the actions that are available in the connector.

### Get a record

Use this action to fetch a record for a specific data entity from the target instance.

*Instance* refers to the URL of the target instance of the application to which the connector must connect. Enter the URL without the `https://` prefix or choose one from the drop-down menu. This list shows all the environments that are deployed in the Microsoft Entra tenant for the user account that you used to sign in to the specific client like Power Automate, Power Apps, or Logic App.

*Entity name* refers to the data entity from which the record must be fetched. The drop-down menu shows the list of data entities from the target environment.

*Object ID* refers to the primary keys fields that must be specified to uniquely identify the record that must be fetched. The values must be specified as a comma-separated list of values in the order that is defined in the entity.

### Create a record

This action can be used to create data records for a data entity.

*Instance* is the URL of the target instance to which the connector connects. Enter the URL without the `https://` prefix or choose one from the drop-down menu. This menu lists all the environments that are deployed in the Microsoft Entra tenant for the user account that you used to sign in to the specific client, like Power Automate, Power Apps, or Logic App.

*Entity name* refers to the data entity in which the record must be created. The dropdown menu shows the list of data entities from the target environment.

Based on the selected data entity, the list of fields displayed will be vary.

### Update a record

This action can be used to update an existing data record for a data entity. The usage is the same as the create a record action.

### Delete a record

This action can be used to delete an existing data record for a data entity. The usage is the same as the get a record action.

### Execute action

Use this action to invoke methods on a data entity to perform a business action.

*Instance* is the URL of the target instance to which the connector connects. Enter the URL without the `https://` prefix or choose one from the drop-down menu. This menu lists all the environments that are deployed in the Microsoft Entra tenant for the user account that you used to sign in to the specific client, like Power Automate, Power Apps, or Logic App.

*Action* is the method on the data entity that you want to execute. The list of fields that you see varies based on the selected method. These fields represent the parameters for the selected method.

### Get list of entities

Use this action to get the list of entities for further use in the app that you're developing.

*Instance* is the URL of the target instance to which the connector connects. Enter the URL without the `https://` prefix or choose one from the drop-down menu. This menu lists all the environments that are deployed in the Microsoft Entra tenant for the user account that you used to sign in to the specific client, like Power Automate, Power Apps, or Logic App.

### List items present in the table

Use this action to get the list of records from an entity. This action supports cross-company reading of data.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
