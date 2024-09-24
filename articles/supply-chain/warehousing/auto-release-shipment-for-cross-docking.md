---
title: Auto-release shipment for cross-docking 
description: Learn about cross-docking strategies that let you automatically release a demand order to the warehouse when the production order is reported as finished.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 10/15/2019
ms.custom:
ms.reviewer: kamaybac
ms.search.form: WHSCrossDockingTemplate
---

# Auto-release shipment for cross-docking

[!include [banner](../includes/banner.md)]

This article describes a cross-docking strategy that lets you automatically release a demand order to the warehouse when the production order that supplies the demand quantity is reported as finished. In this way, the quantity that is required for fulfillment of the demand order is moved directly from the production output location to the outbound location.

Cross-docking is a warehouse handling flow where the quantity that is required to fulfill an outbound order is directed to the order's outbound dock or staging area from the location where the inbound order was received. (The inbound order can be a purchase order, a transfer order, or a production order.) Whereas the Advanced cross-docking feature supports all supply and demand orders, and it requires that the outbound demand be released before the cross-dock opportunity is identified, the Auto-release shipment feature has these characteristics:

- It supports only production orders as supply, and only sales orders and transfer orders as demand.
- The cross-docking operation can be started even if the demand order wasn't released to the warehouse before the supply receipt was registered (that is, before the production was reported as finished).

This cross-docking functionality has two advantages:

- The warehouse operations can skip the step of putting away quantities of finished goods to the regular warehouse storage area if those quantities will just be picked up again to fulfill the outbound order. Instead, the quantities can be moved one time, from the output location to a packing/shipping location. In this way, the functionality helps minimize the number of times that stock is handled and, ultimately, helps maximize time and space savings on the warehouse shop floor.
- The warehouse operations can postpone the release of sales orders and transfer orders to the warehouse until the output of finished goods for the associated production order is reported as finished. This advantage might be especially relevant in make-to-order production environments, where manufacturing lead times tend to be longer than the lead times in make-to-stock environments.

## Prerequisites

| Prerequisite | Description |
|---|---|
| Item | The item must be enabled for warehouse management processes (WMS).<p>**Note:** Catch-weight-enabled items can't be included in the cross-docking processes.</p> |
| Warehouse | The warehouse must be enabled for warehouse management processes (WMS). |
| Cross-docking templates | At least one cross-docking template that uses the **At supply receipt** demand release policy must be set up for a given warehouse. |
| Work class | A cross-docking work class ID must be created for the **Cross docking** work order type. |
| Work templates | Work templates of the **Cross docking** work order type are required to create cross-docking pick and put work. |
| Location directives | Location directives of the **Cross docking** work order type are required to guide put work in the locations where sales order quantities will be packed and shipped. |
| Marking between a demand order and a production order | The warehouse system can trigger automatic release of the outbound order shipment and create cross-docking work from the output location at the report-as-finished action only if sales orders and transfer orders are reserved and marked against a production order. |

## Example cross-docking flow

A typical cross-docking flow consists of the following main steps.

1. A sales order taker creates a sales order for a make-to-order product. Typically, the requested quantity isn't on hand and must first be produced.
2. The sales order taker creates a production order directly from the sales order line. In this way, the sales order taker reserves and marks the sales order quantity against the production order quantity. 

    Alternatively, a production planner specifies that the marking must be updated when planned orders are being firmed.

3. The production order goes through the following steps:

    1. A production planner estimates and releases the production order. (Estimation includes raw material reservation, and the release includes the release to a warehouse.)
    2. A warehouse worker starts and completes raw material picking from the storage location to the production input location, according to the production pick work.
    3. A shop floor operator starts the production order.
    4. In the last operation, a machine operator uses the mobile device to report the production order as finished.

4. The system uses the setup to identify the cross-docking event for the two linked orders and then completes these tasks:

    1. Automatically release the associated sales order to a warehouse to create a shipment.
    2. Automatically create cross-docking work that has instructions to pick the finished goods from the output location and move them to the outbound location that the cross-docking location directives assigned to the sales order.
    3. Prompt a machine operator to complete the cross-docking work immediately after the production order is reported as finished.

5. After the cross-docking work is completed, and quantities are loaded onto the vehicle, an outbound warehouse planner confirms the sales shipment.

## Example scenario

For this scenario, you must have demo data installed, and you must use the **USMF** demo data company.

### Set up cross-docking that uses the auto-release shipment feature

#### Cross-docking template

1. Go to **Warehouse management** \> **Setup** \> **Work** \> **Cross docking templates**.
2. Select **New**.
3. In the **Sequence number** field, enter **1**.
4. In the **Cross docking template ID** field, enter a name, such as **XDock\_RAF**.
5. In the **Demand release policy** field, select **At supply receipt**.
6. In the **Warehouse** field, enter the number of the warehouse where you want to set up the cross-docking process. For this example, select **51**.

    > [!NOTE]
    > As soon as you select **At supply receipt** as the demand release policy for the template, all other fields on the page become unavailable. Likewise, you can't define any supply sources. This behavior occurs because cross-docking that uses the auto-release shipment feature supports only production orders as supply sources, and it requires that a marking exist between sales orders and production orders. If you select **Before supply receipt** as the demand release policy, the fields on the **Planning** and **Supply sources** tabs are available and can be edited.

#### Work classes

1. Go to **Warehouse management** \> **Setup** \> **Work** \> **Work classes**.
2. Select **New**.
3. In the **Work class ID** field, enter a name, such as **CrossDock**.
4. In the **Work order type** field, select **Cross docking**.

To limit the types of locations where cross-docked finished goods can be put, you can specify one or more valid location types.

#### Work templates

1. Go to **Warehouse management** \> **Setup** \> **Work** \> **Work templates**.
2. In the **Work order type** field, select **Cross docking**.
3. Select **New**.
4. In the **Sequence number** field, enter **1**.
5. In the **Work template** field, enter a name, such as **CrossDock\_51**.
6. Select **Save**.
7. In the **Work Template Details** section, select **New**.
8. For the new line, in the **Work type** field, select **Pick**. In the **Work class ID** field, select **CrossDock**.
9. Select **New**.
10. For the new line, in the **Work type** field, select **Put**. In the **Work class ID** field, select **CrossDock**.

#### Location directives

A standard put-away process for finished goods requires a **Put** location directive to guide the movement of picked production quantities to a regular storage space. Likewise, you must set up a cross-docking **Put** location directive to instruct the work to put the finished quantity in a designated outbound location that services the shipment of the associated sales order.

For cross-docking, as for regular put-away of finished goods, you don't have to create a location directive for the pick work action, because the output location is given. Additionally, this output location is expected to be set up either as the default output location on one of the resource-related records (that is, the resource, resource group relation, or resource group) or as a default production finished goods location for a warehouse.

1. Go to **Warehouse management** \> **Setup** \> **Location directives**.
2. In the **Work order type** field, select **Cross docking**.
3. Select **New**.
4. In the **Sequence number** field, enter **1**.
5. In the **Name** field, enter a name, such as **Baydoor**.
6. In the **Work type** field, select **Put**.
7. In the **Site** field, select **5**.
8. In the **Warehouse** field, select **51**.
9. On the **Lines** FastTab, select **New**.
10. In the **To quantity** field, enter the maximum quantity of the range, such as **1000000**.
11. Select **Save**.
12. On the **Location Directives Actions** FastTab, select **New**.
13. In the **Name** field, enter a name, such as **Baydoor**.
14. Select **Save**.
15. You can use the standard query facility to limit put locations to one or more specific locations. Select **Edit query**, and select **51** as the criterion for the **Warehouse** field in the **Locations** table.

### Cross-dock finished goods to the outbound location

To cross-dock the quantity of finished goods to the outbound location of the associated sales order, follow these steps.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
2. Select **New**.
3. For the sales order header, select customer account **US-001** and a warehouse that is set up for cross-docking that uses the auto-release shipment feature.
4. Add a line for a finished product, and enter **10** as the quantity.
5. In the **Sales order lines** section, select **Product and supply** \> **Production order**.
6. In the **Create production order** dialog box, review the default values, and then select **Create**. A new production order is created and linked to the sales order (that is, it's reserved and marked).
7. Optional: Change the value of the **Quantity** field so that it's more than the value that is required to fulfill the sales order. When the production quantity is reported as finished, the system will create cross-docking work for the marked quantity and put-away work for the remaining quantity, according to the regular procedure for handling the put-away of finished goods.

    As was mentioned earlier, a marking must exist between the sales order and the production order. Otherwise, the cross-docking won't work. A marking can be created in the multiple ways:

    - The system can automatically create the marking in the following situations:

        - The production order is manually created directly from the sales order line (see step 6).
        - Planned production orders are firmed, and the **Update marking** field is set to **Standard**.

    - The user can manually create the marking by opening the **Marking** page from the demand order line.

    > [!NOTE]
    > A marking can't be manually created for items that are set up to use standard and weighted average as inventory models.

8. On the **Production order** page, on the Action Pane, on the **Production order** tab, in the **Process** group, select **Estimate**, and then select **OK**. The order is estimated, and the raw material quantity is reserved for the production.
9. On the Action Pane, on the **Production order** tab, in the **Process** group, select **Release**, and then select **OK**. Warehouse pick work is created for the raw materials.
10. Open and review the work. On the Action Pane, on the **Warehouse** tab, in the **General** group, select **Work details**. Make a note of the work ID.
11. Sign in to the Warehouse Management mobile app to run work in warehouse 51.
12. Go to **Production** \> **Production pick**.
13. Enter the work ID to start and complete the raw material picking. 

    After the work is reported as finished, the quantity of raw materials is available in the production input location (**005** in USMF demo data), and execution of the production order can start.

14. On the **Production order** page, on the Action Pane, on the **Production order** tab, in the **Process** group, select **Start**, and then select **OK**.
15. In the app, go to **Production** \> **RAF and put away**.
16. In the **Prod ID** field, enter the production order number and other mandatory details, and then select **OK**.

Notice that the following events occur:

- The release to a warehouse is triggered for the linked sales order.
- Based on the release, shipment and cross-docking work is created. This work instructs the warehouse operator to pick the quantities that are required to fulfill the sales order line and put them in the outbound location that specified in the cross-docking location directive.
- If the production order quantity is more than the quantity that is required by the sales order, regular put-away work is created. This work instructs the warehouse operator to pick the quantity of finished goods that remains after cross-docking and move it to regular storage, according to the location directive.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]