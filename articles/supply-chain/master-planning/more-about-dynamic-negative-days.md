---
# required metadata

title: Negative days and dynamic negative days
description: This topic covers how you can better understand negative days and dynamic negative days to help your business.
author: t-benebo
manager: AnnBe
ms.date: 06/06/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
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
ms.search.validFrom: 2019-06-07
ms.dyn365.ops.version: AX 7.0.0

---

# Negative days and dynamic negative days

This topic covers how you can better understand negative days and dynamic negative days to help your business. *Negative days time fence* represents the number of days you are willing to wait with negative inventory before ordering new replenishment.

In this topic, you'll learn:
- How planned orders get created.
- How the negative days time fence and the item's lead time correlate.
- How the dynamic negative days time fence is calculated, and how that factors the item's lead time into the calculation of the time fence.
- How to interpret the [MRP (master planning) runtime improvement suggestions].(http://blogs.msdn.com/b/axmfg/archive/2015/01/02/checklist-for-improving-mrp-performance-part-2-how-to-setup-planning-parameters.aspx) related to negative days

This topic is best understood in three hypothetical scenarios. The difference between these scenarios is at what point within the item's lead time you get demand; before, during, or after the time period.

## Scenario 1- getting demand before the item's lead time period

You might get demand relatively early within your item's lead time, or just before the time period begins. For example, the situation may look like this:

- Item "DemoProduct" has a 6 days purchase lead time.  
- On day zero (January 1st), the inventory level for item "DemoProduct" is zero.
- On day zero (January 1st), you get a sales order for item "DemoProduct", quantity 10.  
- On day seven (January 7th), there is an existing purchase order for item "DemoProduct", quantity 10.  

![What follows is a graph of the situation described](./media/negative-days-1.jpg)

### Case A- negative days are less than the item's lead time

In this case, material requirements planning (MRP) looks for receipts for item "DemoProduct" within the negative days time fence, and since it doesn’t find any, it creates a new planned purchase order. This planned order is immediately delayed with six days (the lead time), so it'll arrive on January 7th. The existing purchase order gets a **Cancel** action message, since it's now made redundant by the creation of the new planned purchase order.

![What follows is an overview of the case described](./media/negative-days-2.png)

![What follows is a graph of the case described](./media/negative-days-3.png)

If you take into account MRP performance and plan nervousness, this case doesn't perform well. MRP has to create a new planned order and calculate delays and actions, which are all time consuming tasks. This case also adds two more transactions onto your plan. On the other hand, the sales order isn't delayed by seven days, but by six days.

### Case B- negative days are greater than the item's lead time

To get better MRP performance, set the negative days to be greater than the item’s lead time. Since you can't get the supply inside the lead time in this situation, you can search for receipts as long as it makes sense. Though MRP will run faster, look out for orders being further delayed.

### Case C- automatically correlate the item's lead time to the negative days time fence

To automatically correlate the item's lead time to the negative days time fence, use **dynamic negative days**, found at **Master planning > Setup > Master planning parameters > General > Coverage > Use dynamic negative days**. In this case, MRP looks for receipts inside the dynamic negative days time fence, which is calculated based on the following formula:

> *DynamicNegativeDaysTimeFence = PurchaseLeadTime + NegativeDaysTimeFence + (Today'sDate – RequirementDate)*

(If the default order type of "DemoProduct" would have been **Production** or **Transfer**, then the lead time would be the **Inventory** lead time.)

With dynamic negative days, the time fence that MRP looks at for receipts is now `6 + 2 + 0 = 8`. MRP finds the existing purchase order and pegs the sales order against it. No new planned orders are created, so MRP runtime is shorter. The net requirements for "DemoProduct" look as follows:

![What follows is a screenshot of the requirements](./media/negative-days-4.png)

Schematically, this is what happened:

![What follows is a graph of the case described](./media/negative-days-5.png)

### Case D- use only dynamic negative days

If you set negative days to zero and use only the dynamic negative days time fence, which is now `6 + 0 + 0 = 6`, you end up in the same situation as in case A. MRP has to create a new planned order and calculate delays and actions, which are time consuming tasks that can be frustrating. In addition, you'll have two more transactions to process. Since the demand can't be fulfilled on time for the item to arrive, this adds more complications to your plan than are necessary.

![What follows is a screenshot of the case described](./media/negative-days-6.png)

![What follows is a graph of the case described](./media/negative-days-7.png)

### Case E- use both greater negative days and the dynamic negative days time fence

If you both set the negative days to be greater than the item’s lead time and use the dynamic negative days time fence as well, then the equation becomes `6 + 6 + 0 = 12`. This might lead to a very long time fence for MRP to search for results in. Look at the section titled "Conclusion" at the end of this topic to see how case E relates to a situation in which you set negative days to a long time fence.

## Scenario 2- getting demand during the item's lead time period

You might get demand sometime during your item's lead time. Here's an example of this situation:

- Item "DemoProduct" has a six days purchase lead tim. 
- On day zero (January 1st), the inventory level for item "DemoProduct" is zero.  
- On day four (January 5th), inside the item’s lead time, you get a sales order for item "DemoProduct", quantity 10.  
- On day seven (January 8th), there is a purchase order for item "DemoProduct", quantity 10.  

![What follows is a graph of the situation described](./media/negative-days-8.png)

### Case A- negative days are less than the item's lead time

In this case, MRP looks for receipts for item "DemoProduct" within the negative days time fence, and since it doesn’t find any, it creates a new planned purchase order using the current date as the order date. This planned order is immediately delayed with six days (the lead time), so it'll arrive on January 7th. The existing purchase order gets a **Cancel** action message, since it's now made redundant by the creation of the new planned purchase order.

![What follows is a screenshot of the case described](./media/negative-days-9.png)

![What follows is a graph of the case described](./media/negative-days-10.png)

### Case B- negative days are greater than the item's lead time

This is similar to Scenario 1. If you set the negative days to a value greater than the item’s lead time, then you won't get a new planned order. The sales order is attached to the existing purchase order.

### Case C- automatically correlate the item's lead time to the negative days time fence

This is also similar to Scenario 1, in the sense that dynamic negative days work just as well. The dynamic negative days time fence is now `6 + 2 – 4 = 4`. If you choose this route, MRP finds the existing purchase order and attaches the sales order to it. Since no new planned orders are created, MRP runtime is better.

![What follows is a screenshot of the case described](./media/negative-days-11.png)

![What follows is a graph of the case described](./media/negative-days-12.png)

### Case D- use only dynamic negative days

If you set negative days to zero and use only the dynamic negative days time fence, which is now `6 + 0 – 4 = 2`, you again end up in the same situation as in case A. For a graphical view, refer to Scenario 2, case A.

### Case E- use both greater negative days and the dynamic negative days time fence

If you both set the negative days to be greater than the item’s lead time and use the dynamic negative days time fence as well, then the equation becomes `6 + 6 – 4 = 8`. This might lead to a very long time fence for MRP to search for results in. Look at the section titled "Conclusion" at the end of this topic to see how case E relates to a scenario in which you set negative days to a long time fence.

## Scenario 3- getting demand after the item's lead time period

You might get demand after the item's lead time. If so, the situation might look like the following example:

- Item "DemoProduct" has a six days purchase lead time.  
- On day zero (January 1st), the inventory for item "DemoProduct" is zero.  
- On day seven (January 8th), outside the item’s lead time, you get a sales order for item "DemoProduct", quantity 10.  
- On day 10 (January 11th), there is a purchase order for item "DemoProduct", quantity 10.  

![What follows is a graph of the situation described](./media/negative-days-13.png)

### Case A- negative days are less than the item's lead time

In this case, MRP looks two days ahead of the sales order’s requirement date. Since it doesn’t find anything, it creates a planned purchase order on January 2nd which will be shipped just in time to fulfill the sales order demand. The existing purchase order gets a **Cancel** action message, since it’s not needed.

![What follows is a screenshot of the case described](./media/negative-days-14.png)

![What follows is a graph of the case described](./media/negative-days-15.png)

In the above screenshot, the purchase order requirement date is January 12th. That is because the screenshot was taken in 2015, when January 11th was a Sunday, so MRP moved the requirement date to January 12th, the next working day. Even so, the purchase order has a delivery date of January 11th.

### Case B- negative days are greater than the item's lead time

If you set the negative days to be greater than the item’s lead time, then you won't get a new planned order. The sales order is pegged against the existing purchase order, so in this case the sales order is delayed. If you were to create a planned order, you could ship the sales order on time.

![What follows is a screenshot of the case described](./media/negative-days-16.png)

![What follows is a graph of the case described](./media/negative-days-17.png)

### Case C- automatically correlate the item's lead time to the negative days time fence

This is similar to Scenario 1, in the sense that dynamic negative days work just as well as, if not better than, case B.

The dynamic negative days are `6 + 2 – 7 = 1`, but in this case the system still considers the negative days lead time (two), because MRP takes into account the maximum value between negative days lead time and dynamic negative days lead time. Therefore, the result in case C is the same as in case A.

![What follows is a graph of the case described](./media/negative-days-18.png)

### Case D- use only dynamic negative days

In this case, if you set negative days to zero and use only the dynamic negative days time fence, which is now `6 + 0 – 7 = -1`, the system still considers the negative days lead time (two), so case A is the same as case D, with all the same pitfalls. For a graphical view, refer to Scenario 2, case A.

### Case E- use both greater negative days and the dynamic negative days time fence

In this situation, case E is exactly the same as in Scenarios 1 and 2. It has more or less the same benefits and drawbacks.

## Conclusion

These three scenarios demonstrate that it's a good idea to set the negative days to be greater than the lead time of the items in the coverage group. It's also a good option to only use dynamic negative days and to set the negative days to the number of days you are willing to wait with negative inventory before ordering new replenishment (in other words, the number of days you are willing to further delay demand). Items in the same coverage group should have similar lead times as well.

If you set the negative days to zero and don’t use dynamic negative days, then MRP always creates a new planned order to fulfill demand. With a system like this, it’s important to work with the action messages to make sure you don’t pile up inventory.

You might want to set the negative days to long time fences and then work with the action messages. This provides good planning results, but it's also a bit slower and potentially more difficult to analyze, due to the need to analyze and apply the action messages. You can see a situation like this in the following example:

- Item "DemoProduct" has a six days purchase lead time.  
- On day zero (January 1st), the inventory for item "DemoProduct" is zero.  
- On day zero (January 1st), you get a sales order for item "DemoProduct", quantity 10.  
- On day 10 (January 10th), you get a sales order for item "DemoProduct", quantity 10.  
- On day 12 (January 12th), there is a purchase order for item "DemoProduct", quantity 10.  
- Negative days are set to 20, which is a lot more than the item’s lead time.  

![What follows is a graph of the example given](./media/negative-days-19.png)

MRP creates the following result:

![What follows is a screenshot of the results](./media/negative-days-20.png)

The sales order requirement date listed above is January 9th instead of January 10th. That is because the screenshot was taken in 2015, when January 10th was a Saturday, so the requirement date of the order should be the previous working date—Friday, January 9th.

MRP creates a planned purchase order to fulfill the demand requested by the first sales order, but then it also recommends you cancel this planned order, because you can advance the existing purchase order and increase the quantity on it.

The results are not wrong, but MRP will potentially run longer, because it needs to create all the delays and suggestions. Also, the planner might need more time to understand the MRP results. Most importantly, in this case, it’s essential that the planner understands and uses the action messages.

Lowering the negative days to a value that's closer to the item's lead time and using the dynamic negative days setting gives the following result:

![What follows is a screenshot of the results](./media/negative-days-21.png)

MRP creates a planned order attached to the first sales order. Then the second sales order gets pegged against the existing purchase order, as expected, based on the negative days setting. This planning result is also correct, and MRP will potentially run faster. In this case, it’s not essential that you understand and know how to work with the action messages.

To have the right values entered for your business, you must think in terms of both funcionality and MRP runtime. This can take a little trial and error to figure out.

## See also

For more discussion, [see the original blog post](https://blogs.msdn.microsoft.com/axmfg/2015/02/19/more-about-dynamic-negative-days/).
