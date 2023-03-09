---
title: Customer and product price attribute groups
description: This article explains how to configure customer and product price attribute groups for the Pricing management module.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPPricingAttributeGroup, GUPPricingAttributeGroup
ms.topic: how-to
ms.date: 03/24/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Customer and product price attribute groups

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

*Customer price attribute groups* and *product price attribute groups* let you create logic to establish groups of customers and products, respectively. The membership of each group is based on the values of attributes that you assign to each group. These groups can make it easier to set up collections of customers and products that you can later target in your pricing rules.

## Usage examples

The following two usage examples show how you can simplify your [price attribute groups](price-attribute-groups.md) and pricing rules by establishing a customer price attribute group. The more often you need to use a given customer price attribute group in your various price attribute groups and pricing rules, the more useful the customer or product price attribute group will be. 

Product price attribute groups work similarly to customer price attribute groups, but establish groups of products instead of customers.

### Example customer segment

Suppose you often address a customer target segment of American female wholesale and retail customers aged 20-45. You could define this segment using the attribute values shown in the following table.

| Price attribute | Value |
|---|---|
| Gender | Woman |
| Customer group | 30, 10 |
| Customer age range | 20-45 |
| Country/region | USA |

### Example price attribute group without a customer price attribute group

To set up price attribute groups that could address the example segment without using a customer price attribute group, each of your price attribute groups would need to include all four of the mentioned attributes, and each pricing rule designed to address that segment would have to specify all four values, plus any additional values.

### Example of the same price attribute group that does use a customer price attribute group

Now suppose that you want to simplify the price attribute groups and pricing rules that you use to target this segment. Therefore, you create a customer price attribute group with name and attribute values shown in the following table.

<table>
<thead>
  <tr>
    <th>Customer attribute group </th>
    <th>Attribute</th>
    <th>Value</th>
    <th>Rank</th>
    <th></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="4">US-F-20-45-RE&WH</td>
    <td>Gender</td>
    <td>Girls, Women</td>
    <td>4</td>
    <td></td>
  </tr>
  <tr>
    <td>Customer group</td>
    <td>10, 30</td>
    <td>3</td>
    <td></td>
  </tr>
  <tr>
    <td>Customer age range</td>
    <td>20-45</td>
    <td>2</td>
    <td></td>
  </tr>
  <tr>
    <td>Country/region</td>
    <td>USA</td>
    <td>1</td>
    <td></td>
  </tr>
</tbody>
</table>

As a result, each price attribute group can simply include the *Customer Price Attribute Group* attribute, plus whatever other attributes are needed for each individual group. The related pricing rules could simply specify that a price applies when the **Customer Price Attribute Group** = *US-F-20-45-RE&WH*.

## Manage customer and product price attribute groups

To add, edit, or delete a price attribute group, follow these steps.

1. Do one of the following steps, depending on which type of group you want to create:
    - Go to **Pricing management \> Setup \> Price attribute groups \> Customer price attribute groups**.
    - Go to **Pricing management \> Setup \> Price attribute groups \> Product price attribute groups**.
1. Do one of the following steps:
    - To create a new group, select **New** on the Action Pane.
    - To edit an existing group, select it on the list pane and then select **Edit** on the Action Pane.
    - To delete an existing group, select it in the list pane and then select **Delete** on the Action Pane.
1. Review or edit the following settings in the header of your new or selected group.
    - **Price attribute group** – If you're creating a new group, then enter a unique name for the group here. This becomes read-only on save.
    - **Validated** – Indicates whether the group has been validated. Only validated groups are active and available for use in pricing rules. You can't edit this setting directly. When you create a new group or edit a previously validated group, this field is set to *No*. To validate a new or edited group, you must select **Validation** on the Action Pane, which will trigger a validation check and, if the check passes, will move this setting to *Yes*.
1. Make the following settings on the **General** FastTab.
    - **Friendly name** – Enter a descriptive or common name for the group here. For new groups, this will initially match the value you entered for **Price attribute group**, but you're free to change it.
    - **Description** – Enter a short description for the group.
    - **Help text** – Enter help text that will be shown to describe the group on other pages of Supply Chain Management.
    - **Sales order matching scope** – This read-only value tells whether your group will apply to the overall order header values or to individual order line values. If you're creating a customer price attribute group, then this is always *Header*. If you're creating a product price attribute group, then this is always *Line*. For more information about order matching scopes, see [Price attribute groups](price-attribute-groups.md).
1. On the Action Pane, select **Save**.
1. Expand the **Attributes** FastTab to view and edit the attributes that belong to this group. Use the following toolbar buttons to work with the list.
    - **Add** – Select to add one or more attributes to the list. This button opens the **Add price attribute** dialog, which shows attributes that match your selected group type (product or customer) and provides filtering controls to help you find the attributes you're looking for. Mark the check box for each attribute you want to add and then select **Update** to add those attributes to the group.
    - **Remove** – Remove a selected attribute from the list.
    - **Move up** and **Move down** – Move a selected attribute up or down in rank. <!-- KFM: Does the rank actually matter here?    See the next section for more information about how to use this setting. -->

    [<img src="media/add-customer-price-attribute.png" alt="The Add price attribute dialog." title="The Add price attribute dialog" width="720" />](media/add-customer-price-attribute.png)

1. For each row on the **Attributes** FastTab, enter or select one or more values in the **Value** column. All customers or products that match the attribute values established here will become a member of the current group. The following rules apply.
    - All rows are combined using a logical AND operator, which means that only those companies or products that have matching values for *all* rows will be included in the group.
    - If you want to create one or more rows that include multiple values, set **Enable multiple selections** to *Yes*. This will allow you to add a comma-separated list of values in the **Values** column for each row. The values are combined using an OR operator, which means that the row will find products or customers that have *any* of the values in the list.
    - You can specify values to exclude by adding an "!" before the value. For example, to find all companies located outside of the USA, you could set the attribute with **Name** *Country/region* to have **Value** *!USA*. You can add the exclusion prefix to the values of any row automatically by selecting it and then selecting **Exclude values in selected lines** from the FastTab toolbar.

1. As you are setting up your attributes and values on the **Attributes** FastTab, the **Preview matching results** FastTab updates to show the resulting group members. This can help you verify that your settings are giving you the result you expect. <!-- KFM: What does the **Exclude/Include** Toolbar button do here? -->

1. When you're done adding and arranging attributes, select **Validation** on the Action Pane to trigger a validation check. If the check passes, then the system will set **Validated** to *Yes*, which means the price attribute group is now activated and can be used in pricing rules.

<!-- KFM: What affect do the ranks have for these types of groups? I suspect none? 

## Price attribute ranks

-->

## Use customer and product price attribute groups in price attribute groups

To use a customer or product price attribute groups in a price attribute group, add the customer or product attribute group as an attribute. You add these attribute just as you add other types of attributes. 

*Customer* price attribute groups can only be used in price attribute groups with a **Sales order matching scope** of *Header*, while *product* price attribute groups can only be used with attribute groups wih a **Sales order matching scope** of *Line*.

You can use the **Price attribute source** filter on the **Add price attribute** dialog to find the value quickly, as summarized in the following table.

| Price attribute group scope | Attribute name | Source | Table |
|---|---|---|---|
| Header | Customer Price Attribute Group | CustomerPriceAttributeGroup | Customer Price Attribute Group |
| Line | Product Price Attribute Group | ProductPriceAttributeGroup | Product Price Attribute Group |

For more information about how to set up price attribute groups, see [Construct price attribute groups](price-attribute-groups.md).

[<img src="media/add-ProductPriceAttributeGroup.png" alt="Add a customer groups to a price attribute group." title="Add a customer groups to a price attribute group" width="720" />](media/add-ProductPriceAttributeGroup.png)