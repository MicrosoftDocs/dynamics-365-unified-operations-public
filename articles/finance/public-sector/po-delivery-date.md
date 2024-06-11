---
title: Calculate the delivery date for a line, based on the lead time
description: Learn how to calculate a delivery date for a line, based on the vendor's lead time and your organization's working days calendar.
author: velofog
ms.author: twheeloc
ms.topic: article
ms.date: 09/03/2019
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2019-09-03
ms.dyn365.ops.version: 10.0.7
---

# Calculate the delivery date for a line, based on the lead time

[!include [banner](../includes/banner.md)]

This article describes how to calculate a delivery date for a line, based on the vendor's lead time and your organization's working days calendar, as they are specified on the **Quotation** tab of the **Request for quotation reply** page. Vendors can specify a lead time for each line. Then, when a purchase order is confirmed, a delivery date for a line is calculated from the confirmation date, based on the lead time and the working days calendar. If no lead time is specified, the confirmation date is used as the delivery date, unless the delivery date is automatically calculated.

The lead time details for a line are available on the following pages: **Request for quotation reply**, **Purchase requisitions**, **Purchase agreements**, and **Purchase order**.

The lead time details aren't overwritten when you calculate delivery dates for all lines on the page by using the **Delivery dates** button on the **Calculate** tab on the Action Pane. You can update the lead time details for unconfirmed or unapproved records. When you confirm a change order, you can recalculate a delivery date.

## Set up a lead time calendar

You must set up the ability to calculate delivery dates, and the calendar that is used in those calculations, on the **Procurement and sourcing parameters** page.

1. Go to **Organization administration \> Setup \> Calendars**, and determine whether any existing calendar indicates the days when your agency is open. If you find an existing calendar that matches your organization's working days (that is, the days when your office is open and can receive shipments), move on to step 2. Otherwise, follow these steps to create a new working days calendar. You might want to create a new calendar if, for example, your office receives shipments from Monday through Thursday, but your organization's working days are from Monday through Friday.

    1. Select **New** to create a new calendar. Alternatively, select **Copy** to create a calendar from an existing, similar calendar that you can quickly update.
    2. In the **Calendar** field, enter an identifier for the calendar.
    3. In the **Name** field, enter a descriptive name.
    4. Select **Working times**.
    5. Select **Compose working times**.
    6. For each calendar day that is a working day, clear the **Closed for pickup** check box.
    7. Select **Save** to save your changes.

    > [!IMPORTANT]
    > We don't recommend that you change an existing calendar that is already used by another part of your organization.

2. Go to **Procurement and sourcing \> Setup \> Procurement and sourcing parameters**.
3. On the **General** tab, set the **Calculate purchase order delivery date based on lead times and working days** option to **Yes**.
4. In the **Select calendar to determine working days** field, select the calendar that indicates the days when your agency is open.
5. Select **Save** to save your changes.

A **Lead time** section now appears on the **Purchase requisitions**, **Purchase order**, and **Purchase agreements** pages.

## Edit the lead time for a line

### Purchase requisition

Lead time details that a vendor enters for a line on the **Request for quotation reply** page appear in the **Lead time** section for a purchase requisition. You can enter or edit the lead time details for a purchase requisition line. The lead time values for the purchase requisition lines are carried over when a purchase order is created.

1. Go to **Procurement and sourcing \> Purchase requisitions \> All purchase requisitions** to open the **All purchase requisitions** list page. (Alternatively, open a different list page.)
2. Select a purchase requisition in the list. Alternatively, select **New**.
3. On the **Purchase requisition lines** FastTab, select a line, and then select **Details**.
4. On the **Purchase requisition line details** page, on the **Details** FastTab, in the **Lead time** section, enter delivery date details.

    - In the **Lead time** field, enter the number of days that are required for lead time.
    - To use only business days, not all calendar days, to calculate the lead time, set the **Working days** option to **Yes**.

7. Select **Save** to save your changes.

### Purchase agreement

Lead time details that are entered for a line on the **Purchase requisition** page appear in the **Lead time** section for a purchase agreement. You can edit an existing unapproved purchase agreement or include the lead time details in a new purchase agreement. The lead time values for the purchase agreement lines are carried over when a purchase order is created.

1. Go to **Procurement and sourcing \> Purchase orders \> Purchase agreements**.
2. On the **Purchase agreements** list page, select a purchase agreement in the list. Alternatively, select **New**.' (as in step 2 of the 'Purchase requisition' procedure' above).
3. On the **Purchase agreement details** page, on the Action Pane, on the **Maintain** tab, select **Edit**.
4. On the **Purchase agreements** FastTab, select the purchase agreement line.
5. On the **Line details** FastTab, on the **General** tab, in the **Lead time** section, update the calculated delivery date.

    - In the **Lead time** field, enter the number of days that are required for lead time.
    - To use only business days, not all calendar days, to calculate the lead time, set the **Working days** option to **Yes**.

8. Select **Save** to save your changes.

### Purchase order

Lead time details that are entered for a line on the **Purchase agreement** and **Purchase requisition** pages appear in the **Lead time** section for a purchase order. You can edit lead time details for an unconfirmed purchase order.

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
2. On the **All purchase orders** list page, select a purchase order in the list. Alternatively, select **New**.' (as in step 2 of the 'Purchase requisition' procedure' above).
2. On the **Purchase order** page, on the Action Pane, on the **Maintain** tab, select **Edit**.
3. On the **Line details** FastTab, on the **Delivery** tab, in the **Lead time** section, in the **Delivery date** field, view the calculated delivery date.
4. In the **Lead time** field, edit the number of days that are required for lead time.
5. To use only business days, not all calendar days, to calculate the delivery date, set the **Working days** option to **Yes**. The delivery date will be updated when the purchase order is approved and confirmed based on the specified lead time.
6. Select **Save** to save your changes.

> [!NOTE]
> For released items, you can select a purchase lead time. The purchase lead time will automatically calculate the delivery date when a purchase order is created. The delivery date won't be recalculated if the lead time on the purchase order line is 0 (zero).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
