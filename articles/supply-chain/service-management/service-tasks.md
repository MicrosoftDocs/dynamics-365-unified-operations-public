---
title: Service tasks overview
description: Use service tasks to describe the task to be completed during a service order. Both technicians and customers can see this information. 
author: ChristianRytt
ms.author: crytt
ms.reviewer: kamaybac
ms.search.form: SMAServiceTask
ms.topic: how-to
ms.date: 08/26/2024
ms.custom: 
  - bap-template
  - evergreen
---

# Service tasks overview

[!include [banner](../includes/banner.md)]

Use service tasks to describe the task to be completed during a service order. Both technicians and customers can see this information.

You create service tasks in the **Service tasks** page, and you associate service tasks with a specific service agreement or service order by creating service task relations. Every time that you create a service task relation, you can create the following:

- Internal notes for the task, such as detailed technical requests for the task that are important for the technician to know.

- External notes that the customer can see. These might provide a less technical explanation of the task that is being completed, according to the agreement between the customer and the service company.

When you have set up a service task relation between a service task and a
service order or service agreement, you can specify this service task when you
create service order lines or service agreement lines for the current service
order or service agreement.

When you generate service orders from a service agreement, you can use the
service tasks that are assigned to each service agreement line to group service
order lines into service orders.

## Create a service task

1. Go to **Service management** \> **Setup** \> **Service tasks**.
2. Create a new line.
3. Enter the service ID and description.

## Example

A technician must complete two jobs on a gearbox (service object GB-1234) at a
customer site. A service agreement is created for the customer, and several
transactions are associated with the jobs. The service agreement and service
agreement lines for the two jobs are as follows:

### Service agreement

| Project | Service agreement | Description                                  | Group   |
|---------|-------------------|----------------------------------------------|---------|
| 9012    | 000008\_001       | Inspection and routine replacement – GB-1234 | Premium |

### Service agreement lines

| Description             | Transaction type | Service object | Service task |
|-------------------------|------------------|----------------|--------------|
| Inspection and cleaning | Hour             | GB-1234        | I/C - GB1234 |
| Travel                  | Expense          | GB-1234        | I/C - GB1234 |
| Materials               | Item             | GB-1234        | I/C - GB1234 |
| Routine replacement     | Hour             | GB-1234        | RR - GB1234  |
| GR-1                    | Item             | GB-1234        | RR - GB1234  |
| GR-5                    | Item             | GB-1234        | RR - GB1234  |

The service agreement lines for the two jobs have two service tasks attached to them. The service tasks determine the transactions that belong to each job. In the first case, service task I/C - GB1234 identifies all the service agreement lines that are involved in the inspection and cleaning of object GB-1234. In the second case, service task RR - GB1234 identifies all the service agreement lines that are involved in completing a routine replacement job.

The service task relations that connect the service tasks to the specific agreement are as follows:

### Service tasks

| Service task | Description | Internal note | External note |
|--|--|--|--|
| I/C - GB1234 | Inspection of gearbox GB-1234 | Visual and mechanical inspection and cleaning of gearbox GB-1234 | Routine inspection of gearbox |
| RR - GB1234 | Routine replacement of parts in GB-1234 | Routine service replacement of GR-1 and GR-5 components (for gearboxes manufactured before 2002, also replace GR-2 component) | Routine replacement of parts |

## Group service orders

When you create service orders automatically, you can use service tasks as grouping criteria. To group service orders by service tasks, define on the service agreement that service orders that are based on the service agreement should be grouped by service task ID as their initial grouping criteria.

## Group by service task

1. Go to **Service management** \> **Service agreements** \> **Service agreements**.
2. On the **Setup** tab, select **By service task** in the **Combine service orders** field.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
