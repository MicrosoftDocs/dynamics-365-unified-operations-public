---
# required metadata

title: Service orders  
description: This topic provides an overview of how to work with service orders.
author: sorenva
ms.date: 05/01/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMAServiceOrderTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sorenand
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Service orders

[!include [banner](../includes/banner.md)]

A service order represents a visit that a service technician makes to a customer site on a specific date. Each service order consists of one or more service order lines. Service order lines represent the hours of work that must be performed by the service technician, and the related items, expenses, and fees.

You can attach tasks and objects to a service order line. You can then group service order lines by task or by object. You can also attach items that are listed in inventory to service order lines.

## Create service orders

You can create service orders based on a service agreement and the lines that are contained in that agreement. However, you can create service orders that are associated with a service agreement only in the period that is specified in the agreement. For example, if a service agreement is valid for the 2011 calendar year, you can create service orders for the agreement from January 1, 2011, and December 31, 2011.

You can also create service orders individually, without associating them with an agreement. These service orders can be used to handle unscheduled or one-time service visits. For example, in the month of March, your customer wants service to be performed on two machines, in addition to the machines that are specified in the service agreement. For this task, you create service orders but do not associate them with an agreement.


> [!NOTE]
> To create service orders that are not associated with a service agreement, you must select the **Allow without service agreement** check box in the **Service management parameters** page.

### Scenario

The following scenario describes another situation where it is useful to create a service order that is not associated with a service agreement.

The company dispatcher receives a call requesting emergency service on an elevator. There is no time to set up a service agreement and a project for the service. Therefore, the dispatcher creates a service order directly in the **Service orders** page, attaches the service order to an existing project, and creates the service order lines. The dispatcher also creates a task or object relation for an existing service order, to record work that is not related to the service agreement. For more information, see [Create service orders manually](create-service-orders-manually.md) and [Create service task relations](create-service-task-relations.md).

## Monitor the progress of service orders

To monitor the progress of a sales order through the different teams and work processes, you can set up a system of stages and reason codes for service orders. For each stage, you can specify the actions that are allowed. For more information, see [Create reason codes](create-reason-codes.md).

### Example

A service order is approved by the dispatcher. The dispatcher updates the stage of the service order and specifies a reason code that indicates that the service order has been released to the service technician. The technician goes to the customer site and performs the service.

## Specify item requirements for service orders

You can specify the inventory items that are required for service orders. However, the service order must be associated with a project. Item requirements for service orders are processed through a project. 

### Example

The service orders that are created from the service agreement are processed by the dispatcher. For the first service order, the dispatcher realizes that the service technician requires an important spare part that is not in the on-hand inventory. Therefore, the dispatcher creates an item requirement for the spare part directly from the service order.

## Move and post lines

A service technician returns from a service visit, and then modifies and updates the service order lines. During the service visit, the technician performed a service job that was scheduled for the next service visit. Therefore, the technician moves the lines from the next service visit to the current service visit. The technician then posts the service order. For more information, see [Move service order lines](move-service-order-lines.md).

## Cancel service orders

One of the other service orders that was generated for the month of January becomes obsolete, because the job is canceled. Therefore, the service dispatcher cancels the service order. For more information, see [Cancel service orders](cancel-service-orders.md).

## Post from projects

At the end of each week, the dispatcher wants to post all service orders that are attached to a specific project. Therefore, the dispatcher locates the relevant project in the **Projects** page and posts the service orders that have been completed. For more information, see [Post service orders (class form)](https://technet.microsoft.com/library/aa574685\(v=ax.60\)).

## Delete service orders

During the second half of the year, your customer decides that the service visits are too infrequent. You must create a new, more frequent series of service visits for the remaining time on the service agreement. Therefore, you must delete the existing service orders and create new service orders. For more information, see [Delete service orders](delete-service-orders.md).

## See also

[Service orders (form)](https://technet.microsoft.com/library/aa554361\(v=ax.60\))

  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]