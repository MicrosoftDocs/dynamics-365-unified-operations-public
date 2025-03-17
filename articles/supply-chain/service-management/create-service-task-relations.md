---
title: Create service task relations   
description: You can associate service tasks with service agreements or service orders in order to describe the service task to be completed for the agreement or order.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMAServiceOrderTable, SMAAgreementTable
ms.topic: how-to
ms.date: 01/30/2025
ms.custom: 
  - bap-template
---

# Create service task relations

[!include [banner](../includes/banner.md)]

You can associate service tasks with service agreements or service orders in order to describe the service task to be completed for the agreement or order. This information is available to service technicians and customers.

## Create a relation with a service agreement

1. Go to **Service management** \> **Service agreements** \> **Service agreements**.

2. Select an existing service agreement, or create a new service agreement.

3. On the Action Pane, select the **Service tasks** button.

4. On the **Service tasks** page, select **New** to create a new line, and then select a service task from the **Service task** list to attach the service task to the service agreement.

5. On the **Description** tab, enter any internal or external note descriptions in the free text fields.

6. Close the page to save the record.

Repeat this procedure until you have created all the necessary service task relations for the service agreement. You can now specify these service tasks for any attached agreement lines.

A service tasks relation that is created on a service agreement is available from all service orders that are attached to the service agreement.

## Create a relation with a service order

1. Go to **Service management** \> **Service orders** \> **Service orders**.

2. Select an existing service order, or create a new service order.

3. On the Action Pane, select the **Service tasks** button.

4. From the **Service tasks** page, select **New** to create a new line, and then select a service task from the **Service task** list to attach the service tasks to the service order.

5. On the **Description** tab, enter any internal or external note descriptions in the free text fields.

6. Close the page to save the record.

Repeat this procedure until you have created all the necessary service task relations for the service order. You can now select the service task for which you have created the relation when you create service order lines.

Service task relations that are created on a service order are available on the specific service order.

## Related information

- [Service tasks overview](service-tasks.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
