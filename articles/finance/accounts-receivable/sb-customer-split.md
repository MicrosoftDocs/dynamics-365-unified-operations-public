---
# required metadata

title: Customer split on billing schedules
description: This article describes how to split a customer with subscription billing 
author: JodiChristiansen
ms.date: 11/04/2022
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
ms.search.validFrom: 2022-11-05
ms.dyn365.ops.version: 10.0.31

---
# Customer split on billing schedules

On a billing schedule, the **Invoice account** is the customer that receives the sales order invoice to pay the bill. There are scenarios where more than one customer can pay for an invoice. The **Customer split** functionality allows you to add more customers that can be billed for the same billing schedule. This functionality is enabled by going to **Subscription billing > Recurring contract billing > Setup > Recurring contract billing parameters**. Set **Customer split** to **Yes**. 

## Customer split on billing schedule header
Once a billing schedule is created, additional customers can be added to the billing schedule header. Select **Customer split** on the **Billing schedule** tab. The customer assigned as the **Billing schedule customer** is listed at the top in the **Customer account** and **Customer account name** fields. The new customer account added can't be the same as the invoice account. 

To add a new customer:
1. Select **Add line** on **Customer split lines**. 
2. Select a new customer and then enter the percentage of each invoice for this customer. 
3. The start date and end date default to the billing schedule start and end date. Enter different start and end dates if the new customer will pay this percentage for only a portion of the billing schedule. For example, if the billing schedule has a start and end date of January 1 – December 31 and the new customer is billed 40% for the first nine months enter January 1 – September 30 as the start and end dates and 40.00 as the **Percentage**. 

You can add more than one customer to the **Customer split lines**. The total percentage entered must not total more than 100 percent. Enter a **Customer reference** and **Customer requisition** as informational fields that will be displayed on the sales order line during the **Generate invoice** process. 

The **Line details** will display the added customers’ **Contact information**, **Delivery address**, **Bill to address** and **Payment details** and will be displayed on the sales order for the customer. 

When adding customer split information to the billing schedule header, if there are unbilled billing schedule lines on the billing schedule, you'll be asked to roll
down the changes. **“Do you want to roll down the change from the header to the lines? Changes will only update the billing schedule lines that are not billed.”** Select **Yes** to update the **Customer split** information on the billing schedule line. Changes won't be updated if the billing schedule line has already been billed. 

If a billing schedule is created using the **Copy schedule** option, the **Customer split header lines** information will default and can't be the same as the **Customer account**.

When the **Generate invoice** process is complete, multiple sales orders (and sales invoices if posting automatically) will be created. These can be viewed in the **View billing detail page**, **Line details**, **Invoice** tab. **Multiple** is shown on the billing detail line to indicate multiple sales orders and sales invoices were created. 

## Customer split on billing schedule lines

The Customer split can be added to each individual billing schedule line if you only want to split certain billing schedule lines. Mark the **Customer split** checkbox
on the line, select **Customer split** on the billing schedule line menu to update or enter the **Customer split** information. 

The **Audit** information is updated if the billing schedule has already been billed and then the percentage is changed on the billing schedule line. Any lines billed
after that will use the new percentage. 

>[!NOTE]
> - The customer split option can't be used with stocked products. 
> - If the **Unbilled revenue** checkbox is marked, the **Customer split** checkbox can't be marked. 
> - If using **Revenue split only**, the parent line has the **Customer split** option, the child line items don't. 

