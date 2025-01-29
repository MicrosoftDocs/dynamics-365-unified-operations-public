---
title: Create service orders manually   
description: Learn how you can create service orders manually by using a service agreement or by using the service orders page, including step-by-step processes. 
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMAServiceOrderTable, SMAAgreementTable
ms.topic: how-to
ms.date: 01/06/2025
ms.custom: 
  - bap-template
---

# Create service orders manually

[!include [banner](../includes/banner.md)]

You can create service orders manually by using a service agreement or by using the **Service orders** page. You can also create a service order from a project.

> [!TIP]
> You can use automated processes to create service orders.

## Create a service order manually from a service agreement

1. Go to **Service management** \> **Service agreements** \> **Service agreements**.
1. Select a service agreement or create a new service agreement.
1. Select the **Deliver** tab and in the **Create** group select **Planned service orders** to open the **Create service orders** page.

## Create a service order manually on the Service orders page

1. Go to **Service management** \> **Service orders** \> **Service orders**.
1. Select **New** to create a new service order.
1. Create service order lines for the service order.

> [!NOTE]
> If the **Allow without service agreement** check box on the **Service management parameters** page is selected, you can post the transactions from the service order lines without attaching the service order to a service agreement. If the check box is cleared, you must attach the manually created service order to a project before posting the service order lines.

## Create a service order from a project

1. Go to **Project management and accounting** \> **Projects** \> **All projects**.
1. On the **Projects** page, on the Action Pane, select the **Manage** tab \> select **Service** \> **Service orders**.
1. Follow the previous procedure to create a service order manually on the **Service orders** page. The **Project ID** field displays the project reference.

> [!NOTE]
> If the **Allow without service agreement** check box on the **Service management parameters** page is selected, you can post the transactions from the service order lines without attaching the service order to a service agreement. If the check box is cleared, you must attach the manually created service order to a project before posting the service order lines.

## Create a service order from the Sales order page

You can create a service order from the **Sales orders** page by using the **Create a new service order based on the sales order** wizard.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Open the relevant sales order.
1. On the **Sales order** tab, select **Service order** to start the **Create a new service order based on the sales order** wizard.
1. Select **Next \>**, and then complete the following steps on the **Select agreement for service order** page:
      - Use the **Service agreement** field to select the service agreement with which the new service order should be associated.
      - Optional: Use the **Project ID** field to associate this service order with a particular project.

1. Select **Next \>**, and then complete the following steps on the **Create service order** page:
      - Enter a date and time for the service call to begin in the **Preferred service time** field.
      - Optional: Modify the text in the **Description** field. By default, this field contains the description of the service agreement that you selected on the previous page.
      - In the **Responsible** field, select the ID of the employee who is responsible for the agreement, and if you know what it is, enter the ID of the customer's preferred technician for the service call.
      - In the **Contact ID** field, select the person in the customer's company who should be contacted regarding this service order.

1. Select **Next \>**, and then select **Finish**.

## Related information

- [Service orders](service-orders.md)
- [Create service orders automatically](create-service-orders-automatically.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
