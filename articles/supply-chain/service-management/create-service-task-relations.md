---
# required metadata

title: Create service task relations   
description: You can associate service tasks with service agreements or service orders in order to describe the service task to be completed for the agreement or order.
author: sorenva
ms.date: 05/01/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMAServiceOrderTable, SMAAgreementTable
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

# Create service task relations    

[!include [banner](../includes/banner.md)]

You can associate service tasks with service agreements or service orders in order to describe the service task to be completed for the agreement or order. This information is available to service technicians and customers.

## Create a relation with a service agreement

1.  Go to **Service management** \> **Common** \> **Service agreements** \> **Service agreements**.

2.  Select an existing service agreement, or create a new service agreement.

3.  On the Action Pane, select the **Service tasks** button.

4.  On the **Service tasks** form, select **New** to create a new line, and then select a service task from the **Service task** list to attach the service task to the service agreement.

5.  On the **Description** tab, enter any internal or external note descriptions in the free text fields.

6.  Close the form to save the record.

Repeat this procedure until you have created all the necessary service task relations for the service agreement. You can now specify these service tasks for any attached agreement lines.

A service tasks relation that is created on a service agreement is available from all service orders that are attached to the service agreement.

## Create a relation with a service order

1.  Go to **Service management** \> **Common** \> **Service orders** \> **Service orders**.

2.  Select an existing service order, or create a new service order.

3.  On the Action Pane, select the **Service tasks** button.

4.  From the **Service tasks** form, select **New** to create a new line, and then select a service task from the **Service task** list to attach the service tasks to the service order.

5.  On the **Description** tab, enter any internal or external note descriptions in the free text fields.

6.  Close the form to save the record.

Repeat this procedure until you have created all the necessary service task relations for the service order. You can now select the service task for which you have created the relation when you create service order lines.

Service task relations that are created on a service order are available on the specific service order.

## See also

[Service tasks overview](service-tasks.md)


  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]