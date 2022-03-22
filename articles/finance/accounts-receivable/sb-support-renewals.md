---
# required metadata

title: Support and renewal levels
description: This topic explains how to set up and use the support and renewal process on sales transaction which will create a billing schedule for renewal items.
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
ms.reviewer: twheeloc
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

[!include [banner](../includes/banner.md)]

This topic explains how to enter support or renewal items when entering sales orders. These items are used to calculate the charge amount for the original support contract and/or the renewal amount for creating a billing schedule in **Subscription billing**. For example, your company sells a copier to a customer and you offer to provide a support contract for the first year of service with the option to renew that support contract yearly. The **Support item** is the support contract for the first year and the **Renewal item** is the renewal every year after that. You can enter the support or renewal contract information, or both. When you enter the support contract information, only the support item is added to the sales order. When you enter the renewal contract information, the renewal item is used to create a billing schedule.

When a support contract lapses, you are asked to make the billing schedule active again. 

To create a sales order that includes the first year of support only without an automatic renewal of the support contract: 
1. Clear the **Renewal** checkbox 
2. When the sales transaction is posted, a recurring billing schedule is not created.

> [!Note] 
> The support and renewal process is available for the sales order only and doesn't affect the existing billing schedule. When adding support and renewal to a sales order you can create a new billing schedule or add the renewal item to an existing billing schedule. 

## Support and renewal setup

On the **Support and renewal levels** page you can set up different support levels for support and renewal items. The support or renewal can be a percentage of the original item amount or it can be a standard amount. 

You can select the default support levels on the **Recurring contract billing parameters** page. 

For example, a company offers the following different support levels and renewal levels: 

| Support level | Percentage| Renewal percentage|
| :------------- | :------------- |-------------:| 
| Unlimited| 40%| 30%|
| Gold| 25% | 18%|
| Silver| 20%| 14%|  
| Bronze| 15%| 10%| 


Create a support or renewal level: 
1. Select **New**. 
2. Specify a unique **Support level** name and **Description**. 
3. Select the **Support calculation method**. If you select **Percent**, enter a **Support percentage**. 
4. Select the **Renewal calculation method**. If you select **Percent**, enter a **Renewal percentage**. 
5. Select **Save**.

Delete a support or renewal level: 
1. Select one or more lines that you want to delete, and select **Delete**. 
2. When you are asked to confirm the action, select **Yes**.

Edit a support or renewal level: 
1. Select the line you want to edit. 
2. Select **Edit**. 
3. Make the necessary changes, and select **Save**. 


### Fields

The **Support and renewal levels** page page contains the following fields: 

| Field| Description|
| :------------- |:-------------| 
| **Support level**| A unique identifier for the support or renewal level (for example, Gold or Silver). | 
| **Description**| A description for the support or renewal level.|  
| **Support calculation method**| Select the support calculation method for the level: **Percent** or **Standard amount**. |  
| **Support percentage**|Specify a percentage to be used for calculating the support item price. If standard amount is selected, the amount is specified at the time the transaction is created.  | 
| **Renewal calculation method**| Select the support calculation method for the level: **Percent** or **Standard amount**.|  
| **Renewal percentage**| Specify a percentage to be used for calculating the renewal item price. If standard amount is selected, the amount is specified at the time the transaction is created. |      

---

### Support and renewal audit

The **Support and renewal** audit allows you to review the details of the billing schedule lines created from the renewal item on a sales order. This is available when the billing schedule line item is a support or renewal item. 

To edit support and renewal information for a billing schedule line, follow these steps: 
1. On the **Support and renewal levels** page, click the **Schedule number** of the billing schedule.  
2. In the **Billing schedule lines** section, select a line and click **Support and renewal**. 
3. Review all the information for the support or renewal item. 
4. If needed, change the support level or renewal percentage or amount, and enter a **Reason code**. 
5. Select **Process**.

### Fields

The **Support and renewal audit** page contains the following fields: 

| Field| Description|
| :------------- |:-------------| 
|**Item number**|Displays the item number for the billing schedule line. |
|**Product name**|Displays the product name. |
|**Support plan level**|Select the support level for the renewal or support item. |
|**Renewal percentage**|Enter the renewal percentage used when calculating the unit price for a renewal item in a billing schedule.|
|**Renewal amount**|Enter the renewal amount used when calculating the unit price for a renewal item in a billing schedule.|
|**Reason for change**|Displays the reason for changing the support and renewal information. You must enter a reason when you change the **Renewal percentage**, **Renewal amount**, or **Support level**. |
|**Original sales item**|Displays the original sales item number from the sales order. |
|**Original new amount**|Displays the original new amount for the item. |
|**Original support level**|Displays the original support level for the item. |
|**Original renewal percentage**|Displays the original renewal percentage for the item. |
|**Original renewal amount**|Displays the original renewal amount for the item. |
|**Grid**|
|**Original support level**|Displays the previous support level. |
|**Original renewal percentage**|Displays the previous renewal percentage. |
|**Original renewal amount**|Displays the previous renewal amount. |
|**Modified by**|Displays the user name who made the change. |
|**Modification date and time**|Displays the date on which the change occurred. |
|**Reason**|Displays the reason for the change. |


## Support and renewal process

The **Support and renewal** functionality can apply different support levels to items and update renewal information in Subscription billing.

The following setup tasks must be completed first:
1. Create at least one support or renewal level in **Support and renewal levels**.
2. Associate an item with support and renewal items using **Item Setup**.
3. Specify the default support and renewal settings for new billing schedules in **Recurring contract billing paramaters**. 

To apply different support levels to items and update renewal information, follow this steps.

1. On the **Sales Order** page, create a sales order. 
2. On the **Sales order lines** FastTab, add an item and edit any of the values as needed. 
3. Select the **Invoice** tab > **Add support and renewal** under **Support and renewal**. 
4. On the **Support and Renewal Process** page the header section is updated with the default settings from the **Recurring Contract Billing Parameters**. These values apply to all the support and renewal items (for example, if the billing frequency is **Annually**, all sales lines that have a renewal item are created with the annual frequency). <br />To associate the sales order with an existing billing schedule, select a **Billing schedule number**. 
5. To change the support or renewal start date, set **Override start date** to **Yes**. 
6. On the **Support and renewal Process** page, select **OK**.
7. Select **Invoice** under the **Generate** tab. When the sales order is posted, the billing schedule is created. A notification with the billing schedule information appears in the **Message details**. 
8. Open the **All/Active billing schedules** list and select the billing schedule number to review the details of the billing schedule on the **Billing Schedules** page. 
   - To review the details of the lines created, go to the **Billing schedule lines** FastTab and select **Support and renewal**. 

> [!Note]
> If the renewal start date for a billing schedule line needs to be changed, you can edit the **Start date** for the line on the **Billing schedules** page. When you select the **View billing detail** page for the line, the **Billing start date** is updated with the new date and the **Billing end date** is recalculated based on the billing frequency. The renewal start date can be updated only if the first invoice for the renewal billing schedule has not been created and posted. After the first invoice is created and posted, the start date can't be edited. 


## Additional resources
