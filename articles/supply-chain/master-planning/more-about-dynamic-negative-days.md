---
# required metadata

title: More about (dynamic) negative days
description: 
author: 
manager: 
ms.date: 5/31/2019
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 

# optional metadata

ms.search.form: ReqDemPlanForecastViewer
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 72704
ms.assetid: e7c5d44e-07bc-40b1-a4b3-8ba46483ef9e
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: 
ms.search.validFrom: 
ms.dyn365.ops.version: AX 7.0.0

---

# More about (dynamic) negative days

*Negative days time fence* represents the number of days you are willing to wait with negative inventory before ordering new replenishment. But how do the negative days really work?

In this post:  
- I will be explaining how planned orders get created, taking into account the negative days time fence.
- I will touch upon the correlation between the negative days time fence and the item’s lead time.
- I will also explain the Dynamic negative days time fence calculation and how that factors in the item's lead time into the calculation of the time fence.
- I will also try to better explain the [MRP runtime improvement suggestions](http://blogs.msdn.com/b/axmfg/archive/2015/01/02/checklist-for-improving-mrp-performance-part-2-how-to-setup-planning-parameters.aspx) related to negative days.
- I will explain the above in the context of three different situations. The difference between these situations is at what point within the item’s lead time you get demand.

Please excuse the poor quality of the screenshots. Click on them to get a better view.

## Situation 1

- Item `_DemoProduct` has a 6 days purchase lead time  
- On day 0 (1st Jan) the inventory level for item `_DemoProduct` is 0  
- On day 0 (1st Jan) you get a sales order for item `_DemoProduct`, quantity 10  
- On day 7 (8th Jan) there is an existing purchase order for item `_DemoProduct`, quantity 10  

![What follows is a graph of the situation described](./media/negative-days-1.jpg)

### Case A
Negative days are set to 2, a value not really close to the 6 days lead time of `_DemoProduct`. We don’t use Dynamic negative days.

In this case, MRP will look for receipts for item `_DemoProduct` within the negative days time fence, and since it won’t find any, it will create a new planned purchase order. This planned order will immediately be delayed with 6 days (the lead time) so it will arrive on 7th Jan. The existing purchase order will get a **Cancel** action message, since it is now made redundant by the creation of the new planned purchase order.

![What follows is an overview of the case described](./media/negative-days-2.png)

![What follows is a graph of the case described](./media/negative-days-3.png)

So far so good, but if you take into account MRP performance and plan nervousness it may be not so good. Why? From a performance standpoint, MRP had to create a new planned order, calculate delays and actions, which are all time consuming tasks. From a plan nervousness perspective, you just got 2 more transactions to deal with...

What you gained? The sales order will not be delayed with 7 days, but with 6 days.

### Case B

If this gain is not that important for you, then what you could do is set the negative days to be greater than the item’s lead time. There is no way you can get the supply inside the lead time anyway, so then why not search for receipts as long as it makes sense? On the bright side, it will make MRP run faster, but beware of orders being further delayed!

### Case C

Another thing you could do is use Dynamic negative days (**Master planning > Setup > Master planning parameters > General > Coverage > Use dynamic negative days**). This setting will automatically correlate the item’s lead time to the negative days time fence. What will happen in this case is that MRP will look for receipts inside the dynamic negative days time fence, which is calculated based on the following formula:

> *DynamicNegativeDaysTimeFence = PurchaseLeadTime + NegativeDaysTimeFence + (TodaysDate – RequirementDate)*

If the default order type of `_DemoProduct` would have been Production or Transfer, then the lead time would be the Inventory lead time.

With Dynamic negative days, the time fence MRP looks for receipts is now 6 + 2 + 0 = 8. So MRP will find the existing purchase order and will peg the sales order against it. No new planned orders will be created, hence MRP runtime will be shorter. The Net requirements for `_DemoProduct` look as follows:

![What follows is a screenshot of the requirements](./media/negative-days-4.png)

Schematically, this is what happened:

![What follows is a graph of the case described](./media/negative-days-5.png)

### Case D

So what happens if you set negative days to 0 and use Dynamic negative days only? Would that help you deliver on time and not create impossible planned orders? This actually works just like not using Dynamic negative days, as in the example below.

If you set Negative days to 0 and use only the Dynamic negative days time fence, which will now be 6 + 0 + 0 = 6, you will end up in the same situation as in case A: from a performance standpoint, MRP had to create a new planned order, calculate delays and actions, which are all time consuming tasks. From a plan nervousness perspective, you just got 2 more transactions to deal with… The demand still can’t be fulfilled on time, it will be late anyway.

![What follows is a screenshot of the case described](./media/negative-days-6.png)

![What follows is a graph of the case described](./media/negative-days-7.png)

### Case E

If you both set the negative days to be greater than the item’s lead time and you use the Dynamic negative days time fence as well, than this will be 6 + 6 + 0 = 12. This may lead to a very long time fence MRP will search for results in. At the end of this post, there is a section related to what happens if you set Negative days to a long time fence, so please refer to that in order to understand Case E.

## Situation 2

- Item `_DemoProduct` has a 6 days purchase lead time  
- On day 0 (1st Jan) the inventory level for item `_DemoProduct` is 0  
- On day 4 (5st Jan), inside the item’s lead time, you get a sales order for item _DemoProduct, quantity 10  
- On day 7 (8th Jan) there is a purchase order for item `_DemoProduct`, quantity 10  

![What follows is a graph of the situation described](./media/negative-days-8.png)

### Case A

Negative days are set to 2 and don’t use Dynamic negative days.

In this case, MRP will look for receipts for item `_DemoProduct` within the negative days time fence, and since it won’t find any, it will create a new planned purchase order, order date current date. This planned order will immediately be delayed with 6 days (the lead time) so it will arrive on 7th Jan. The existing purchase order will get a **Cancel** action message, since it is now made redundant by the creation of the new planned purchase order, with delivery date 7th Jan.

![What follows is a screenshot of the case described](./media/negative-days-9.png)

![What follows is a graph of the case described](./media/negative-days-10.png)

### Case B

This is similar to situation 1: if you set the negative days to greater than the item’s lead time, then you will not get a new planned order. The sales order will be pegged to the existing purchase order.

### Case C

This is also similar to situation 1, in the sense that dynamic negative days will work just as well. The dynamic negative days time fence will now be 6 + 2 – 4 = 4. So MRP will find the existing purchase order and will peg the sales order against it. No new planned orders will be created, hence MRP runtime will be better.

![What follows is a screenshot of the case described](./media/negative-days-11.png)

![What follows is a graph of the case described](./media/negative-days-12.png)

### Case D

If you set Negative days to 0 and use only the Dynamic negative days time fence, which will now be 6 + 0 – 4 = 2, you will again end up in the same situation as in Case A. For a graphical view, refer to Situation 2, Case A.

### Case E

If you both set the negative days to be greater than the item’s lead time and you use the Dynamic negative days time fence as well, than this will be 6 + 6 – 4 = 8. This may lead to a very long time fence MRP will search for results in. At the end of this post, there is a section related to what happens if you set Negative days to a long time fence, so please refer to that in order to understand Case E.

## Situation 3

- Item `_DemoProduct` has a 6 days purchase lead time  
- On day 0 (1st Jan) the inventory for item `_DemoProduct` is 0  
- On day 7 (8st Jan), outside the item’s lead time, you get a sales order for item `_DemoProduct`, quantity 10  
- On day 10 (11th Jan) there is a purchase order for item `_DemoProduct`, quantity 10  

![What follows is a graph of the situation described](./media/negative-days-13.png)

### Case A

Negative days are set to 2 and you don’t use Dynamic negative days.  

MRP will look 2 days ahead from the sales order’s requirement date. Since it doesn’t find anything, it will create a planned purchase order on 2nd Jan, that will be shipped just in time to fulfill the sales order demand. The existing purchase order will get cancelling action message, since it’s not needed.

![What follows is a screenshot of the case described](./media/negative-days-14.png)

![What follows is a graph of the case described](./media/negative-days-15.png)

You may notice that in the above AX screenshot, the Purchase order Requirement date is 12th Jan. That is because the screenshot was taken in 2015, when 11th Jan is a Sunday, so MRP moves the Requirement date to 12th Jan, the next working day. But the purchase order has a Delivery date of 11th Jan.

### Case B

This is a case to take a minute and think about. If you set the negative days to be greater than the item’s lead time, then you will not get a new planned order. The sales order will be pegged against the existing purchase order, so in this case the sales order will be delayed, although if you were to create a planned order you could ship the sales order on time!

![What follows is a screenshot of the case described](./media/negative-days-16.png)

![What follows is a graph of the case described](./media/negative-days-17.png)

### Case C

This is also similar to situation 1, in the sense that dynamic negative days will work just as well and even better than if you compare to case B.

The dynamic negative days will be 6 + 2 – 7 = 1, but in this case the system will still consider the negative days lead time (2), because MRP takes into account the maximum value between negative days lead time and dynamic negative days lead time. So the result in case C is the same as in case A.

![What follows is a graph of the case described](./media/negative-days-18.png)

### Case D

If you set Negative days to 0 and use only the Dynamic negative days time fence, which will now be 6 + 0 – 7 = -1, but in this case the system will still consider the negative days lead time (2), hence case A is the same as case D. So all the pitfalls you have in A you will have in D. For a graphical view, refer to Situation 2, Case A.

I will not refer to case E anymore, since it’s exactly the same as in situation 1 and 2 – it has more or less the same benefits and pitfalls.

Based on the above it seems a good idea to set the negative days to be greater than the lead time of the items in the coverage group and/or to always use dynamic negative days and set the negative days to number of days you are willing to wait with negative inventory, before ordering new replenishment (in other words, the number of days you are willing to further delay demand).

The above hopefully also illustrates why items in the same coverage group should have similar lead times.

If you set the negative days to 0 and you don’t use Dynamic negative days, then MRP will always create a new planned order to fulfill demand. So if you setup the system like this, it’s important to work with the Action messages to make sure you don’t pile up inventory.

I have come across blogs and went to conference session where it is recommended to set the negative days to long time fences and then work with the action messages. This will indeed provide good planning results, but will just be a bit slower and potentially more difficult to analyze, due to the need to analyze and apply the action messages.

Let’s look at the following example:

- Item `_DemoProduct` has a 6 days purchase lead time  
- On day 0 (1st Jan) the inventory for item `_DemoProduct` is 0  
- On day 0 (1st Jan) you get a sales order for item `_DemoProduct`, quantity 10  
- On day 10 (10st Jan) you get a sales order for item `_DemoProduct`, quantity 10  
- On day 12 (12th Jan) there is a purchase order for item `_DemoProduct`, quantity 10  
- Negative days are set to 20, which is a lot more than the item’s lead time  

![What follows is a graph of the example given](./media/negative-days-19.png)

MRP will create the following result:

![What follows is a screenshot of the results](./media/negative-days-20.png)

You may notice in the above that the sales order Requirement date is 9th Jan, instead of 10th Jan. That is again because the screenshot was taken in 2015, when 10th Jan is a Saturday, so the Requirement date of the order should be the previous working date, hence Friday, 9th Jan.

MRP creates a planned purchase order to fulfill the demand requested by the first sales order, but then it also recommends you cancel this planned order, because you can advance the existing purchase order and increase the quantity on it.

The results are not wrong by any means. But MRP will potentially run longer, because it will need to create all the delays and suggestions. Also, the planner may need more time to understand the MRP results. And, most importantly, in this case it’s essential that the planner understands and uses the action messages!

Setting the negative days to a lower value, close to the item’s lead time (hence also adhering more to the definition that they represent the number of days you allow negative inventory) and using the Dynamic negative days setting, will give the following result:

![What follows is a screenshot of the results](./media/negative-days-21.png)

MRP will create a planned order pegged to the first sales order. Then the second sales order gets pegged against the existing purchase order, as expected based on the negative days setting. This planning result is also correct and in this case MRP will potentially run a faster. In this case it’s not essential that you understand and know how to work with the action messages.

So all in all, it’s not easy to come up with the right setting for negative days. There are some "do"s and "don’t"s, but finding the right values for your business is a trial and error game, and you have to think in terms of both functionality and MRP runtime.
