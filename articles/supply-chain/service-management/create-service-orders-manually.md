---
title: Create service orders manually
TOCTitle: Create service orders manually
ms:assetid: baa499dc-5003-4e1d-bb0c-3f8990e67548
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Aa498854(v=AX.60)
ms:contentKeyID: 36059127
ms.date: 04/18/2014
mtps_version: v=AX.60
_tocRel: gg243195(v=ax.60)/toc.json
f1_keywords:
- project
- sales order wizard
- service agreement
- service order
---

# Create service orders manually 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

You can create service orders manually by using a service agreement or by using the **Service orders** form. You can also create a service order from a project.


> [!TIP]
> <P>You can use automated processes to create service orders. For more information, see <A href="create-service-orders-automatically.md">Create service orders automatically</A></P>



## Create a service order manually from a service agreement

1.  Click **Service management** \> **Common** \> **Service agreements** \> **Service agreements**.

2.  Select a service agreement or create a new service agreement.

3.  Click the **Deliver** tab and in the **Create** group click **Planned service orders** to open the **Create service orders** form.

4.  See [Create service orders (class form)](https://technet.microsoft.com/en-us/library/aa553901\(v=ax.60\)) for more information about how to create a service order.

## Create a service order manually in the Service orders form

1.  Click **Service management** \> **Common** \> **Service orders** \> **Service orders**.

2.  Press Ctrl+N to create a new service order.

3.  Create service order lines for the service order.


> [!NOTE]
> <P>If the <STRONG>Allow without service agreement</STRONG> check box in the <STRONG>Service management parameters</STRONG> form is selected, you can post the transactions from the service order lines without attaching the service order to a service agreement. If the check box is cleared, you must attach the manually created service order to a project before posting the service order lines.</P>



## Create a service order from a project

1.  Click **Project management and accounting** \> **Common** \> **Projects** \> **All projects**.

2.  In the **Projects** form, on the **Action pane**, click the **Manage** tab \> click **Service** \> **Service orders**.

3.  Follow the previous procedure to create a service order manually in the **Service orders** form. The **Project ID** field displays the project reference.


> [!NOTE]
> <P>If the <STRONG>Allow without service agreement</STRONG> check box in the <STRONG>Service management parameters</STRONG> form is selected, you can post the transactions from the service order lines without attaching the service order to a service agreement. If the check box is cleared, you must attach the manually created service order to a project before posting the service order lines.</P>



## Create a service order from the Sales order form

You can create a service order from the **Sales orders** form by using the **Create a new service order based on the sales order** wizard.

1.  Click **Sales and marketing** \> **Common** \> **Sales orders** \> **All sales orders**.

2.  Open the relevant sales order.

3.  On the **Sales order** tab, click **Service order** to start the **Create a new service order based on the sales order** wizard.

4.  Click **Next \>**, and then complete the following steps on the **Select agreement for service order** page:
    
      - Use the **Service agreement** field to select the service agreement with which the new service order should be associated.
    
      - Optional: Use the **Project ID** field to associate this service order with a particular project.

5.  Click **Next \>**, and then complete the following steps on the **Create service order** page:
    
      - Enter a date and time for the service call to begin in the **Preferred service time** field.
    
      - Optional: Modify the text in the **Description** field. By default, this field contains the description of the service agreement that you selected on the previous page.
    
      - In the **Responsible** field, select the ID of the employee who is responsible for the agreement, and if you know what it is, enter the ID of the customer's preferred technician for the service call.
    
      - In the **Contact ID** field, select the person in the customer's company who should be contacted regarding this service order.

6.  Click **Next \>**, and then click **Finish**.

## See also

[About service orders](about-service-orders.md)

[About automatically creating service orders](about-automatically-creating-service-orders.md)

  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

