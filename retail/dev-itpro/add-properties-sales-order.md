---
# required metadata

title: Add properties to a sales order
description: By customizing the properties of sales orders, you can send additional data from your online store to meet the requirements of your business processes. This article explains how to add properties to a sales order.
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 44351
ms.assetid: dd9b86cb-630a-4429-9aea-8ba4c4723baa
ms.search.region: Global
# ms.search.industry: 
ms.author: meeram
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Add properties to a sales order

By customizing the properties of sales orders, you can send additional data from your online store to meet the requirements of your business processes. This article explains how to add properties to a sales order.

The starter store has sales order properties that you can use to capture data during order transactions. However, you can extend the sales order properties to send additional data during order transactions. For example, you can add a **GiftWrap** attribute to indicate that an item should be gift-wrapped. To customize sales order properties, you must complete the following tasks:

1.  Create an attribute.
2.  Add the attribute to an attribute group.
3.  Assign the attribute group to your online store.
4.  Set the attribute on a sales order.

## Create an attribute
To create an attribute, you must define an attribute type and then assign the attribute type to your new attribute. In this example, you use a pre-defined attribute type.

1.  In the client, click **Product information management** &gt; **Setup** &gt; **Categories and attributes** &gt; **Attributes**.
2.  Click **New**, and enter the following values.

    | Property       | Value        |
    |----------------|--------------|
    | Name           | GiftWrap     |
    | Friendly name  | Gift wrap    |
    | Attribute type | StringDomain |

## Add the attribute to an attribute group
After you define an attribute, you can add it to an attribute group.

1.  Click **Product information management** &gt; **Setup** &gt; **Categories and attributes** &gt; **Attribute groups**.
2.  Click **New**, and enter the following values.

    | Property      | Value                       |
    |---------------|-----------------------------|
    | Name          | SalesOrderGroup             |
    | Friendly name | Sales order attribute group |
    | Description   | Sales order attribute group |

3.  On the **Attributes** FastTab, click **Add**.
4.  Select **GiftWrap**, and then click **Select**.
5.  Click **OK**.

## Assign the attribute group to your online store
After you create an attribute group, you can assign it to your online store.

1.  Click **Retail and commerce** &gt; **Channels** &gt; **Online stores**.
2.  In the **Online stores** list, double-click your store.
3.  On the **Set up** tab, click **Sales order attributes**.
4.  On the **Channel attribute groups** page, click **New**.
5.  In the **Name** field, select **SalesOrderGroup**.

## Set the attribute on a sales order
You can add the attribute to a sales order by adding business logic in the commerce runtime. Add the following code to add the attribute to the cart, save the cart, and then create a sales order from the cart.

    var cart = orderManager.GetCart(cartId, accountNumber, false);
    cart.AttributeValues.Add(new AttributeTextValue { Name = "GiftWrap", TextValue = "Yes" });
    orderManager.SaveCart(cart);
    orderManager.CreateOrderFromCart(...);

## Next steps
After you create a sales order in the commerce runtime, you can view the new attribute.

### View the attribute

1.  In the client, click **Retail and commerce** &gt; **Retail IT** &gt; **Distribution schedule**.
2.  Run the **P-0001\_OC** job to run POS transactions in the online channel.
3.  Click **Retail and commerce** &gt; **Retail IT** &gt; **Synchronize orders** to create a sales order.
4.  Click **Retail and commerce** &gt; **Inquiries and reports** &gt; **Sales orders** &gt; **All sales orders**.
5.  On the **Retail** tab, and click **Retail attributes**. You should see the attribute that you created.


