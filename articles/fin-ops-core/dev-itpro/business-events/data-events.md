---
# required metadata

title: Data events
description: This topic provides an overview of data events in Finance and Operations.
author: jaredha
ms.date: 10/15/2021
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: jaredha
ms.search.validFrom: 2021-10-15
ms.dyn365.ops.version: 10.0.22
---

# Data events

Data events are events based on changes to data in Finance and Operations. Create, update, and delete (CUD) events can be enabled for each entity. For example, if the Create event is enabled on the "Purchase order headers V2" entity, an event notification is emitted each time a new purchase order is created in the database.

All OData-enabled entities in Finance and Operations, both standard and custom, are able to emit data events. In the data events catalog, each of the events for an entity is listed as a data event to which subscriptions can be established. The concept of activa6ting the data event and associating a data event to an endpoint is like the concepts with business events. When a data event happens, the payload of teh event will contain the corresponding entity record.

> [!NOTE]
> Data events are only available for Finance and Operations environments for which the Power Platform integration has been enabled. See [Enabling the Power Platform integration](enable-power-platform-integration.md) for more information.

## Data events catalog

The data events catalog is accessed from the **Business events** page in Finance and Operations (System administration > Setup > Business events). The data events catalog lists the data events that are available in the Finance and Operations environment. The catalog displays the full list of available data events. For each data event, the catalog shows the category, event ID, name, and whether the event is company-specific. The catalot allows you to filter the list by category and data event ID.

![Data events catalog](../media/businessevents_dataeventscatalog.png)

## Activating data events

Data events are not active by default. To activate a data event from the data event catalog, select the event(s) in the list, and select the **Activate** action. 

Data events can be activated either in all legal entities or in specific legal entities. In the **Legal entity** field of the **Configure new data event** pane, select the legal entity in which you want to activate the data event. If you leave the **Legal entity** field blank, the selected data event(s) will be activated in all legal entities. If a data event is required in multiple specified legal entities, the event must be configured separately for each legal entity.

Only company-specific data events can be configured for specific legal entities. When configuring data events that are not company-specific, the **Legal entity** field will be disabled, and the data event will be enabled for all legal entities.

You must select a configured endpoint to activate the data event. For information on configuring endpoints business events and data events, see [Managing endpoints](home-page.md#managing-endpoints).

Activating a data event adds the event to the list on the **Active data events** tab of the page, and makes it available for subscription through the selected endpoint.

![Configure new data event](../media/businessevents_activatedataevent.png)

## Deactivating data events

From the **Active data events** tab you can deactivate data events. To deactivate a data event, select the event(s) in the list, and select **Deactivate**. This action removes the event(s) from the list of active data events, and adds it to the **Inactive data events** list. 

Data events, similar to business events, can be deactivated when processing of business events must be temporarily paused. Reasons this may be needed can include specific system maintenance or some bulk data imports or processing. Bulk data processing with data events enabled on the related data entities may send a high volume of data events that may or may not be needed, and that may impact system performance.

When data events are no longer needed to meet business requirements, you can delete the data event from either the **Active data events** or **Inactive data events** list. This removes the event from the list and deletes all error history for the event. Deactivating the data event may be used rather than deleting the event if the history of errors for the data event must be preserved. See [Errors](home-page.md#errors) for more information on error logs for business events and data events.

## Download the data event schema

The **Data events catalog** page also displays the fields that are passed to the data event that make up the event schema. This includes the field name and field label. Selecting the **Download schema** action allows you to download the JavaScript Object Notation (JSON) schema for the event. This is helpful where external integration systems require the schema of the payload for a business event during development.

[!include[banner](../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]
