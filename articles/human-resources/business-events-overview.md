---
# required metadata

title: Human resources business events overview
description: This article provides an overview of business events.
author: twheeloc
ms.date: 05/06/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HRMParameters, EssWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: ["51941", "intro-internal"]
ms.assetid: 2cfb061a-a616-4bf9-9d98-9cde00039eec
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-03-19
ms.dyn365.ops.version: Human Resources

---

# Human resources business events overview

Business events provide a mechanism that enables external systems to receive notifications from finance and operations apps. In this way, the systems can perform business actions in response to the business events.

Business events occur when a business process is run. During a business process, users perform business actions to complete the tasks that make up that business process.

A business action that a user performs can be either a workflow action or a non-workflow action. Approval of a purchase requisition is an example of a workflow action, whereas confirmation of a purchase order is an example of a non-workflow action. Both types of actions can generate business events that external systems can use in integration and notification scenarios.

## Prerequisites

Business events can be consumed by using Microsoft Power Automate and Azure messaging services. Therefore, customers must bring their subscriptions to those assets to use business events.

For more information about business events, see [Business events overview](../fin-ops-core/dev-itpro/business-events/home-page.md).

## Human resources business event catalog

You can find the business event catalog by going to **System administration \> Set up \> Business events** and filter the category column to Human Resources. The business event catalog lists the business events that are available in the instance that you're using. The catalog is useful because it shows which business events are available, and you can filter it by category, business event ID, and name.

The category of a business event identifies its source. Business events that originate from a workflow are assigned to the **Workflow** category. For business events that originate from other modules, the module name is used as the category name.

The business event catalog is built during database synchronization at the time of deployment. Users should see the complete list of business events in the catalog. If an explicit update of the catalog is required, go to **Manage \> Rebuild business events catalog**.

![Filter to Human Resources](./Media/overview-filter.png)

For each business event, the business event catalog shows a description. This description can help you better understand the business event and its context in the business process. The catalog also shows the list of data fields that will be sent out in the event. 

In scenarios where external integration systems require the schema of the payload for a business event during development, select **Download schema** to download the JavaScript Object Notation (JSON) schema.

In summary, the business event catalog helps identify the business events that are required for an implementation. It also helps identify the schema for each business event. The next step is to manage the endpoints.

For more information about business events such as activation, performance, and errors, see [Business events overview](../fin-ops-core/dev-itpro/business-events/home-page.md#activating-business-events) and [Business event consumption models](../fin-ops-core/dev-itpro/business-events/home-page.md#business-event-consumption-models).

### Human resources business events 

- Personnel actions (position change)
- Hire actions
- Task assignment
- Leave request assigned
- Leave request complete
- Leave of absence return
- Time off cancelled
- Course assignment
- Course completion
- Goal assignment


For a full list of business events, review the business events catalog and search category: Human Resources.
