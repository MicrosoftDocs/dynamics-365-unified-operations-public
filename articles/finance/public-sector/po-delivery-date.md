
## Calculate delivery date for a line based on the lead time

Calculate a delivery date for a line based on a vendor's lead time (**Request for quotation reply** page, **Quotation** tab) and your organization's working days calendar. Vendors can enter a lead time for each line. When a purchase order is confirmed, a delivery date for a line is calculated from the confirmation date, based on the lead time and the working days calendar. If no lead time is specified, the delivery date is the confirmation date, unless the delivery date is auto calculated. The lead time information for a line is available on the following pages: **Request for quotation reply, Purchase requisitions, Purchase agreements**, and **Purchase order**. The lead time details are not overwritten when delivery dates are calculated for all lines in the form, by using the **Delivery dates** on the **Calculate** tab, on the Action Pane. You can update the lead time details for unconfirmed or unapproved records. You will have the option to recalculate a delivery date when you confirm the change order.

## Setting up lead time calendar

The ability to calculate delivery dates and the calendar to use must be set up in the Procurement and sourcing parameters page 
1. Determine whether a calendar exists that indicates the days your agency is open. If no calendar matches your organization's working days - that is, days your office is open and able to receive shipments - create a new working days calendar. For example, create a new calendar if your office receives shipments M-T even though your working days are M-F. We recommended that you do not change an existing calendar already in use by another part of your organization. 

- Go to **Organization administration > Setup > Calendars**. View calendars to find one that matches your working days. If one exists, continue with step 2. If not, continue with the next bullet.
- Click **New** to create a new calendar, or click **Copy** to create a calendar from an existing, similar calendar that you can quickly update.
- In the **Calendar** and **Name** fields, enter an identifier and a descriptive name for the calendar.
- Click **Working times**.
- Click **Compose working times**.
- For each calendar day, clear the **Closed for pickup** check box to indicate it is a working day.
- Click **Save** to save the changes.

2. Go to **Procurement and sourcing > Setup > Procurement and sourcing parameters**.
3. On the **General** tab, set the **Calculate purchase order delivery date based on lead times and working days** option to **Yes**.
4. In the **Select calendar to determine working days** field, select the calendar to indicate the days your agency is open.
5. Click **Save** to save the changes. 
The **Lead time** group now appears in the **Purchase requisitions** page, **Purchase order** page, and **Purchase agreements** page.


## Purchase requisition: Edit lead time for a line

Lead time details that a vendor has entered for a line in the **Request for quotation** reply page appear in the Lead time group for a purchase requisition. You can enter or edit the lead time details for a purchase requisition line.

1. Go to **Procurement and sourcing > Purchase requisitions > All purchase requisitions** (or other list page), and then select the purchase requisition in the list. Alternatively, click **New** on the Action Pane.
2. Click the **Purchase requisition lines** FastTab, select a line, and then on the Action strip, click **Details**.
3. In the **Purchase requisition line details** page, on the **Details** FastTab, enter delivery date details in the **Lead time** group. 
4. In the **Lead time** field, enter the number of days required for lead time.
5. To limit the lead time calculation to business days rather than all calendar days, set the **Working days** option to **Yes**.
6. Click **Save** to save the changes. The lead time values for the purchase requisition line are carried over when a purchase order is created.

## Purchase agreement: Edit lead time for a line

Lead time details entered for a line in the **Purchase requisition** page appear in the **Lead time** group on a purchase agreement. You can edit an existing unapproved purchase agreement or include the lead time details for a new purchase agreement. The lead time values for the purchase agreement lines are carried over when a purchase order is created.

1. Go to **Procurement and sourcing > Purchase orders > Purchase agreements**.
Select the purchase agreement in the list. Alternatively, click **New**, and include this information when you enter a new purchase agreement.
2. On the **Purchase agreements** list page, select a purchase agreement.
3. In the **Purchase agreement details** page, on the Action Pane, on the **Maintain** tab, click **Edit**.
4. On the **Purchase agreements** FastTab, select the purchase agreement line.
5. On the **Line details** FastTab, on the **General** tab, update the calculated delivery date in the **Lead time** group. 
- In the **Lead time** field, enter the number of days required for lead time.
- To limit the lead time calculation to business days rather than all calendar days, set the **Working days** option to **Yes**.
6. Click **Save** to save the changes.

## Purchase order: Edit lead time for a line

Lead time details entered for a line in the **Purchase agreement** and **Purchase requisition** pages appear in the **Lead time** group for a purchase order. You can edit lead time details for an unconfirmed purchase order. 

1. Go to **Procurement and sourcing > Purchase orders > All purchase orders** list page (or other list page).
Select the purchase order in the list. Alternatively, click **New** and include this information when you create a new purchase order.
2. In the **Purchase order** page, on the Action Pane, on the **Maintain** tab, click **Edit**.
3. On the **Line details** FastTab, on the **Delivery** tab, in the **Lead time** group, view the calculated delivery date (**Delivery date** field). 
4. In the **Lead time** field, edit the number of days required for lead time.
5. To use only business days to calculate the delivery date, set the **Working days** check box to **Yes**. The delivery date will update when the purchase order is approved and confirmed based on the lead time specified.
6. Click **Save** to save the changes.

[Note!] Released items have the option to select a **Purchase lead time**. The **Purchase lead time** will auto calculate the the **Delivery date** when a Purchase order is created.  The **Delivery date** will not be recalculated if the **Lead time** on the purchase order line is zero. 
