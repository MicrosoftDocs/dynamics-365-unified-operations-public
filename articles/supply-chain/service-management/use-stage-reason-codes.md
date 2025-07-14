---
title: Use stage reason codes 
description: You use a reason code to indicate why a service level agreement (SLA) has been canceled, or why a service order has exceeded the defined time limit.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMAServiceOrderTable, SMAParameters
ms.topic: how-to
ms.date: 07/10/2025
ms.update-cycle: 1095-days
ms.custom: 
  - bap-template
  - evergreen
---


# Use stage reason codes

[!include [banner](../includes/banner.md)]

You use a reason code to indicate why a service level agreement (SLA) has been canceled, or why a service order has exceeded the time limit that is you define in the SLA.

You can also specify that a reason code is required when an SLA is canceled, or when the time limit exceeds the time that is specified in the SLA for the service order.

If you have specified that a reason code is required, you must enter a reason code in the following situations:

- When a service order is moved to a stage that stops time recording against the SLA for the service order
- When the service order is signed off
- When time recording is manually stopped

## Set up reason codes

1. Go to **Service management** \> **Setup** \> **Service orders** \> **Stage reason codes**.

2. On the **Stage reason codes** page, select **New** to create a new reason code.

3. In the **Stage reason code** field, enter a unique stage reason code.

4. In the **Description** field, enter a description of the stage reason code.

5. Close the page to save your changes.

## Require reason codes when a service level agreement is canceled

1. Go to **Service management** \> **Setup** \> **Service management parameters**.

2. On the **Service management parameters** page, select the **General** link, and then select the **Reason code on canceling** check box.

## Require reason codes when a service order exceeds the time limit that is set by the service level agreement

1. Go to **Service management** \> **Setup** \> **Service management parameters**.

2. On the **Service management parameters** page, select the **General** link, and then select the **Reason code on exceeding time** check box.

## Related information

- [Start and stop time recording on a service order](start-and-stop-time-recording-on-a-service-order.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
