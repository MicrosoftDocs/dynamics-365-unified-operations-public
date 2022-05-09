---
# required metadata

title: Create service orders manually   
description: You can create service orders manually by using a service agreement or by using the **Service orders** form. 
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

# Create service orders manually    

[!include [banner](../includes/banner.md)]


You can create service orders manually by using a service agreement or by using the **Service orders** form. You can also create a service order from a project.

> [!TIP]
> <P>You can use automated processes to create service orders. 

## Create a service order manually from a service agreement

1.  Select **Service management** \> **Common** \> **Service agreements** \> **Service agreements**.

2.  Select a service agreement or create a new service agreement.

3.  Select the **Deliver** tab and in the **Create** group select **Planned service orders** to open the **Create service orders** form.

## Create a service order manually in the Service orders form

1.  Select **Service management** \> **Common** \> **Service orders** \> **Service orders**.

2.  Select **New** to create a new service order.

3.  Create service order lines for the service order.

> [!NOTE]
> <P>If the <STRONG>Allow without service agreement</STRONG> check box in the <STRONG>Service management parameters</STRONG> form is selected, you can post the transactions from the service order lines without attaching the service order to a service agreement. If the check box is cleared, you must attach the manually created service order to a project before posting the service order lines.</P>

## Create a service order from a project

1.  Go to **Project management and accounting** \> **Common** \> **Projects** \> **All projects**.

2.  In the **Projects** form, on the **Action Pane**, select the **Manage** tab \> select **Service** \> **Service orders**.

3.  Follow the previous procedure to create a service order manually in the **Service orders** form. The **Project ID** field displays the project reference.

> [!NOTE]
> <P>If the <STRONG>Allow without service agreement</STRONG> check box in the <STRONG>Service management parameters</STRONG> form is selected, you can post the transactions from the service order lines without attaching the service order to a service agreement. If the check box is cleared, you must attach the manually created service order to a project before posting the service order lines.</P>

## Create a service order from the Sales order form

You can create a service order from the **Sales orders** form by using the **Create a new service order based on the sales order** wizard.

1.  Go to **Sales and marketing** \> **Common** \> **Sales orders** \> **All sales orders**.

2.  Open the relevant sales order.

3.  On the **Sales order** tab, select **Service order** to start the **Create a new service order based on the sales order** wizard.

4.  Select **Next \>**, and then complete the following steps on the **Select agreement for service order** page:
    
      - Use the **Service agreement** field to select the service agreement with which the new service order should be associated.
    
      - Optional: Use the **Project ID** field to associate this service order with a particular project.

5.  Select **Next \>**, and then complete the following steps on the **Create service order** page:
    
      - Enter a date and time for the service call to begin in the **Preferred service time** field.
    
      - Optional: Modify the text in the **Description** field. By default, this field contains the description of the service agreement that you selected on the previous page.
    
      - In the **Responsible** field, select the ID of the employee who is responsible for the agreement, and if you know what it is, enter the ID of the customer's preferred technician for the service call.
    
      - In the **Contact ID** field, select the person in the customer's company who should be contacted regarding this service order.

6.  Select **Next \>**, and then select **Finish**.


## See also

[Service orders](service-orders.md)

[Create service orders automatically](create-service-orders-automatically.md)

[Create service orders (class form)](https://technet.microsoft.com/library/aa553901\(v=ax.60\)) 



[!INCLUDE[footer-include](../../includes/footer-banner.md)]