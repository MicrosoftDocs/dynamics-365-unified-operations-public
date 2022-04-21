---
# required metadata

title: Periodic tasks in Recurring contract billing
description: This topic describes the periodic tasks in Recurring contract billing
author: JodiChristiansen
ms.date: 11/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---
# Periodic tasks

This topic describes the periodic tasks available in Recurring contract billing. 

## Generate invoice

Use this page to create mass monthly recurring invoices with the information that you set up on the All billing schedules and the View billing detail pages. When an invoice is created, the sales order processing line item description is updated with the item description as well as the billng start date and end dates for the schedule line that is invoiced.

## Generate invoice batch processing

## Price update

Use this utility to update the prices of several items on multiple billing schedules in a single action. The prices can be updated based on a specified percent or a specified amount. The lines list shows the current unit prices of the items only. It does not show the prices after the price update. 

The price update feature can be used for line items as follows: 
- If the sales order for a specific year has already been created, meaning the item has been billed, the price of the items is not affected 
- Items that have a status of **Active** or **On hold** can use the price update utility. For items on hold, the **Adjust schedule** option must have been set to **No** when the hold was placed. 
- The price update feature cannot be used for line items that are usage items or items that use escalation, milestone billing, or revenue splitting. 

### Price update example

A billing schedule is created and a renewal item is added. The unit price is $750.
- The first year of the item is paid on December 15, 2021. 
- The billing schedule is created for the period January 1, 2022 to December 31, 2022. 

At renewal time, Generate invoice creates the sales order for the year 2022. Some time after the price update utility is run and updates the price from $750 to $800. 

The sales order and billing schedule for 2022 are not affected and the unit price remains at $750 because the billing schedule for 2022 has already been billed. The billing schedule line and line detail for 2023 are updated to $800 since it has not been billed yet.

### Updating prices - Flat pricing method

When updating prices for items that use the flat pricing method, you can specify a percent or amount in which to increase the price. 

To run the price update utility for items that use the flat pricing method do the following:
1. Select the **Flat** pricing method. 
2. Select the **Increase method** used to update the price of the items, and specify the **Percent** or **Amount**.
3. In the **Records to include** fastTab, use the **Filter** button to add data filters. 
4. Select **View preview** to see the range of records.
5. If there are lines that you do not want to process, mark them and select **Remove**. 
6. Select **OK**.

### Updating prices - Standard pricing method

If the price of an item has changed on the item record, the item price can be updated for all billing schedule lines if the item uses the standard pricing method.

1. Select the **Standard** pricing method. 
2. In the **Records to include** fastTab, use the **Filter** button to add data filters. 
3. Select **View preview** to see the range of records.
4. If there are lines that you do not want to process, mark them and select **Remove**. 
5. Select **OK**.

## Mass hold processing

Use this page to apply hold options to several billing schedules at the same time. If you want to put only one billing schedule on hold or a single billing schedule line on hold go to the **All billing schedules** page and use **Place hold**. To remove a hold, use the **Remove hold** page. 

### Put billing schedules on hold
To put a bill on several billing schedules do the following:
1. Set **Process option** to **Apply hold**. 
2. Select the **Reason code**. 
3. When **Adjust schedule** is set to **Yes**, specify the **Hold date**. Any billing schedule lines after the hold date are removed. 
4. When **Adjust schedule** is set to **No**, the billing schedule lines are not changed, only the status is changed to **On hold**.
5. In the **Records to include** fastTab, use the **Filter** button to add data filters. 
6. Select **View preview** to see the range of records. 
7. If there are lines that you do not want to process, mark them and select **Remove**. 
8. Select **OK**.

When you return to the list of billing schedules, you can see the status of the billing schedules has changed to **On hold**. 

### Remove a hold from several billing schedules
1. Set the **Process option** to **Remove hold**.
2. Enter a **Reason code**.
3. Select the **Remove date**.
4. If needed, select the **Resumption date** and the **Deferral date**. The deferral date is added to all lines that are deferrable.
5. In the **Records to include** fastTab, use the **Filter** button to add data filters. 
6. Select **View preview** to see the range of records. 
7. If there are lines that you do not want to process, mark them and select **Remove**. 
8. Select **OK**.

**Note:** To remove a hold you must setup the **Remove hold user group override** in **Recurring contract billing parameters**. 

For example, a billing line has a start date of February 1, 2022 and an end date of February 28, 2022 with a billing amount of $200. The **Hold date** is February 10, 2022 which means the February period is adjusted to exclude any date after February 10, inclusive. The new period is February 1, 2022 - February 9, 2022 with an amount of $64.29 (daily proration). All billing schedule lines after and including February 10, 2022 are removed. If the Remove hold process is then done with a **Remove date** of February 10, 2022 there are two billing periods now. The first billing period is Feb 1-Feb 9 for 64.29. The second is Feb 10-Feb 28 for $135.71.
