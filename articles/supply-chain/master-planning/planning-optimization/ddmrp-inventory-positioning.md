---
title: Inventory positioning
description: Strategic inventory positioning involves identifying points in your supply chain where you can build up inventory on hand, which helps compress lead times and absorb shocks to your supply chain.
author: t-benebo
ms.date: 06/30/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2022-06-30
ms.dyn365.ops.version: 10.0.28
---

# Inventory positioning

[!include [banner](../includes/banner.md)]

## Decoupling points

Strategic inventory positioning involves identifying points in your supply chain where we can build up inventory on hand - we do this for a few reasons, mainly for lead time compression and shock absorption in our supply chain. This lets us mitigate the bullwhip effect by not passing demand variability all the way down the supply chain. There is an example of a multi-level BOM for a pillow product.

![Diagram Description automatically generated](media/image1.png)

Also, the following various considerations we take into account when choosing where our decoupling points are:

- External variability

- Inventory leverage and flexibility

- Critical operation protection

- Customer tolerance time

- Sales order visibility horizon

- Market potential lead time

The first decoupling point can be placed at Foam billets (represented by the yellow inventory icon) for two main reasons – one, that sourcing the materials used to make the billet is difficult and volatile in the current supply chain and because foam billets are then cut into many different shapes and sizes of foam inserts for our products, so this part meets the qualifications for external variability and inventory leverage and flexibility

![Diagram Description automatically generated](media/image2.png)

The next decoupling point is at the Fabric kit, which is our pre-cut pillow fabric. We chose this one because we only have one fabric cutting machine and so we are using the critical operation protection factor in this case.

And finally, we are choosing to set up a decoupling point for the finished good pillow item – firstly, because we have a very low customer tolerance time on sales, secondly because our sales order visibility horizon is fairly short and we want to ensure we have the inventory on hand to meet incoming orders. We are also able to set a higher price when we can keep the lead time this short, which is what the market potential lead time consideration refers to.

## Decoupled lead time

Let's use this same pillow example to understand how decoupling points can help us compress our lead times. Looking at the gray boxes in the top left corner we can see the lead time for each item in our multi-level BOM.

![Teams Description automatically generated](media/image3.png)

In red, we can see the items that drive the cumulative lead time for this item, which is 21 days if we have to start from scratch.

But if we apply the decoupling points for our previous example

![Application  Teams Description automatically generated](media/image4.png)

We see that our new lead time for the pillow would be only 5 days – the three days to produce the pillow and the two days to purchase the thread. This is called a decoupled lead time.

## Strategic inventory positioning in a retail model

Another way we can look at strategic inventory positioning and buffer levels is not just looking at which items in a BOM we should stock, but also which locations in our distribution network. In this example we have a distribution center in Seattle and stores in Boston, Atlanta, and Portland that sell blankets from our company.

![Diagram  timeline Description automatically generated with medium confidence](media/image5.png)

You could decide that the transfer time between the distribution center and the stores is too long for my customer tolerance time since they expect the product to be in stock when they visit. In this case, you would set up a decoupling point for the blanket item at each of the three stores and each one would get a different buffer level based on that particular store's lead times, demand patterns, etc.

## How should we do that in DYNAMICS?

It's a very careful, unexamined decision on how should you place decoupling points and where.

And there's many factors such as Customer tolerance time, External variability and Inventory leverage and flexibility that would influence on and how should you take them into account.

### Customer tolerance time

If you know that for your end item, the highest in this bill of material, the customers willing to wait, let's say 8 days. Please see the Pillow item structure picture from Decoupling lead time parameters.

Then you probably want to took the items as in the picture. Because the whole cumulative time will be longer than 8 days and it is about 25 days.

If you place decoupling points at Foam billet and Fabric kit you will be able to reduce cumulative time up to 5 days and you will be able to meet the expectations of the client.

### External variability

If there's a lot of variability your stock, have some stock to be on the safe side seems to be a good idea because some of your items may have long lead time.

### Same with inventory, leverage and flexibility

Maybe a purchased item you probably want to stock because it's used in many bills of materials across many your items. So that gives you a lot of flexibility.

In case of having some bottlenecks in production, or if you have specific resources that breakdown a lot, or they are very expensive if they go down, you probably want to protect those operations and then make sure that the product you use before that operation you always have it stocked and handy.

Step 1. Set up an Item coverage group

1. Go to **Master planning &gt; Setup &gt; Coverage &gt; Coverage groups**

1. Click **New**

1. Set **Coverage code** = *Decoupling point*

1. Expand the **Other** FastTab

1. Set necessary values to **Lead time factor**, **Variability factor**, **Average daily usage past period (days)**, **Min, max, and re-order point period**.

Once you choose value *Decoupling po*int for the**Coverage code** field, all new fields DDMRP parameters are going to be enabled and then these will be used in DDMRP process.

![Graphical user interface  application Description automatically generated](media/image6.png)

Step 2. Set up Item coverage for item

1. Go to **Product information management &gt; Products &gt; Released products**

1. Select a released item that you want to set up

1. Click the **Plan** tab

1. Click **Item coverage** under **Coverage** button group

1. Click **New** and create a new item coverage record

1. Click the **General** tab

1. Set **Use specific settings** = *Checked*

1. Set **Coverage group** to previously created coverage group for your decoupling point

To define a decoupling point for specific item you have to put this definition on the item coverage level. You need to specify the following fields:

**Coverage code** = Decoupling point. The value of the field determines the principle of replenishment. All records with Decoupling points value are considered by the system as part of the data for DDMRP planning.

**Lead time factor** – The values range from 0 to 1 and the guidance is that the longer the lead time is, the lower the value should be.

**Variability factor** – The values once again range from 0 to 1 and the guidance for this is that products with a higher demand variability should have a higher value for this factor

**Average daily usage past period (days)** – the value means how much do you consume when you order from the moment you order until the order arrives.

**Min, max and reorder-point period** – ???

Besides, you have to specify all the dimensions. If you miss site or warehouse that are mandatory for this item, you will not be able to define the decoupling point for this item.

Among other things you can create many different Item coverage codes if you want many different defaults. There is the easiest way to specify a decoupling point.

> [!NOTE]
> All other items that are not decoupling points should continue to be planned as they are with the classic MRP.
