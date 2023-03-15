---
title: Sales trade agreement prices
description:
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 03/24/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Sales trade agreement prices

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

*Sales trade agreement prices* are negotiated prices for specific products that apply for specific customers. For sales where a sales trade agreement applies, this price will take priority over the item base price.

Pricing management leverages the standard Supply Chain Management *Trade agreement price - sales price* side and enhanced with the price attributes. <!-- KFM: This sentence is unclear. Please revise. -->

> [!NOTE]
> Pricing management respects [Supply Chain Management sales agreements](../sales-marketing/sales-agreements.md), which are different from the *sales trade agreement prices* described in this article. For order lines where a sales agreement applies, Pricing management will use that price. If no sales agreement applies, then Pricing management will check whether an applicable *sales trade agreement price* exists. The discounts included in sales trade agreements (line discounts, multiple discounts, and total discounts) fall outside the purview of Pricing management. Pricing management provides a new approach to defining discount rules. <!-- KFM: I don't understand the point we are making here. Please revise. -->

## Configure sales trade agreement price control

Several general configuration settings affect the way sales trade agreements work in Pricing management. Follow these steps to set up your system before you start creating any sales trade agreement price rules.

1. Go to the **Pricing management \> Setup \> Pricing management parameters**
1. Open the **Price and discounts** tab.
1. In the **Trade agreements** section, there are 2 options:
    - **Enable default find next** – by enabling this, price engine will check all the applicable trade agreement price and apply the **cheapest** price. If you don't enable this, the pricing determination rule will be 'Price attribute combination rank'. Price engine will apply the highest rank. In case there are multiple price records found with the same rank, price engine will apply the cheapest price.
    - **Apply existing trade agreement (Yes/No)** – If you have the posted sales trade agreement price rule records in the **Sales and Marketing \> Prices and discounts \> Trade agreement journal** with the Default relation as the **Price (sales).** By enabling this, price engine will check those appliable records as well. The logic will be:
        - First apply the sales trade agreement price that meets the criteria.
        - If no applicable record is identified, price engine will check whether there are rules of the Trade agreement journal in the Sales and Marketing module.

1. Enable the sales trade agreement journal name with price attribute. Go to **Pricing management \> Setup \> Trade agreement journal names**. Tick 'Enable price attribute' to allow you to create sales trade agreement journals with the price attributes.
1. Ensure that the Trade agreement price component code is created in the **Pricing management \> Setup \> Price component code.** For sales trade agreement, you are allowed to create only one price component code.

1. Ensure that the Trade agreement price component code is in the price structure in **Price component code setup\\Price trees**.

## Configure price calculation date type

Go to the **Price management \> Setup \> Pricing management parameters \> General** tab to setup the Date type.

Pricing management allows you to use different date type as the criteria to match the price rule record. It has following options:

- Today
- Requested ship date
- Requested receipt date
- Created date

## Create a new sales trade agreement journal

1. Go to **Pricing management \> Sales trade agreement price \> Trade agreement journals.**
1. Select **New**.
1. In the **Name** field, select the drop-down button to open the lookup. Pricing management only allows you to create the journal with Default relation as **Price (sales)**. Selected the journal names with 'Enable price attributes' as Yes.
1. On **Action Pane**, select **Lines**.
1. Select **New** to create a new line.
1. The **Edit price attribute** slider displays for you to enter the attribute value as rule condition.
1. In the **Price attribute group combination** field, select from the price attribute combinations that you have associated with the Price component code of the Sales trade agreement price.
1. In the **Header price attribute group**, select the value condition of the price attributes. If you set 'Enable multiple selections' as Yes, you are allowed to select multiple values for the price attributes.
1. Select **Preview matching results** under the Heade price attribute group section, it will display a preview of the current applicable customers. You can select customers and select **Exclude.** The rule will not apply to the excluded customers.
1. In the **Line price attribute group**, select the value condition of the price attributes. If you set 'Enable multiple selections' as Yes, you are allowed to select multiple values for the price attributes.
1. Select **Preview matching results** under the Line price attribute group section, it will display a preview of the current applicable products. You can select customers and select **Exclude.** The rule will not apply to the excluded products.
1. Select **OK** and the line condition will be populated.
1. In the line, you can further define the **inventory dimensions** (Product\\Storage\\Tracking) to complement the rule condition for the item line.
1. In the **From** field, enter a minimum quantity.
    - If the customer has to order a minimum quantity before they can qualify for the new price, then you need to specify that quantity here.
    - Enter a value in the **To** field to specify the maximum quantity above which the agreement's price will not be valid. If you offer prices based on multiple quantity breaks, then specify each quantity bracket as a pair of minimum and maximum quantity in the **From** and **To** fields respectively.

    For the Sales trade agreement price, the tiered quantity range is per sales order line. This differs from the Discounts where quantity discount tiers are per sales order line.

1. In the **Amount in currency field**, enter a price.
1. In the **Currency** field, enter a currency.
1. In the **Unit** field, enter the price unit.
1. Tick **Allow unit conversion** if you want to use the price conversion when the unit in the sales order line is different from the unit of this sales trade agreement price line.This feature allows you to maintain one record which can apply converted price based on the unit conversion (Sales trade agreement price line unit &lt;&gt; Sales order line unit).
1. Tick **Allow price adjustment** in the line, if your sales trade agreement price is not your final unit price, margin component price adjustments need to be added on top of the price.

    Example:

    Price tree are configured as:

    | Price component code | Price component | Price sequence | Value |
    |---|---|---|---|
    | TAM01 | Sales trade agreement price | 10 | $200 |
    | MAC01 | Price adjustment 01 | 20 | $10 |
    | MAC02 | Price adjustment 02 | 30 | $20 |
    | Allow price adjustment | Yes | Unit price | $230 |
    | | No | | $200 |

1. Under the **Details** section, in the **From date** field, enter a date from which this agreement will be valid. In the **To date** field, enter the date to which this agreement will expire.
1. Select **Save**.
1. Select **Validate**.
1. Select **Validate selected lines**.
1. Select **OK**.
1. Select **Post**.
1. Select **OK**.

## Extract posted journal to a new journal

In case there are minor change of the price rule compared to the previously posted journal. You can copy the old posted sales trade agreement journal with certain criteria and into a new sales trade agreement journal, adjust and post the journal.

Go to new journal line, select **Select**, and you will get a query form you can set different conditions to extract the data from old journals.

Pricing management offers the capability to filter the old trade agreement line based on the attributes.

The '**Match value only**' controls how the system filter the records.

Assuming, the rule has the price attribute as Customer group= A and customer US-001 belongs to customer group A.

- **Match value only**= Yes, when you select customer account= US-001, system will not match the line, as there is no record specify the customer account, though the rule applies to US-001.
- **Match value only**= No, when you select customer account= US-001, system will match the line, as the rule applies to US-001.

Once these details are set, select **Select** to extract old trade agreement lines to a new journal as per the predefined conditions. Once lines are extracted, those can be updated with necessary details and new journal will be validated & posted. 

## View posted sales trade agreement price from product and customer

Pricing management allows you to view the posted sales trade agreement price in the customer and released product master form.

- Customer

In the **Price \> Price setup \> Trade agreements**

Enter the selection criteria and set **Match value only** to No.

Select **Posted** to Yes to filter for the posted trade agreement price.

The price setup price report will display the related Sales trade agreement price that are relevant to this customer.

- Release product

In the **Price \> Price setup \> Trade agreements**

Enter the selection criteria and set **Match value only** to No.

Select **Posted** to Yes to filter for the posted trade agreement price.

The price setup price report will display the related Sales trade agreement price that are relevant to this product.
