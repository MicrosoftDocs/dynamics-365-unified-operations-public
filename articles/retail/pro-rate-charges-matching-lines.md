---
# required metadata

title: Prorate header charges to matching sales lines
description: This topic describes additional capabilities for calculating and applying auto-charges to Retail channel orders using the advanced auto charges features.
author: hhaines
manager: annbe
ms.date: 03/05/2019
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
ms.dyn365.ops.version: 10.0.1


---

# Prorate header charges to matching sales lines

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

The grouping and proration of header auto charges to the Retail sales line feature described in this topic will be available for Point of Sale (POS)-created transactions in Dynamics 365 for Retail version 10.0.1 and available for call center-created sales in version 10.0.2.

This feature is only available if the [advanced auto charges](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/omni-auto-charges) feature is enabled in the **Retail parameters**. The enhanced auto charges calculation method can only be applied to Retail sales orders created through Retail channels (POS, call center, and ecommerce).

With this new functionality, an organization will have more flexibility in how header level auto charges are calculated and applied to retail sales transactions.

In versions earlier than Dynamics 365 for Retail version 10.0.1, auto charges defined at the header level with a specific mode of delivery relation are only calculated when there is a match with the mode of delivery defined on the sales order header. For example, if header level auto charges are defined for mode of delivery "99" and mode of delivery "11", and a sales order is created with mode of delivery "99" on the order header, but also had some sale lines that were configured to ship by mode of delivery "11",  only the header level charges linked to mode of delivery "99" are considered and applied to the sales order. 

In all in-market versions of Retail, the header level charges have an added feature that allows you to define a [tiered charge configuration](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/configure-call-center-delivery) based on the order value. For example, if the order value is between $50.00 and $200.00, the organization may want to charge a freight charge of $5.00, but if the order is between $200.01 and $500.00, the freight charge may be $4.00.  

Some organizations want the benefits of the tiered charges calculation that is provided with the header level charges, but they also want to ensure that in a mixed delivery mode scenario, that the charges calculated are based on a match with the mode of delivery as defined on each sales line.

You can now configure your header level auto charges so that all modes of delivery on the order will be considered in the charges calculation. This functionality requires a more complex calculation logic when calculating the header charges that will group together the items shipping the same mode of delivery and treat those as their calculation group when calculating the header auto charges. Items with like modes of delivery have their auto charges calculated based on their combined sales value to determine the appropriate auto charge tier to be used.   

With this new feature, once the appropriate Header charges are obtained for the sales lines that are shipping the same mode of delivery, the calculated charges will be pro-rated down to the sales line level.  By placing these charges at the line level vs. keeping them at the header level, this allows for a more specific link between the item and the charges value calculated for it.  This can be useful in partial return scenarios when an organization may wish to only refund a portion of the charge instead of the entire charge when only some items are returned.

Below are two sample scenarios to outline how these charges would be calculated with and without this new feature enabled:

Scenario 1:
This scenario outlines the behavior when **Pro-rate to matching sales lines** configuration is **disabled** on the Auto Charge setup (note this is the equivalent to how the Header charges behaved prior to version 10.0.1).

In this scenario, Header level charges have been defined by the organization for Mode of Delivery "99" and Mode of Delivery "11".  Note that no Auto Charges are configured for Mode of Delivery "21".

![Auto Charges for Mode of Delivery 99 with matching line Pro-ration Disabled](media/99_disabled.png)

![Auto Charges for Mode of Delivery 11 with matching line Pro-ration Disabled](media/11_disabled.png)


A sales order is created in Call Center with a Header Mode of Delivery set as "99".  This order contains 5 items; two order lines have been configured to use Mode of Delivery "99", two lines configured for Mode of Delivery "11" and one line configured with Mode of Delivery "21".

![Sales Order Line Example](media/orderlineexample.png)

In this scenario, the entire order is evaluated against the Auto Charges table for Mode of Delivery "99".  The full total of all sales lines is used to determine a matching Tier in the Auto Charges configuration and this charge is applied at the order header level.  In this example, the order total is $165 and the application would apply the $15.00 Freight charge to the order header. Auto Charges configured for Mode of Delivery "11" are never referenced or applied.

In this scenario, if a customer returns some of the items on this order and if the [charge code has been configured to be refunded](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/omni-auto-charges#setup-and-configuration-2), the total Header charge will be systematically applied to the refund, even if only some of the items are being returned.

Scenario 2:
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

In this example, item 81334 will be assigned a Freight charge of $5.62.  These charges can be viewed on the **Maintain Charges** form for the specific sales line.  An example of what this will look like for item 81334 is shown below:

![Pro-rated charges on sales line](media/proratedlinecharge.png)

With this method of calculation in a partial return scenario, if the charge code is refundable, only the portion of the charge allocated to that line will be refunded when the item is returned. 
