---
title: Release production orders
description: Learn about release production orders, including outlines on characteristics of the released state and releasing jobs to the shop floor.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: ProdParmRelease
ms.topic: conceptual
ms.date: 03/02/2021
ms.custom: 
  - bap-template
---

# Release production orders

[!include [banner](../includes/banner.md)]

A released production order is an order that has been authorized for production. The term Released is used to describe a state in the production order life cycle, where the production order is available for execution on the production shop floor and for warehouse processes.

## Characteristics of the Released state

The **Released** state is one state in the production order life cycle. Production orders that are in the **Released** state are available for execution on the production shop floor and for warehouse processes. The **Released** state has the following characteristics:

- A production order can be changed to the **Released** state either from the production order or by using a batch process. The production order can also be updated automatically from planned production orders that are firmed by using the **Firming time fence** field on the **Master plan** page.
- The **Released** state is the signal for the shop floor operators (operators) to start executing the production jobs on the shop floor.
- Production papers, such as route cards, route jobs, and jobs cards provide information about production jobs and can be issued.
- For materials that are physically reserved, warehouse work is generated to pick materials for the production order.

## Releasing jobs to the shop floor

After a production order is released, production jobs that are related to the order are visible and ready for registration. The operators can make job registrations, such as Start, Stop, and Completion, on the [production floor execution interface](production-floor-execution-use.md). The registered time and quantity are automatically transferred from the registration pages to production journals to keep track of the consumed time and quantity.

## Route cards

A route card provides an overview of information that comes from route and operation setups, and from operation and job scheduling methods.

## Route jobs

A route job lists each job of an operation in detail, and includes setup, process, queue, and transportation times. For example, an operation such as painting might require individual jobs, such as setup time, run time for the painting process, and queue time for drying.

## Job cards

A job card lists the individual job numbers of a particular operation. One job appears on each page. The jobs that are included on a job card, and their estimated times, come from the route and operation setup information. From a job card, you can open the **Production journal lines**, **job card** page. People who run operations resources can provide feedback about the production process. There are fields where you can enter consumption statistics and information such as the error quantity.

## Warehouse work for raw material picking

Work for raw material picking is generated during release. Work is generated only for the quantity of materials that was physically reserved for the production order before the order was released. The following setup is required to generate warehouse work for raw material picking:

- A location directive for raw materials picking that determines which warehouse location to pick the materials in
- A wave template for raw materials, where policies for the execution of warehouse work are configured
- A production input location that determines where materials are put

When using license plate controlled locations, you can choose whether the ordered quantity or the full quantity available for the item should be picked while processing the raw material picking work. To set this option:

1. Go to **Product information management \> Products \> Released products** and open the relevant item.
1. Expand the **Warehouse** FastTab.
1. Select one of the following options for the  **Material picking in license plate locations** field:
    - *Order picking*: Only the ordered quantity should be picked.
    - *Staging*: Whenever possible, the full quantity available at the license plate should be picked. For a worker to be able to pick the full license plate quantity, the license plate must not contain mixed items and must not have mixed dimensions. If the license plate contains mixed dimensions or items, the pick will proceed as if it were set to *Order picking*.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]