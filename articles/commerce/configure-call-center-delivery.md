---
title: Configure call center delivery modes and charges
description: This article describes how to set up modes of delivery and charges for a call center order in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 09/23/2026
ms.update-cycle: 1095-days
ms.topic: article
audience: Application User 
ms.reviewer: mirao
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2018-04-30
ms.search.form: RetailMCRChannelDetailPage, MCROrderParameters
ms.custom: 
  - bap-template
  - evergreen
---

# Configure call center delivery modes and charges

[!INCLUDE [banner](includes/banner.md)]

This article describes how to set up delivery modes and charges for a call center order in Microsoft Dynamics 365 Commerce.

When you place a sales order in Dynamics 365 Commerce, if the person who enters the sales order is linked to a call center channel, the system uses logic and rules to validate the delivery mode and calculate charges for the order.

When you create a sales order, you can select a delivery mode on the sales order header and the sales order lines. By default, the delivery mode that you select on the header is used for all sales order lines. However, you can override the default delivery mode on individual sales lines as needed. You can also define a delivery mode on a customer record. Then, when you create orders for the customer, the system uses that delivery mode by default on the sales order header.

Commerce has capabilities that let you limit the delivery modes that a channel can use, the delivery modes that can be used for a product, and the delivery modes that are valid for specific shipping destinations. You can also define charges so that the system adds extra fees to a customer's order, based on the delivery modes that you select for the sales order and the total order value.

## Define delivery modes

Before you specify which delivery modes can be used for call center orders, and define the associated rules and charges, you must define the delivery modes. Go to **Sales and marketing** > **Setup** > **Distribution** > **Modes of delivery**. Select **New** to create a new delivery mode. Alternatively, select an existing delivery mode in the list, and then select **Edit** to make changes.

In the **Mode of delivery** field, enter any combination of alphanumeric characters, based on your business requirement. Use the **Description** field to provide more information. The **Charges group** and **Expedite** fields are optional.

On the **Commerce channels** FastTab, add any channel that should be allowed to use the delivery mode when you create sales transactions in that channel.

On the **Products** FastTab, specify which products and product categories the delivery mode can and can't be used for. For example, if a product can't be shipped by air because of hazardous material (hazmat) restrictions, ensure that the product or product category is excluded from all delivery modes that involve air transportation.

On the **Addresses** FastTab, specify which countries or regions, or states, the delivery mode can and can't be used for. For example, orders that are shipped to Hawaii or Alaska aren't eligible for ground delivery. Therefore, exclude these states from any delivery mode that is associated with a ground delivery service but include them in any delivery mode that is associated with an air delivery service.

## Validate delivery modes for a call center order

After you define the delivery modes, run the **Process delivery modes** batch job. This job makes the delivery modes available so that sales order processes for channels can use them. To run the **Process delivery modes** job, go to **Retail and Commerce** > **Retail and Commerce IT** > **Process delivery modes**. Run this job any time you add new delivery modes to a channel or make changes to existing delivery mode and channel relationships.

After you run the **Process delivery modes** batch job, go to **Retail and Commerce** > **Channels** > **Call centers** > **All call centers**. On the **All call centers** page, on the **Action** pane, on the **Set up** tab, select **Modes of delivery**. The **Modes of delivery** page lists all the valid delivery modes for the selected call center channel. To edit existing delivery modes or add new delivery modes, select **Manage modes of delivery**. You must run the **Process delivery modes** job whenever you make changes.

> [!NOTE]
> If your changes impact any POS or online stores, run the corresponding CDX jobs along with **Process delivery modes** to reflect the changes in these channels.

## Define charges for delivery services

When you create sales orders for customers, you might want to add charges that the system automatically calculates based on the delivery modes you select for the order. You can configure these charges to be the same for all customers and delivery modes. Alternatively, the charges can vary depending on the customer and the delivery modes you select for the sales order.

To define the charges, go to **Retail and Commerce** > **Channel setup** > **Charges** > **Auto charges**. Select **New** to add new charges. Alternatively, select an existing entry, and then select **Edit**.

You can define charges to calculate at the level of either the order header or the order lines. Use the **Level** field to select the level you want.

You can define charges for a specific customer, a group of customers, or all customers. In the **Account code** field, select **Table** to define charges that apply only to a specific customer. Select **Group** to define charges for a specific customer group. Select **All** to apply the charges to every customer who places a sales order that uses the related delivery mode. If you selected **Table** or **Group** in the **Account code** field, select the customer or customer group in the **Account relation** field.

You can configure charges to apply for a specific delivery mode, a delivery mode group, or all delivery modes. If you select **Table** in the **Mode of delivery code** field, you must select a specific delivery mode in the **Mode of delivery relation** field. If you select **Group**, you must select a delivery mode group in the **Mode of delivery relation** field. Define delivery mode groups at **Retail and Commerce** > **Channel setup** > **Charges** > **Delivery charges group**. You can then link them to one or more delivery modes on the **Modes of delivery** page. If you select a group when you define charges, any delivery mode that is linked to the selected delivery group uses those charges. If you select **All** in the **Mode of delivery code** field, all delivery modes use the charges. Therefore, don't select a value in the **Mode of delivery relation** field.

In the **Lines** section, you can define one or more charges by currency, as you require. You must link charges to a charges code that defines the financial posting rules for the charge. Use the **Category** field to define how charges are calculated. For example, if customers should be charged a flat rate of $9.95 to have an order shipped by a specific delivery mode, use the **Fixed** category. If the business decides to charge customers a percentage of the order total to cover the delivery charges, use the **Percent** category. Define the actual charge to the customers in the **Charges value** field.

Companies often configure tiered charges. In this case, the amount that customers pay for delivery is based on the order value. To configure tiered charges, enter values in the **From amount** and **To amount** fields in addition to defining the charge itself in the **Charges value** field. For example, for orders that have a value that is less than $50, a retailer charges $5.95 for ground shipping. For orders that have a value that is equal to or more than $50, but less than $100, the retailer charges $7.95. Finally, for orders that have a value that is equal to or more than $100, the retailer provides free shipping. The following illustration shows the configuration of these charges.

:::image type="content" source="media/fixedtieredcharges.png" alt-text="Fixed tiered charges example." lightbox="media/fixedtieredcharges.png":::

You can use a mixture of categories for charges, depending on your business requirements. For example, for all orders that have a value that is less than $100, there is a fixed charge of $9.95 for shipping. Then, for orders that have a value that is equal to or more than $100, delivery charges are calculated at a rate of 5 percent of the order value. The following illustration shows the configuration of these charges.

:::image type="content" source="media/mixedtieredcharges.png" alt-text="Mixed tiered charges example." lightbox="media/mixedtieredcharges.png":::

## Apply delivery modes during order entry in a call center

When you create a new sales order, you must specify a value in the **Mode of delivery** field on the **Delivery** FastTab of the sales order header. Default values from the customer record might fill in this field automatically.

The delivery mode that you define on the order header automatically copies to the sales order lines as you create them. However, you can change the delivery mode setup for a specific line item on the **Delivery** tab in the **Line details** section of the sales order entry page.

If the selected delivery mode isn't valid for the product or the delivery address that you define for the order or order line, you receive an error message. You must then select a delivery mode that is defined to support that product or address configuration.

## Calculation of delivery charges during entry of order

If you turn on the **Enable order completion** setting for your call center channel, the system automatically calculates shipping charges for sales orders when users select **Complete**. The following message appears at the top of the **Sales order summary** page: "Tiered charges calculated." The system adds the calculated charges to the value of the **Sales total** field. On the **Amount** FastTab, the **Charges** field shows the total amount of all charges that the system calculates for the order and lines. To see a more detailed breakdown of the charges, select **Order** on the **Sales order summary** page, and then select the **Charges** option to view, add, or edit the charges. The system calculates delivery charges on the order header based on the delivery mode that is linked to the header. The system calculates line-level delivery charges based on the delivery mode that you configure for the sales line. If you use multiple delivery modes on different lines, the system might apply and add together multiple charges. The **Charges** field on the **Sales order summary** page shows the total amount.

If you turn off the **Enable order completion** setting, users must manually trigger the calculation of charges. On the **Sales order** page, on the Action Pane, on the **Sell** tab, in the **Calculate** group, select **Tiered charges**. The "Tiered charges calculated" message appears. You can then select the **Charges** option on the **Sell** tab to view, edit, or delete the calculated charges.

## Use expedited delivery modes on call center orders

You can optionally link an expedite code to any delivery mode that you configure. Use this code as a prioritization sorting and reporting tool. It doesn't currently cause the system to apply extra fees to the order. To set up expedite codes, go to **Sales and marketing** > **Setup** > **Distribution** > **Expedite codes**.

For example, for orders that the system ships by next-day air, you must pick items in the warehouse by 1 PM every day. In this case, you can create an expedite code and link that code to any next-day delivery mode that you configure in the system. When the warehouse creates its pick wave, it can use the appropriate expedite code in the **Expedite** field as a filter, so that the system runs picking only for orders that have delivery modes that are linked to that code.

Additionally, when you enter a call center order, you can manually apply an expedite code to either the sales order header or to an individual sales order line. Again, use the code for sorting or reporting purposes. Sometimes, you must handle an order carefully because of a customer service issue. In this case, applying a specific expedite code to the order header or lines can help identify and prioritize the order during the fulfillment process.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
