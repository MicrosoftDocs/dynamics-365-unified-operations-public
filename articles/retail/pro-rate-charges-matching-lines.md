---
# required metadata

title: Pro-rate Header Charges to matching sales lines
description: This topic describes additional capabilities for calculating and applying auto-charges to Retail channel orders using the advanced auto charges features.
author: hhaines
manager: annbe
ms.date: 02/28/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: hhaines
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0


---

# Pro-ration and grouping of Header Auto Charges to Retail sales lines

[!include [banner](includes/preview-banner.md)]
[!include [bannder](includes/banner.md)]

This grouping and pro-ration of Header Auto Charges to Retail Sales Line feature will be available for Point of Sale created transactions in version 10.0.1 and available for Call Center created sales in version 10.0.2.

This feature is only available if the [Advanced Auto Charges](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/omni-auto-charges) feature is enabled in Retail parameters.  This enhanced auto charges calculation method can only be applied to Retail sales orders created through Retail channels (POS, Call Center and Ecommerce).

This feature will allow an organization to have more flexibility in how Header level Auto Charges are calculated and applied to Retail sales transactions.

Prior to version 10.0.1, any Auto Charges defined at the Header level with a specific Mode of Delivery relation would only be calculated when there was a match with the Mode of Delivery defined on the sales order header.  For example, if Header level Auto Charges were defined for both Mode of Delivery "99" and Mode of Delivery "11" in the application, and a Sales Order was created with Mode of Delivery "99" on the order header; but had some sale lines that were configured to ship by Mode of Delivery "11"...with the existing functionality in this scenario, only the Header level charges linked to Mode of Delivery "99" would be considered and applied to this sales order. 

In all in-market versions of our product, the Header level charges have an added feature that allows you to define a [tiered charge configuration](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/configure-call-center-delivery) based on the order value.  For example, if the order value is between $50.00-$200.00, the organization may want to charge a freight charge of $5.00, but if the order is between 200.01-500.00, the freight charge may be $4.00.  

In Retail scenarios, organizations have desired the benefits of the tiered charges calculation that is provided with the Header level charges, but they also want to ensure that in a mixed delivery mode scenario that the charges calculated are based on a match with the Mode of Delivery as defined on each sales line.

This new feature allows for configuring your Header level Auto Charges so that all modes of delivery on the order will be considered in the charges calculation.  This feature adds a more complex calculation logic when calculating the Header charges that will group together the items shipping the same mode of delivery and treat those as their calculation group when calculating the Header Auto Charges.  This allows for the items with like Modes of Delivery to have their Auto Charges calculated based on their combined sales value to determine the appropriate auto-charge tier to be used.   

With this new feature, once the appropriate Header charges are obtained for the sales lines that are shipping the same mode of delivery, the calculated charges will be pro-rated down to the sales line level.  By placing these charges at the line level vs. keeping them at the header level, this allows for a more specific link between the item and the charges value calculated for it.  This can be useful in partial return scenarios when an organization may wish to only refund a portion of the charge instead of the entire charge when only some items are returned.

Below is an example of a scenario and how these charges would be calculated with and without this new feature enabled

When **Pro-rate to matching sales lines** configureation is **disabled** on the Auto Charge setup (note this is the equivalent to how the Header charges behaved prior to version 10.0.1).

In this scenario, Header level charges have been defined by the organization for Mode of Delivery "99" and Mode of Delivery "11".  Note that no Auto Charges are configured for Mode of Delivery "21".

![Auto Charges for Mode of Delivery 99 with matching line Pro-ration Disabled](media/99_disabled.png)

![Auto Charges for Mode of Delivery 11 with matching line Pro-ration Disabled](media/11_disabled.png)


A sales order is created in Call Center with a Header Mode of Delivery set as "99".  This order contains 5 items; two order lines have been configured to use Mode of Delivery "99", two lines configured for Mode of Delivery "11" and one line configured with Mode of Delivery "21".

![Sales Order Line Example](media/orderlineexample.png)

In this scenario, the entire order is evaluated against the Auto Charges table for Mode of Delivery "99".  The full total of all sales lines is used to determine a matching Tier in the Auto Charges configuration and this charge is applied at the order header level.  In this example, the order total is $165 and the application would apply the $15.00 Freight charge to the order header. Auto Charges configured for Mode of Delivery "11" are never referenced or applied.

In this scenario, if a customer returns some of the items on this order and if the [charge code has been configured to be refunded](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/omni-auto-charges#setup-and-configuration-2), the total Header charge will be systematically applied to the refund, even if only some of the items are being returned.

Now let's review this same scenario, but where **Pro-rate to matching sales lines** is enabled (available in 10.0.1 for POS and 10.0.2 for Call Center)

In this scenario, Header level charges are also defined for Mode of Delivery "99" and Mode of Delivery "11", but the **Pro-rate to matching sales lines** flag has also been enabled for these Auto Charge tables.

![Auto Charges for Mode of Delivery 99 with matching line Pro-ration Enabled](media/99_enabled.png)

![Auto Charges for Mode of Delivery 11 with matching line Pro-ration Enabled](media/11_enabled.png)

In this scenario, we have the same sales order with 5 lines.  The Mode of Delivery on the order header is set to "99", but each item on the sales order has delivery modes configured as shown in this example:

![Sales Order Line Example](media/orderlineexample.png)

Due to the configuration of the Auto Charges to **Pro-rate to matching sales lines**, the system will perform the following calculation steps:

In Step 1, the application will group all like delivery mode items together and add up their total product value:

![Step 1 Calculation](media/step1results.png)

In Step 2, the application will locate the Header level Auto Charges configuration that matches the customer/mode of delivery settings for each group of items.  If found, the application will locate the charge to apply in the tiered configuration based on the total product value of items in that delivery mode group:

![Step 2 Calculation](media/step2results.png)

In Step 3, the system will calculate the Charges value to apply to each line based on pro-ration logic that considers the proportional value of the line in relation to the group's total product value.

![Step 3 Calculation](media/step3results.png)

As an example, item 81334 will be assigned a Freight charge of $5.62 per this example.  Users can view this amount by viewing the **Maintain Charges** form for the specific sales line.

![Pro-rated charges on sales line](media/proratedlinecharge.png)

With this method of calculation, in a partial return scenario, if the charge code is refundable, only the portion of the charge allocated to that line will be refunded when the item is returned. 
