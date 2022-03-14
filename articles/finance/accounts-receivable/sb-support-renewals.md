---
# required metadata

title: Support and renewal levels
description: This topic explains how to set up and use the support and renewal process on sales transaction which will create a billing schedule.
author: JodiChristiansen
ms.date: 11/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Support and renewals 

This topic explains how to enter detailed information about the support or renewal item for the sales transaction. This information is used to calculate the charge amount for the original support contract and/or the renewal amount for creating a billing schedule in Subscription billing.

You can enter the support or renewal contract information, or both. When you enter the support contract information, only the support item is added to the sales document. When you enter the renewal contract information, the renewal item is used to create a billing schedule.


[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Modules > Subscription billing > Recurring contract billing > Setup > Support and renewal levels

This topic explains how to set up different support levels for support and renewal items. 

You can select the default support levels on the **Recurring contract billing parameters** page. 

For example, a company offers the following different support levels: 

| Level | Percentage|
| :------------- |-------------:| 
| Unlimited| 40%|
| Gold| 25% | 
| Silver| 20%|  
| Bronze| 15%|  


## Processes

Create a support or renewal level: 
1. Select **New**. 
2. Specify a unique **Support level** name and **Description**. 
3. Select the **Support calculation method**. If you select **Percent**, type a **Support percentage**. 
4. Select the **Renewal calculation method**. If you select **Percent**, type a **Renewal percentage**. 
5. Select **Save**.

Delete a support or renewal level: 
1. Select one or more lines that you want to delete, and select **Delete**. 
2. When you are asked to confirm the action, select **Yes**.

Edit a support or renewal level: 
1. Select the line you want to edit. 
2. Select **Edit**. 
3. Make the necessary changes, and select **Save**. 


## Fields

This page contains the following fields: 

| Field| Description|
| :------------- |:-------------| 
| **Support level**| Specify a unique identifier for the support or renewal level (for example, Gold or Silver). | 
| **Description**| Specify a description for the support or renewal level.|  
| **Support calculation method**| Select the support calculation method for the level: **Percent** or **Standard amount**. |  
| **Support percentage**|Specify a percentage to be used for calculating the support item price. If standard amount is selected, the amount is specified at the time the transaction is created.  | 
| **Renewal calculation method**| Select the support calculation method for the level: **Percent** or **Standard amount**.|  
| **Renewal percentage**| Specify a percentage to be used for calculating the renewal item price. If standard amount is selected, the amount is specified at the time the transaction is created. |      


---

# Support and renewal audit

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Modules > Advanced recurring contract billing > Billing schedules > All or Active billing schedules > [click a billing schedule] >[select a billing schedule line] > [click Support and renewal] 

This topic explains how to enter detailed information about the support or renewal item for the sales transaction. This information is used to calculate the charge amount for the original support contract and/or the renewal amount for creating a billing schedule in Subscription billing.

You can enter the support or renewal contract information, or both. When you enter the support contract information, only the support item is added to the sales document. When you enter the renewal contract information, the renewal item is used to create a billing schedule.

When a customer allows a support contract to lapse, you are asked if you want to make the billing schedule active again. 

When you want to make a sale that includes the first year of support only, without an automatic renewal of the support contract, clear the **Create/Update Renewal** option so that when you post the sales transaction, a recurring billing schedule is not created.

![Note icon](../../../Resources/images/icons/iAXnote.gif)**Note:** The support and renewal is available for only the sales order and has no other association with the existing billing schedule. 


## Edit Support/Renewal Information

To edit support and renewal information for a billing schedule line, follow these steps: 
1. In the list of all billing schedules, click the **Schedule number** of the billing schedule.  
1. In the **Billing schedule lines** section, select a line and click **Support and renewal**. 
1. Review all the information for the support or renewal item. 
1. If needed, change the support level or renewal percentage or amount, and type a **Reason code**. 
1. Select **Process**.

## Fields

This page contains the following fields: 

| Field| Description|
| :------------- |:-------------| 
|**Schedule number**|Displays the billing schedule number. |
|**Description**|Displays a description of the billing schedule. |
|**Item number**|Displays the item number for the billing schedule line. |
|**Product name**|Displays the product name. |
|**Support level**|Select the support level for the renewal or support item. |
|**Renewal percentage**|Specify the renewal percentage used when calculating the unit price for a renewal item in a billing schedule.|
|**Renewal amount**|Specify the renewal amount used when calculating the unit price for a renewal item in a billing schedule.|
|**Reason for change**|Displays the reason for changing the support and renewal information. When you make changes to this page, you can type a reason for the change. You must enter a reason when you change the **Renewal percentage**, **Renewal amount**, or **Support level**. |
|**Original sales item**|Displays the original sales item number of the original. |
|**Original new amount**|Displays the original new amount for the item. |
|**Original support level**|Displays the original support level for the item. |
|**Original renewal percentage**|Displays the original renewal percentage for the item. |
|**Original renewal amount**|Displays the original renewal amount for the item. |
|**Sales lines**|
|**Old support level**|Displays the previous support level. |
|**Old renewal percentage**|Displays the previous renewal percentage. |
|**Old renewal amount**|Displays the previous renewal amount. |
|**User modified**|Displays the user name who made the change. |
|**Modification date**|Displays the date on which he change occurred. |
|**Reason**|Displays the reason for the change. |

## Buttons

This page contains the following buttons: 

| Button| Description|
| :------------- |:-------------| 
|**Process**|Updated the support or renewal item with the changes specified. |
|**Close**|Closes the page. |

---

# Support and renewal workflow

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]


# Support and renewal workflow

This topic lists the steps for using the support and renewal functionality in Subscription billing to apply different support levels to items, and to update renewal information.

Ensure a system administrator completes the setup tasks:
1. [Create a support or renewal level](../setup/SupportRenewLevel.md). 
2. [Associate an item with support and renewal items](../setup/ItemSetup.md). 
3. [Specify the default support and renewal settings for new billing schedules](../setup/Parameters.md). 

To use the support and renewal functionality where you can apply different support levels to items and update renewal information, follow this general workflow:

1. On the [Sales Order](../general/SalesOrder.md) page, create a sales order. 
2. In the **Sales order lines** FastTab, add an item and edit any of the values as needed. 
3. In the header of the sales order, select the **Invoice** tab, and then select **Support and renewal &amp;amp;gt; Add support and renewal**, which opens the [Support and Renewal Process](../enduser/SupprrtRenewProc.md) page. <br />The header section is automatically updated with the default settings from the [Advanced Recurring Contract Billing Parameters](../setup/Parameters.md), which can be changed as needed. These values apply to all the support and renewal items (for example, if the billing frequency is Annually, all sales lines that have a renewal item are created with the annual frequency). <br />To associate the sales order with an existing billing schedule, select a **Billing schedule number**. <br />![Tip icon](../../../Resources/images/icons/iAXtip.png)**Tip:** To change the support or renewal start date, set **Override start date** to **Yes**. 
4. On the [Support and Renewal Process](../enduser/SupprrtRenewProc.md), select **OK** to return to the [Sales Order](../general/SalesOrder.md). 
5. Select **Generate &amp;amp;gt; Invoice**. <br />When the sales order is posted, the billing schedule is created. A notification with the billing schedule information appears in the **Message details**. Make note of the billing schedule number. 
6. Open the [All/Active Billing Schedules](../enduser/BillSchedActiv.md) list and select the billing schedule number to review the details of the billing schedule on the [Billing Schedules](../enduser/BillSched.md) page. 
   - To review the details of the lines created, go to the [Billing Schedule Lines](../enduser/BillSched.htm#LinesGrid) FastTab and select **Support and renewal**. The [Support and Renewal Audit](../enduser/SupportRenewAudit.md) page opens. 
   - After you are done reviewing the information, close the window. <br />![Note icon](../../../Resources/images/icons/iAXnote.gif)**Note:**  If the renewal start date for a billing schedule line needs to be changed, you can edit the **Start date** for the line on the [Billing Schedules](../enduser/BillSched.md) page. When you review the [Billing Detail](../enduser/BillingDetail.md) page for the line, the **Billing start date** is updated with the new date and the **Billing end date** is recalculated based on the billing frequency. The renewal start date can be updated only if the first invoice for the renewal billing schedule has not yet been created and posted. After the first invoice is created and posted, the start date cannot be edited. 


## Additional resources

[Support and Renewal Workflow](../workflow/SupprtrtRenewWF.md)

[Support and Renewal Process](../enduser/SupprrtRenewProc.md)

[Support and Renewal Audit](../enduser/SupportRenewAudit.md)
