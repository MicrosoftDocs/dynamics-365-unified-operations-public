---
# required metadata

title: Terminate schedule lines
description: This topic 
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
# Customer split on billing schedules

On a billing schedule the Invoice account is the customer that receives the sales order invoice to pay the bill. There are scenarios where more than one customer can
pay for an invoice and the Customer split functionality allows you to add more customers that can be billed for the same billing schedule. Enable this functionality in 
Subscription billing > Recurring contract billing > Setup > Recurring contract billing parameters. Set Customer split to Yes. 

## Customer split on billing schedule header
Once a billing schedule is created additional customers can be added to the billing schedule header. Select **Customer split** on the Billing schedule tab. The customer
assigned as the Billing schedule customer is listed at the top in the **Customer account** and **Customer account name** fields. The new customer account added cannot be the
same as the invoice account. 

To add a new customer select Add line under Customer split lines. Select a new customer and then enter the percentage of each invoice for this customer. The start date
and end date default to the billing schedule start and end date. Enter different start and end dates if the new customer will pay this percentage for only a portion of
the billing schedule. For example, if the billing schedule has a start and end date of January 1 – December 31 and the new customer is billed 40% for the first 9 months
enter January 1 – September 30 as the start and end dates and 40.00 as the Percentage. 

You can add more than one customer to the Customer split lines. The total percentage entered must not total more than 100 percent. Enter a Customer reference and
Customer requisition as informational fields that will be written to the sales order line during the Generate invoice process. End user information can be added as
well.

The Line details will display the added customers’ Contact information, Delivery address, Bill to address and Payment details. These will be written to the sales order
for the customer. 

When adding Customer split information to the billing schedule header, if there are unbilled billing schedule lines on the billing schedule you will be asked to roll
down the changes. **“Do you want to roll down the change from the header to the lines? Changes will only update the billing schedule lines that are not billed.”** Select
**Yes** to update the Customer split information on the billing schedule line. Changes will not be updated if the billing schedule line has already been billed. 

If a billing schedule is created using the Copy schedule option, the Customer split header lines will default in, but they cannot be the same as the Customer account.

When the Generate invoice process runs, multiple sales orders (and sales invoices if posting automatically) will be created. These can be viewed in the **View billing
detail page**, Line details, Invoice tab. The word **Multiple** is shown on the billing detail lines to indicate multiple sales orders and sales invoices were created. 

## Customer split on billing schedule lines

The Customer split can be added at each individual billing schedule line if you only want to split certain billing schedule lines. Mark the **Customer split checkbox**
on the line, then select **Customer split** on the billing schedule line menu to update or enter the Customer split information. 

The **Audit** information is updated if the billing schedule has already been billed and then the percentage is changed on the billing schedule line. Any lines billed
after that will use the new percentage. 

> [!NOTE]
  - The customer split option cannot be used with stocked products. 
  - If the Unbilled revenue checkbox is marked, the customer split checkbox cannot be marked. 
  - If using Revenue split only the parent line has the Customer split option, the child line items do not. 

