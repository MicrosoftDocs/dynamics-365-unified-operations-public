---
# required metadata

title: Warehouse location status
description: This topic provides an overview of Warehouse location status.
author: Mirzaab
manager: AnnBe
ms.date: 12/17/2019
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
ms.search.scope: Core, Operations, Supply Chain Management
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2019-12-31
ms.dyn365.ops.version: 10.0.1

---

# Warehouse location status

[!include [banner](../includes/banner.md)]

Dynamics 365 Supply Chain Management includes several locations fields to provide flexibility in working with and maintaining locations. Location statuses can be included in the location directives query for better warehouse flow control.

There are four recently added fields on the **Locations** page to track additional information about the current state of the location. The fields allow warehouse managers to get a better overview of the status of the locations in the warehouse and enable more advanced reporting and filtering.

- Item number: Item that is currently in the location. If the location contains multiple items, this field will be blank.

- Last activity date and time: Timestamp of the last warehouse transaction that was performed against the location.

- Aging date: Date the inventory in the location was brought into the warehouse. This value is calculated based on the license plate aging date. It is accurate for license plate-tracked locations but not guaranteed to be accurate for non-license plate-tracked locations.

- Location status: There are four options for location status.

  - Undetermined: Location profile cannot track status. Current status is unknown.
  - Empty: There is currently no inventory in the location.
  - Picking: Outbound transactions have been performed against the location after it was last empty.
  - Storage: Only inbound transactions have been performed since the location was last empty.


## Set up location profiles

1. Go to **Warehouse management > Setup > Warehouse > Location profiles**.

2. Select "BULK-06". 

3. On the **General** FastTab, in the **Location Updates** group, set the toggles are set to **Yes** for **Enable item in location**, **Enable location activity date and time**, and **Enable location status**. These parameters control whether the references field on the location are active or not. 

4. Select "PIKC-06".

5. Repeat step 3.


## Example scenario

1. Go to **Procurement and Sourcing > Purchase orders > All purchase orders**.

2. Click **New**.

3. In the **Vendor account** field, select "104".

4. In the **Warehouse** field, select "61". 

5. Click **Ok**.

6. Under **Purchase order lines**, click **Add line**.

7. In the **Item number** field, select "A0002".

8. in the **Quantity** field, enter "5".

9. Open the mobile device and go to **Inbound > Purchase Receive**.

10. Enter the PO number and item, followed by the full quantity of the line.

11. On the purchase order, click **Work details** in the **Purchase order lines** group. On the **General** tab, note the work ID that was created.

12. On the mobile device, go to **Inbound > Purchase Put-away** and enter the work ID. 

13. Complete the pick and the put, noting the putaway location.

14. In Supply Chain Management, go to **Warehouse management > Setup > Warehouse > Locations**.

15. Filter on "Location", and enter the putaway location from the purchase order work.

  - The location status column is populated with "Storage" because the last transaction against the location was put. 
  - The item number column is populated with "A0002", the item that was received and put to the location. 
  - The **Last Activity Date** and **Time** column is populated with the timestamp that the work was completed to the location.

16. On the mobile device, go to **Quality > Movement** and enter the putaway location from the purchase order work as the location. 

17. Confirm the full quantity. Enter "06A07R2S1B" as the put location and accept the system-generated license plate.

18. In Supply Chain Management, on the **Locations** page, refresh and view the original putaway location again. Notice that the **Location Status** is now "Empty", and the **Item number** column is blank.

19. View the record for "06A07R2S1B" and notice that the **Status** changed to "Storage" and the **Item number** and **Last Activity Date and Time** fields are updated.

20. Go to **Sales and marketing > Sales orders > All sales orders**. 

21. Click **New**. 

22. In the **Customer account** field, select "US-002".

23. In the **Warehouse** field, select "61".

24. Click **OK**.

25. Under **Sales order lines**, click **Add line**.

26. In the **Item number** field, select "A0002".

27. In the **Quantity** field, enter "1".

28. Reserve the order line and release to warehouse.

29. Click on Warehouse - Work details from the sales order line action bar. Copy the Work ID that was created.

30. On the mobile device, go to **Outbound > Sales picking** and enter the work ID from above.

31. Enter the putaway location created earlier and confirm the pick and put.

32. In Supply Chain Management, go to the **Locations** page. Notice that the **Location Status** for the location the sales order work picked from is updated to "Picking", and the **Last Activity Date and Time** fields are updated.

> [!NOTE]
> The location fields are only updated by warehouse transactions. Moving inventory using a journal, or other non-WHS processes will not update the fields.
