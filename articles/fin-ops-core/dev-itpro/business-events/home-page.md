---
title: Business events overview
description: Learn about business events, which allow external systems to receive notifications from finance and operations apps.
author: jaredha
ms.author: johnmichalak
ms.date: 01/15/2026
ms.topic: overview
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Global for most topics. Set Country/Region name for localizations
ms.search.validFrom: Platform update 24
# ms.search.form:  [Operations AOT form name to tie this article to]
ms.dyn365.ops.version: 2019-02-28
---

# Business events overview

[!include[banner](../includes/banner.md)]

Business events provide a mechanism that lets external systems receive notifications from finance and operations apps. By using this mechanism, you can perform business actions in response to the business events.

Business events occur when a business process runs. During a business process, users who participate in it perform business actions to complete the tasks that make up the business process.

A business action that a user performs can be either a workflow action or a nonworkflow action. Approval of a purchase requisition is an example of a workflow action, whereas confirmation of a purchase order is an example of a nonworkflow action. Both types of actions can generate business events that external systems can use in integration and notification scenarios.

## Prerequisites

You can consume business events by using Microsoft Power Automate and Azure messaging services. Therefore, you must bring your subscriptions to these assets to use business events.

> [!IMPORTANT]
> Don't consider business events as a mechanism for exporting data. By definition, business events are supposed to be lightweight and nimble. They aren't intended to carry large payloads to fulfill data export scenarios.

## Implemented business events

Some business processes include business events that are implemented out of the box. These business events include both workflow and nonworkflow business events. For more information, see [Application business events](app-business-events.md), [Workflow business events](business-events-workflow.md), and [Alerts as business events](alerts-business-events.md).

Developers must use extensions to implement new business events. For more information, see [Business events developer documentation](business-events-dev-doc.md).

## Business event catalog

Access the business events catalog from **System administration > Set up > Business events**. The catalog lists the business events that are available in the instance you're using. The catalog is useful because it shows which business events are available, and you can filter it by category, business event ID, and name.

The category of a business event identifies its source. Business events that originate from the workflow system belong to the **Workflow** category. For business events that originate from other modules, the module name is the category name.

The system builds the business event catalog during database synchronization at the time of deployment. Therefore, you see the complete list of business events in the catalog. However, if you need to explicitly update the catalog, select **Manage \> Rebuild business events catalog**.

:::image type="content" source="../media/businesseventscatalog.png" alt-text="Screenshot of Business event catalog.":::

For each business event, the business event catalog shows a description. This description can help you better understand the business event and its context in the business process. The catalog also shows the list of data fields that the event sends.

In scenarios where external integration systems require the schema of the payload for a business event during development, select **Download schema** to download the JavaScript Object Notation (JSON) schema.

In summary, the business event catalog helps you identify the business events that are required for an implementation. It also helps you identify the schema for each business event.

The next step is to manage the endpoints.

## Business events parameters

### General

The **General** tab of the **Business events parameters** page provides general settings that apply to business events.

- **Retry count** – The number of times that the system tries again to send business events to an endpoint if an error occurs. The default value is **3**.
- **Wait time between retries** – The interval, in milliseconds, between attempts to send a business event to its endpoint. The default value is **1,000** milliseconds.
- **Endpoints allowed per event** – The maximum number of endpoints that can subscribe to the same business event in a legal entity. The default value is **10**.
- **Key vault secret cache interval** – The number of minutes that the system caches key vault secrets used for business events in memory before it reads and caches them again from the configured key vault. The default value is **5** minutes.

### Performance

The business events framework has two primary settings that affect performance: **Processing threads** and **Bundle size**. The application allocates dedicated batch threads to process business events in near-real time. Because threads are a shared resource for all batch processing, take care when you change the thread allocation for business events.

- **Processing threads** – The number of threads to use to process business events.

  - With dedicated processing for business events, the thread count is the number per Batch Application Object Server (AOS) instance.
  - The maximum value is **4**.

- **Bundle size** – The number of events to group together at a time for processing by a thread.

  - By increasing the number, you produce fewer bundles and reduce the ability to distribute the events to parallel threads.
  - By decreasing the number, you produce more bundles and increase the ability to distribute the events to parallel threads. However, if you make the number too small, you cause unnecessary parallelization on small bundles.

### Event Grid settings

The **Event Grid settings** tab provides options that apply to business event endpoints with an endpoint type of **Azure Event Grid**.

The **Send object in Event Grid data field** toggle controls whether the type of object serialized and sent to the Azure Event Grid endpoint is a JSON string or an object. By default, the object sent to these endpoints is serialized as a JSON string. Turning on this toggle sends these objects as an object to the Azure Event Grid endpoints.

### HTTPS settings

The **HTTP timeout (milliseconds)** toggle controls how long the default HTTPS adapter waits before timing out a request to an endpoint. The default timeout period is 10 seconds. Entering a value of **0** in the field indicates to use the default timeout period.

## Activating business events

Business events in the business event catalog aren't active by default. From the catalog, you can activate any business events that you need. Select one or more business events, and then select **Activate**.

:::image type="content" source="../media/businesseventsactivation.png" alt-text="Screenshot of Activating a business event.":::

You can activate business events in all legal entities or in specific legal entities. If you leave the **Legal entity** field blank, you activate the selected business events in *all* legal entities. If you need a business event only for specific legal entities, you must configure it separately for each legal entity.

You must assign endpoints to the business events that you activate. For more information about setting up and managing endpoints, see [Manage business event endpoints](managing-business-event-endpoints.md).

When business events occur as business processes run, the system does outbound processing only for activated business events.

After you activate business events, they appear on the **Active events** tab.

:::image type="content" source="../media/businesseventsactivetab.png" alt-text="Screenshot of Active business events.":::

From the **Active events** tab, you can deactivate business events. The system doesn't perform outbound processing for deactivated events.

After you deactivate business events, they appear on the **Inactive events** tab.

:::image type="content" source="../media/businesseventsinactivetab.png" alt-text="Screenshot of Inactive business events.":::

You can deactivate business events when you need to pause processing of business events for a period because of specific system maintenance activities in the integration landscape.

When business requirements change, some business events might no longer be required. In this case, you can deactivate them instead of deleting them from the list of active events. This approach is useful if you need to preserve the history of errors for the business events. You can delete inactivated business events later when there's no longer a business need to keep them deactivated.

## Errors

Errors can occur while the system does outbound processing of business events. These errors might prevent the system from successfully delivering a business event to the endpoint. If an error occurs, the system retries several times to successfully process the business event. However, if all attempts are unsuccessful, the system saves the business event in an error log.

You can access error logs from the **Active events**, **Inactive events**, and **Errors** tabs. The **Errors** tab shows all errors across all business events, whereas the other two tabs show errors in the context of a specific business event.

You can perform on-demand outbound processing on each error by using the **Resend** action. This action invokes the outbound processing logic. This logic includes retries. If the outbound processing is still unsuccessful, the error is logged in the error log. In this case, the **Last process time** field on the **Errors** tab indicates when the last attempt to process the event occurred.

If an error can't be successfully processed, you can use the **Download payload** option to download the payload from the event for offline processing, as you require.

> [!NOTE]
> If you delete an endpoint and associate a new endpoint with business events, you can still resend all errors that are associated with the business events. In this case, the system does outbound processing to send to the new endpoint that is associated with the corresponding business event. This functionality allows for graceful recovery from misconfiguration or other error states.

## Business event consumption models

Integration requirements and integration solution design for implementations vary. Integration requirements play a role in identifying the consumption model for business events. In summary, consider the following points when you design integrations that use business events:

- You can consume business events by using Power Automate, Service Bus, Event Grid, or other endpoint types.
- Customers must bring their own subscriptions to use Power Automate, Service Bus, Event Grid, or other endpoint types.
- You can activate a business event in all legal entities or in specific legal entities.
- You can send a business event to a unique endpoint or multiple endpoints.
- Power Automate can directly subscribe to business events.

## Idempotency

Business events enable idempotent behavior on the consuming side by having a control number in the payload. The consuming application can use the unique control number to detect duplicate delivery. The consuming application can't misread the control number as the sequence number because the control number isn't sequential. There can be gaps in the numbering space. The order in which events emitted in finance and operations apps isn't guaranteed to preserve the order in which they're delivered to the endpoints.

## Filtering in Azure Event Grid and Azure Service Bus

Azure Service Bus and Azure Event Grid support subscribing to topics by
specifying criteria on the incoming message. For more information, see [Topic filters and actions](/azure/service-bus-messaging/topic-filters) and [Understand event filtering for Event Grid subscriptions](/azure/event-grid/event-filtering).

A business event that is sent to an Azure Service Bus or Azure Event Grid
has the following fields made available for this purpose. Subscribers can use
this information to subscribe to more specific topics as required.

- **Category** – The business event category shown in the
    business event catalog. It's useful as a filter when a common
    article is used for receiving business events from multiple categories and
    subscribers want to only receive business events for the category that they're
    interested in.

- **Business event ID** – Business event ID is the class name of the business event
    implementation shown in the business event catalog. Business event ID uniquely
    identifies the business event (not the instance of the business event). It
    helps in validation of received business events on the consumer side to
    ensure the expected business event is being received and processed.

- **Legal entity** – The legal entity in which the business event
    happened. Legal entity is useful information to base the consuming logic on if
    the processing and distribution of business events on the consumption side
    must be driven by a legal entity.

> [!NOTE]
> The filterable fields that are sent in a business event can be modified to
include custom fields. This is a developer experience.

## Role-based security for business events

Apply role-based security to business events to meet the following requirements by using the appropriate security artifact.

| **Requirement**                                                                                                                                | **Privilege**                                 | **Duty**                          |
|------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------|-----------------------------------|
| Only certain users can access and view the business events catalog.                                                                             | **BusinessEventsCatalogView**                 | None                              |
| Only certain users can activate business events.                                                                                               | **BusinessEventsCatalogMaintain**             | None                              |
| Only certain users can create and manage endpoints.                                                                                            | **Business events security privilege**        | **Business events security duty** |
| Users can only subscribe to business events they're granted access to from external applications like Power Automate.                         | **Subscribe to business events from service** | None                              |
| Only certain users can view the business events security setup.                                                                                | **BusinessEventsCatalogSecuritySetupView**    | None                              |
| Only certain users can manage business events security.                                                                                        | **Maintain business events catalog security** | None                              |

Add these privileges to the required duties to grant corresponding roles appropriate access levels.

### Enabling role-based security for business events

Role-based security for business events must be enabled via Feature management.

1. Go to **System administration \> Feature management**.

2. Select the **Business events catalog security** feature.

3. Enable the feature.

4. Go to the business events catalog via **System administration \> Set up \> Business events \> Business events catalog.**

5. The **Security** tab in the catalog is where a business event must be mapped to one or more roles. You must complete the configuration as required.

6. Enable security by selecting the **Enable** menu button on the **Security** menu on the top navigation pane. An informational message confirms if security is enabled or disabled.

7. Modify the necessary security role to add the appropriate privilege or the duty based on security noted in the informational message.

### Subscribe to business events from service

Users having access to the privilege **Subscribe to business events from service** via their roles are able to only see and subscribe to business events that are assigned to their roles, as described below. The organizational assignments that are done, if any, as part of role-based security is honored in the context of business events by letting users to only subscribe
to business events in the organizations to which they have access to via their roles. This behavior is effective using any service calls like from Power Automate or Logic Apps.

### Backward compatibility

To ensure backward compatibility, understand the following behavior.

- Role-based security for business events is disabled by default.

- Even if you enable the feature in Feature management, role-based security doesn't take effect.

- You must explicitly enable role-based security in the business events catalog via the **Security** menu.

- After you enable role-based security, security is enforced. Any user with an administration role doesn't notice any change in behavior. However, nonadmin users either see only business events that their roles were assigned to in the business events catalog security configuration or don't see any business events because their roles weren't assigned to any business events.

> [!NOTE]
> To ensure uninterrupted functionality, understand the backward-compatibility behavior described in this section before you enable security on business events.

### Limitations

Business events that occur in finance and operations apps are processed asynchronously across multiple systems to deliver them to the target endpoint. Therefore, the order in which the apps emit the events isn't guaranteed to preserve the order in which they're delivered to the endpoints.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
