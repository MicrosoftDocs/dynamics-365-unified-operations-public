---
title: Service level agreements overview
description: In a service level agreement, the customer agrees to a minimum response time based on when the service company records the issue and when the issue is resolved.
author: ChristianRytt
ms.author: crytt
ms.reviewer: kamaybac
ms.search.form: SMAServicelevelagreement
ms.topic: how-to
ms.date: 08/26/2024
ms.custom: 
  - bap-template
  - evergreen
---

# Service level agreements overview

[!include [banner](../includes/banner.md)]

A service level agreement (SLA) is an agreement between a service company and a service customer. In a SLA, the customer agrees to a minimum response time based on when the service company records the issue and when the issue is resolved.

A SLA enforces a standard level of service that is offered to customers, and also makes it transparent to a service company when a service job should be completed.

Any number of SLAs can be created to offer service customers different levels of service.

## Create a service level agreement

1. Go to **Service management** \> **Setup** \> **Service agreements** \> **Service level agreements**.
1. Type a name for the service level agreement in the **Service level agreement** field.
1. Type the time that you want to allow for completion of service calls that are attached to the service level agreement. Then select a calendar if you want to base the service level agreement on a specific calendar.

## Apply a service level agreement

The SLA is applied directly to a service agreement.

Service orders that you create manually and attach to a service agreement that has an SLA are measured against that SLA.

Service orders that you create automatically aren't attached to an SLA.

## Apply the service level agreement to the service agreement

1. Go to **Service management** \> **Service agreements** \> **Service agreements**.
1. Select the service agreement that you want to apply the SLA to, and then select **Edit** on the **Action Pane**.
1. In the **Service level agreement** field, select the SLA that you want to assign.

## Apply the service level agreement to the service agreement group

1. Go to **Service management** \> **Setup** \> **Service agreements** \> **Service agreement groups**.
1. In the **Service level agreement** field, select the SLA that you want to assign.

## Track time on a service order against an SLA

When you create a new service order for a service agreement that an SLA is assigned to, the time interval for the delivery of the service is initiated, and the system starts to track the delivery time. Additionally, you can set the following options:

- You can start and stop time recording on the service order to register the total amount of time that is spent on service orders.
- You can monitor compliance with the time interval that is set in the service level agreement.
- You can define reason codes that must be set if the time interval of the service level agreement is exceeded.

## Related information

- [View compliance with service level agreements](view-compliance-with-service-level-agreements.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
