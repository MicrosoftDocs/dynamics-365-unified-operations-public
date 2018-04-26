---
# required metadata

title: Configure call center delivery modes and charges
description: This topic describes how to set up modes of delivery and charges for a call center order in Microsoft Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 04/26/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.: RetailMCRChannelDetailPage, MCROrderParameters
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
ms.author: josaw
ms.search.validFrom: 2018-04-30
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Configure call center delivery modes and charges 

[!INCLUDE [banner](includes/banner.md)]

When placing a sales order in Dynamics 365 for Retail, if the user is tied to a call center channel, the sales orders they create will utilize logic and rules for delivery mode validation and charges.

When creating a sales order, a delivery mode can be configured on the sales order header and the sales order lines. The mode of delivery selected on the header will default to all sales lines, although it is possible to override the mode of delivery on any individual sales line as needed.   It is also possible to define a mode of delivery on the customer record, which can be defaulted into the order header when orders are created for that customer.

Dynamics 365 for Retail has capabilities to allow users to limit which delivery modes can be utilized by a channel, which delivery modes can be used for a product, and which delivery modes are valid for certain shipping destinations.  Charges can also be defined to add additional fees to a customer’s order based on the delivery mode(s) selected for a sales order in relation to the total order value.

## Define modes of delivery
Before configuring which modes of delivery can be used for call center orders and the associated rules and charges, the modes of delivery must first be defined. Navigate to **Sales and marketing > Setup > Distribution > Modes of delivery**.  Click the **New** action button to create a new mode of delivery, or select an existing method from the list and click the **Edit** action button to make changes.

You may choose any alphanumeric combination to define the data for the **Mode of delivery** field based on your business needs. The **Description** field can be used to provide additional context. The **Charges** group is optional and will be further defined later in this document. The **Expedite** setting is optional and will be further defined later in this document.

From the **Retail channels** section, add any Retail channel that should be allowed to select and use this delivery mode when creating sales transactions in that channel.

In the **Products** section, you can define which product and/or product categories to include or exclude from being able to use this mode of delivery. For example, if you have a product that cannot ship by Air due to hazmat restrictions, ensure that this product or product category is excluded from all Air transportation methods.  

In the **Addresses** section, you can define which countries/regions or states can be included or excluded from using this delivery method.  For example, orders shipping to Hawaii or Alaska are not eligible for Ground delivery. In this scenario, these states would be excluded from any method of delivery that is associated to a ground delivery service but would be included in any Air delivery services defined.

## Validate modes of delivery for a call center order
Once the modes of delivery have been defined, for them to be available for use in any Retail channel sales order process, the **Process delivery modes** batch job must be executed. Navigate to **Retail > Retail IT > Process delivery modes** to run this job. This job should be executed any time delivery modes are added or changed in relation to Retail channels.

After running the **Process delivery modes** batch job, you may navigate to **Retail > Channels > Call centers > All call centers**.  From the **All call centers** page, in the **Setup** tab, click **Modes of delivery**. This page will list all valid modes of delivery for the selected call center channel. Users can click **Manage modes of delivery** to edit or add additional methods. Note that the **Process delivery modes** job must be executed if changes are made.

## Define charges for delivery service
When sales orders are created for customers in Call center order entry, a company may wish to automatically calculate charges to be added to the sales order based on the mode(s) of delivery selected for the order. These charges can be configured to be the same or different based on the customer and/or the delivery method(s) chosen for the sales order.

To define the charges, navigate to **Retail > Channel setup > Charges > Auto charges**. Use the **New** action to add new charges or **Edit** action to edit an existing entry.  

Charges can be defined to be calculated at the order header or line level. Use the **Level** drop down menu to select the level desired.

Charges can be defined for a specific customer, a group of customers, or all customers. By selecting **Table** in the **Account** code field, you can define charges that will be applied only to a specific customer. The **Group** selection will allow for charges to be defined for a specific customer group and the **All** selection will apply these charges to any customer who places a sales order using the related mode of delivery. The **Account relation** field allows you to pick your customer or customer group if the **Table** or **Group** option was selected.  

Charges can be configured to be applied for all delivery modes, a specific delivery mode, or a delivery mode group. Selecting **Table** in the **Mode of delivery** field will require a specific mode of delivery to be selected in the **Mode of delivery** relation field.   Selecting **Group** allows for the selection of a delivery mode group. A delivery mode group is defined in **Retail > Channel setup > Charges > Delivery charges group** and this group can then be linked to one or more modes of delivery on the **Modes of delivery** page. Selecting a group when defining your delivery charges implies that any delivery mode linked to that delivery group will utilize the charges configured. Finally, using the **All** setting in the **Mode of delivery** field will not require additional setup in the **Mode of delivery relation** field as this implies that all delivery modes will use these charges.

In the **Lines** section of the page, define one or more charges by currency as needed. Charges must be linked to a **Charges code** which defines the financial posting rules for the charge. The **Category** field is used to define how charges are calculated. For example, if a customer is to be charged a flat rate of $9.95 to have an order shipped by a mode of delivery, the category of **Fixed** would be utilized. If the business decides to charge the customer a percentage of the order total to cover the delivery charges, the category of **Percent** can be utilized. The actual charge to the customer is defined in the **Charges value** field.

For retail companies, the configuration of tiered charges that define the amount the customer pays for delivery based on the order value is commonly used. This can be accomplished by entering values in the **From amount** and **To amount** fields in addition to defining the charge itself in the **Charges value** field. For example, a retailer will charge $5.95 for ground shipping on any order up to $50, $7.95 for orders greater than $50 but less than $100 and they will provide free shipping for any order with a value over $100. This can be accomplished by configuring the charges as shown in the image below.

![fixed tiered charges example](media/fixedtieredcharges.png)

You may mix and match the use of the **Category** for the charges depending on business need. For example, if all orders up to $100 will have a fixed charge of $9.95 for shipping and after that any order over $100 will have delivery charges calculated at 5% of order value, this can be accomplished by configuring the charges as shown in the image below.

![mixed tiered charges example](media/mixedtieredcharges.png)

## Apply delivery modes during call center order entry
When a new sales order is created, the **Mode of delivery** field will need to be defined on the sales order header.  This field is found in the **Delivery** fast tab of the sales order header and may auto-populate based on defaults from the customer record.

The **Mode of delivery** defined on the order header will automatically be copied to the sales order lines as they are created.   It is possible to change the mode of delivery setup for a line item under the **Delivery** tab in the **Line** details section of the **Sales order entry** page.

If the mode of delivery selected is not valid for the product or the delivery address defined for the order or order line, the system will error. The user will need to choose a delivery mode that has been defined to support that product or address configuration.

## Calculation of delivery charges during entry of order
If **Enable order completion** is turned on for your call center channel, the shipping charges will be automatically calculated for the sales order when the user clicks the Complete action from the sales order entry screen toolbar. The user will see the message “Tiered charges calculated” at the top of the **Sales order summary** page. The charges calculated are added into the displayed **Sales total** field. The user can open the **Amount** fast tab and view the data in the **Charges** field which displays the total of all charges calculated for the order and lines. To see a more detailed breakout of the charges, the user can click the **Order** dropdown on the **Sales order summary** page and click the **Charges** option to view, add or edit the charges. Note that header delivery charges are calculated based on the delivery mode tied to the order header. Line level delivery charges will be calculated based on the delivery mode configured for the sales line. If multiple modes of delivery have been used on different lines, this could result in multiple charges being applied and added together for a total value displayed in the **Charges** field on the **Sales order summary** page.

If **Enable order completion** is not configured, users must manually trigger the calculation of charges. This is done from the **Sell** tab on the **Sales order** page. Under the **Calculate** section, users must click the **Tiered Charges** option. Once clicked, the “tiered charges calculated” message will display. The user may then click the **Charges** option under the same **Sell** tab to view, edit or delete the calculated charges.

## Use expedited delivery modes on call center orders
When configuring **Modes of delivery** you may optionally link an **Expedite** code to any mode of delivery. This code is used as a prioritization sorting and reporting tool and currently does not trigger additional fees to be applied to the order. Navigate to **Sales and marketing > Setup > Distribution > Expedite codes** to set up these codes.

For example, if the warehouse needs to pick orders that will ship next day air by 1pm daily, an expedite code could be created and that code could be tied to any of the next day modes of delivery configured in the system.  When the warehouse creates their pick wave, the appropriate code in the **Expedite** field could be used as a filter to only run picking for orders that have modes of delivery linked to that expedite code.

The **Expedite** code can also be manually applied during call center order entry to the sales order header or an individual sales order line.   This can again be used for sorting or reporting purposes. If an order needs to be handled with care due to a customer service issue, applying a specific **Expedite** code to the order header or lines can help to facilitate the identification of that order and the prioritization of that order through the fulfillment process.
