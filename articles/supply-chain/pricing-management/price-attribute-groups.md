---
title: Price attribute groups
description: This article explains how to configure price attribute groups for the Pricing management module.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 03/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Price attribute groups

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Each *price attribute group* establishes a collection of price attributes. When you define a pricing rule, you can select a price attribute group and then specify values for each of the associated attributes, thereby defining the match criteria used to select the sales orders and order lines that the rule applies to. This article explains how to configure price attribute groups for the Pricing management module.

## <a name="scopes"></a>Price attribute scopes

There are two scopes of price attribute groups, *header* and *line*.

- **Header scope** – These attributes are found in *sales order headers*. They describe the overall sales order, such as the sold-to customer, invoice account, and so on.
- **Line scope** – These attributes are found in *sales order lines*. They describe each individual order line, such as the product ID, quantity, and delivery details.

When you build a pricing rule, you will be able to combine one header and one line price attribute group to set up your condition.

<!-- KFM: Introduce the following table. What are we showing here? -->

<table>
<thead>
<tr>
<th>Attribute group</th>
<th>Source</th>
<th>Source table</th>
<th>Price attributes</th>
</tr>
</thead>
<tbody>
<tr>
<td rowspan="4">Header attribute group</td>
<td rowspan="2">Order (header)</td>
<td>Order table</td>
<td>Provide out-of-box fields from the order header. Can be extended to add more fields.</td>
</tr>
<tr>
<td>Order attributes<br><br>Attributes of the attribute group that are defined as the order attribute group in parameters</td>
<td>Configurable</td>
</tr>
<tr>
<td rowspan="2">Customer</td>
<td>Customer master</td>
<td>Provide out-of-box fields from customer masters. Can be extended to add more fields.</td>
</tr>
<tr>
<td>Attributes of the customer attribute group that are defined as the customer attribute group in parameters</td>
<td>Configurable</td>
</tr>
<tr>
<td rowspan="3">Line attribute group</td>
<td rowspan="2">Product</td>
<td>Product master<br><br>Released product master</td>
<td>Provide out-of-box fields from product master. Can be extended to add more fields.</td>
</tr>
<tr>
<td>Associated product attributes that are defined as price attributes and assigned to a product</td>
<td>Configurable</td>
</tr>
<tr>
<td>Order (line)</td>
<td>Order line</td>
<td>Provide out-of-box fields from the order line. Can be extended to add more fields.</td>
</tr>
</tbody>
</table>

## Manage price attribute groups

To add, edit, or delete a price attribute group, follow these steps.

1. Go to **Pricing management \> Setup \> Price attribute groups \> Price attribute groups**.
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
    - **Sales order matching scope** – If you're creating a new group, then select the [scope](#scopes) (*Header* or *Line*) where this group will apply. This becomes read-only on save.
1. On the Action Pane, select **Save**.
1. Expand the **Attributes** FastTab to view and edit the attributes that belong to this group. Use the following toolbar buttons to work with the list.
    - **Add** – Select to add one or more attributes to the list. This button opens the **Add price attribute** dialog, which shows attributes that match your selected scope and provides filtering controls to help you find the attributes you're looking for. Mark the check box for each attribute you want to add and then select **Update** to add those attributes to the group.
    - **Remove** – Remove a selected attribute from the list.
    - **Move up** and **Move down** – Move a selected attribute up or down in rank. See the next section for more information about how to use this setting.

    [<img src="media/add-price-attribute.png" alt="The Add price attribute dialog." title="The Add price attribute dialog" width="720" />](media/add-price-attribute.png)

    > [!NOTE]
    > You can establish groups of products or customers and then add attribute here that will let you specify those groups by name in your pricing rules. For details about how to create and use these groups, see [Customer and product price attribute groups](customer-product-attribute-groups.md).

1. When you're done adding and arranging attributes, select **Validation** on the Action Pane to trigger a validation check. If the check passes, then the system will set **Validated** to *Yes*, which means the price attribute group is now activated and can be used in pricing rules.

## Price attribute ranks

Each attribute in a price attribute group is assigned a rank. The rank affects which rule will apply when multiple pricing rules match for a given sales order. In this case, only the pricing rule that specifies a value for the highest ranked attribute will apply.

For example, suppose a price attribute group includes the following two attributes:

- **Price attribute 1** – **Name** = *Customer loyalty program*, **Rank** = *10*
- **Price attribute 2** – **Name** = *Segment*, **Rank** = *9*

And suppose the following two pricing rules use this price attribute group:

- **Pricing rule 1** – When **Customer loyalty program** = *Platinum* and **Segment** = *blank* (any segment), then **Price** = *$100*.
- **Pricing rule 2** – When **Customer loyalty program** = *blank* (any loyalty program) and **Segment** = *20*, then **Price** = *$150*.

Assuming no other pricing rules apply, then the price will be $100 because that's the price associated with a specific loyalty program, which is the higher ranking attribute.

[<img src="media/price-attribute-rank.png" alt="Price attribute ranks." title="Price attribute ranks" width="720" />](media/price-attribute-rank.png)
