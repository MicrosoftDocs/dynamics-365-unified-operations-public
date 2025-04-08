---
title: Develop and establish service agreements overview
description: Service agreements let you define the resources that are used in a typical service visit and how those resources are invoiced to the customer.
author: Henrikan
ms.author: henrikan
ms.topic: overview
ms.date: 07/25/2019
ms.reviewer: kamaybac
ms.search.form: SMAAgreementTable
---

# Develop and establish service agreements overview

[!include [banner](../includes/banner.md)]

Service agreements let you define the resources that are used in a typical
service visit and how those resources are invoiced to the customer.

Every service agreement is attached to a project through which transactions are
posted and invoiced. However, you can also invoice service order transactions
directly through the project without first having to connect the service order
to a service agreement. You might decide to do this if the service order is for
a one-time-only service visit and the need for processing the service
transactions quickly outweighs the need for maintaining detailed
service-agreement information about the customer over a period of time.

## Service agreement

In each service agreement, you must specify a project, a service-agreement ID,
and a service-agreement group. The service-agreement group can be used to sort
and organize service agreements.

A service agreement header contains settings that apply to all attached
agreement lines:

- Whether the service agreement is suspended. If the service agreement is suspended, you cannot generate service orders from the service agreement.
- The duration of the service agreement.
- How service-order lines are to be combined into service orders.
- Whether the service agreement is a template.

In the service-agreement header, you also set up all the service objects and
service tasks that can be used with the service agreement by entering the
specific service tasks or service objects that are to be attached to the various
lines of the agreement.

From the service-agreement header, you can also copy service-agreement lines or
service-template lines into the current service agreement.

You can suspend service agreements and stop individual service agreement lines.

If you select the **Suspended** check box on a service agreement, you cannot:

- Create service orders automatically or manually from the service agreement.

If you select the **Stopped** check box on a service agreement line, you cannot:

- Create service orders automatically or manually from the service agreement line.
- Copy the service agreement line into another service agreement or service order.

> [!NOTE]
> If a service agreement is suspended, all the attached lines are stopped, regardless of their individual status.

## Service-agreement lines

Each service-agreement line describes in detail the content of the proposed
service work. The lines contain the following settings:

- The transaction type and the description of the transaction type.
- The employee who performs the service work.
- The objects on which service must be performed for the service agreement.
- The frequency with which work is performed and associated item, expense, and fee transactions are registered.
- The time window within which service-order lines can be grouped into a service order.
- The service tasks that are used to group sets of agreement lines together into work tasks and to summarize for service technicians and customers what service task is to be provided.
- Whether a line is stopped. If a line is stopped, you cannot create service orders for that individual line.
- Project settings, such as the category and the line property.

## Related information

- [Create service agreements](create-service-agreements.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
