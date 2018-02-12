---
# required metadata

title: Alerts overview
description: TBD
author: tjvass
manager: AnnBe
ms.date: 02/12/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: EventCreateRule
# ROBOTS:
audience: Application user
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: tjvass
ms.search.validFrom: 2018-15-28
ms.dyn365.ops.version: Platform update 15
---

# Alerts overview

[!include[banner](../includes/banner.md)]

## About alerts
Alerts form a notification system for critical events in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. You can use alerts to stay informed about events that you want to keep track of during the workday. You can easily set up your own set of rules so that you are alerted about overdue deliveries, orders that are deleted, prices that change, or other events that you must respond to.

Here are a few common scenarios in enterprise resource planning that will utilize the alerts feature available in Finance and Operations.

### Scenario 1:  Create an alert rule for new sales orders
   1. Navigate to the **All sales orders** page.
   2. Click the **Options** menu.
   3. In the **Share** area, click **Alert me** and then select  **Create alert rule**.
   4. The **Create alert rule** pane displays. Expand the **Alert me when** section. 
   5. In the **Event list**, select **Record has been created**. 

### Scenario 2:  Create an alert rule for postponement of a delivery date
   1. Navigate to the **All purchase orders** page.
   2. Click on a purchase order ID to access the purchase order details.
   3. Expand the **Purchase order header** tab. 
   4. Click the **Options** menu.
   5. In the **Share** area, click **Alert me** and then select  **Create alert rule**.
   6. The **Create alert rule** pane displays. Expand the **Alert me when** section. 
   7. In the **Field** list, select **Delivery date**.
   8. In the **Event** list, select **has been postponed**. 
	
When you close the **Create alert rule** pane, your rule appears in the **Manage alert rules** page.  Use the **Manage alert rules** page to update your existing alert rules.  This include modifying event triggers, updating event notifications, and expiration dates.  Access the **Manage alert rules** page using the **Alert me** drop-down in the **Options** menu.

### What occurs when an alert rule is created?
When you create alert rules, you can associate a predefined event with a field. For example, when the date that is specified in the field occurs, or when the contents of a field change. Alternatively, you can associate an event with the records on a particular page. For example, when the record is created or deleted. 

When the selected event occurs for that field, or a record on that page, an alert is sent to you. For example, you create a rule in which you associate the **Delivery date** field on a specific purchase order line with the **was due this amount of time ago** event. You set the time frame to five days. In this example, an alert is triggered five days after the delivery date of that purchase order line. 

Additionally, you can refine the alert rules by setting conditions. For example, you can be alerted about new purchase orders that are created for specific vendor accounts. 

### Preparing for an alert
Before you set up an alert rule, decide when or in what situations you want to receive alerts. When you know which event you want to be notified about, locate the page where the data that causes the event is displayed in Finance and Operations. The event can be a date that arrives or a change that occurs. Therefore, you must find the page where this date is specified, or where the field that changes or the new record is displayed. When you have this information, you can proceed with creating your alert rule.

### Components of an alert rule
There are five components to an alert rule:

   1. **Event** - The event that triggers an alert rule can be a date that arrives or a specific change that occurs. Events are defined in the **Alert me when** area of the **Create alert rule** pane.
   2. **Condition** - In the **Alert me for** area of the **Create alert rule** pane, you can use choose the scope of the condition to control when you are alerted about events.  Choose to apply the rule to only the current record, or all visible records on the page.  You can also set the rule to be Organization-wide if the rule applies across legal entities.
   3. **Expiry of rule** - In the **Alert me until** area of the **Create alert rule** pane, you can specify how long you want the alert rule to be active.
   4. **Contents** - In the **Alert me with** area of the **Create alert rule** pane, you can specify the subject text and message text that you want the alert messages to use. 
   5. **User** - In the **Alert me with** area of the **Create alert rule** pane, you can specify which user you want to receive the alert messages. By default, your user ID is selected.  
   > [!Note]
   > This option is restricted to Organization administrators.

