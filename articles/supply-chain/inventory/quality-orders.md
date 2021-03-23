---
# required metadata

title: Quality orders
description: This topic describes how to manually or automatically create quality orders and how to work with quality orders to perform inspections and record test results in Dynamics 365 Supply Chain Management.
author: perlynne
manager: tfehr
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: InventQualityOrderTable
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
ms.custom: 94003
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Quality orders

[!include [banner](../includes/banner.md)]

This topic describes how to manually or automatically create quality orders and how to work with quality orders to perform inspections and record test results in Dynamics 365 Supply Chain Management.

## Automatically created quality orders

You can configure the system to create quality orders automatically based on item sampling rules. More information: [Quality management item sampling](quality-item-sampling.md)

## <a name="manual-quality-orders"></a>Manually create quality orders

To manually create a quality order:

1. Go to **Inventory management >  Periodic tasks > Quality management > Quality orders**.
1. Select **New** to open the **Quality orders** dialog box.
1. In the **Reference type** field, select the inventory reference that your quality order will be related to (for a description of each type available here, see [Quality order reference types](#ref-types)).

    > [!NOTE]
    > Inventory must be available related to the reference. If no inventory is available for the combination of the reference type, quantity, and inventory dimensions that you select, you will receive an error message.

1. Do one of the following:

    - For **Inventory** type references, no additional reference information is required for this step.
    - For **Sales** and **Purchase** references, specify the following information:
      - **Account selection**: References the customer or vendor number.
      - **Reference number**: References the sales order or purchase order number.
      - **Reference lot**: References the specific sales order line or purchase order line.
    - For **Production**, **Quarantine**, and **Co-product production** type references, specify the **Reference number** that represents the production, batch order, or quarantine order number.
    - For **Route operation** type references, specify the following information:
      - **Reference number**: References the production or batch order number.
      - **Oper. no.**: References the specific route operation number.
      - **Operation**: References the specific route operation.
      - **Resource**: References the specific resource to be used with the route operation.
1. In the **Test group** field, select the group of tests that are to be performed.
1. In the **Quantity** field, enter the quantity of items to be tested.
1. In the **Inventory dimensions** section, enter any additional inventory dimensions that are required for the selected item.
1. Select **OK**.

Once a quality order is created, you can begin to inspect the inventory and record the test results. For more information about recording and validating test results, see [Inspect the quality of goods](tasks/inspect-quality-goods.md).

## <a name="ref-types"></a>Quality order reference types

Quality orders are used to track the details about inspections and test results for specific inventory in your warehouse. A quality order must include a reference, which is the source of the inventory that is being tested. Quality orders can be related to the following reference types:

- **Inventory**: This type indicates that you are inspecting inventory that is on-hand. These types of inspections are typically random or unplanned inspections that are done when a problem is identified by a warehouse worker.
- **Sales**: This type indicates that you are inspecting inventory related to a specific sales order. These types of inspections are typically related to customer specifications or the generation of a certificate of analysis (CoA) to be provided to a customer as part of a shipment.
- **Purchase**: This type indicates that you are inspecting inventory related to a purchase order. These types of inspections are often used to inspect incoming goods before they are put into inventory or consumed in production processes.
- **Production**: This type indicates that you are inspecting inventory related to a production order. These types of inspections are often used to inspect the finished good before it is put into inventory.
- **Quarantine**: This type indicates that you are inspecting inventory related to a quarantine order. Quarantine orders are a special type of order that tracks inventory in a segregated warehouse or area in your warehouse. These types of inspections are often used to inspect goods that have been returned by a customer or that have been put in quarantine for further analysis. Quarantine orders can be generated from quality orders, or from other sources and then quality orders can be related to the quarantine order.
- **Route operation**: This type indicates that you are inspecting inventory that is related to a specific step on the route in a production order. These are typically used to analyze the work in process (WIP) of a product before it moves to the next step in the production process.
- **Co-product production**: This type indicates that you are inspecting the inventory related to a co-product of a production order. These types of inspections are typically used to inspect the co-product of a batch order before the co-product is added to inventory.

## View and create quality orders from various parts of the system

Quality orders can be created manually or automatically based on the quality associations that you define. For more information about how to create and manage the automatic creation of quality orders, see [Quality associations](quality-associations.md). When creating quality orders manually, there are several ways to access the quality order page to create a new order, or see the status of a quality order related to another record.

### From the Quality orders page

To create quality orders manually and see all existing quality orders, go to **Inventory management >  Periodic tasks > Quality management > Quality orders**. See the remainder of this topic for more information about how to work with this page.

### From sales orders

To work with quality orders related to your sales orders, go to **Sales and marketing > Sales orders > All sales orders** and then do any of the following:

- Open a sales order or select it on the grid. On the Action Pane, open the **Pick and pack** tab. Then, in the **Quality management** group, select **Quality orders** to open the **Quality orders** page where you can view, create, or update quality orders that are related to the selected sales order.
- Open a sales order, select the **Header** tab, and expand the **General** FastTab. Here you can view the overall status of all quality orders related to the sales order in the **Quality order status** field.
- Open a sales order, select the **Lines** tab, and inspect the **Sales order lines** FastTab. Here you can view the **Quality order status** for each line of the sales order.

### From purchase orders

To work with quality orders related to your purchase orders, go to **Procurement and sources > Purchase orders > All purchase orders** and then do any of the following:

- Open a purchase order or select it on the grid. On the Action Pane, open the **Receive** tab. Then, in the **Quality management** group, select **Quality orders** to open the **Quality orders** page where you can view, create, or update quality orders that are related to the selected purchase order.
- Open a purchase order, select the **Header** tab, and expand the **General** FastTab. Here you can view the overall status of all quality orders related to the purchase order in the **Quality order status** field.
- Open a purchase order, select the **Lines** tab, and inspect the **Purchase order lines** FastTab. Here you can view the **Quality order status** for each line of the purchase order.

### From production orders

To work with quality orders related to your production orders, go to **Production control > Production orders > All production orders** and then do any of the following:

- Open a production order or select it on the grid. On the Action Pane, open the **View** tab. Then, in the **Manage quality** group, select **Quality orders** to open the **Quality orders** page where you can view, create, or update quality orders that are related to the selected production order.
- Open a production order or select it on the grid. On the Action Pane, open the **Production order** tab. Then, in the **Production details** group, select **Route** to open the **Production rout** page. To view the quality orders related to a route operation, do one of the following:
  - Select the target route operation in the grid. Then, on the Action Pane, select **Inquiries > Quality orders**.
  - Select the value in the **Oper. No.** field for the target rout operation to open its **Production route** details page. Expand the **General** FastTab and check the **Quality order status** field to view the status for the quality orders related to this route operation.
- Open a production order to view its details page. Expand the **General** FastTab and check the **Quality order status** field to view the status for the quality orders related to this production order.
  
### From quarantine orders

To work with quality orders related to your quarantine orders, go to **Inventory management > Periodic tasks > Quality management > Quarantine orders** and then do any of the following:

- Read the values shown in the **Quality order status** column to view the overall status of all quality orders related to each quarantine order listed in grid.
- Select a a quarantine order in the grid and then select **Quality orders** ob the Action Pane to view, create, or update quality orders that are related to the selected quarantine order.

## Advanced actions for quality orders

There are several actions you can take on a quality order to manage the status, generate documents, and inquire on additional details.

### Reopen a quality order

By default, when a quality order is validated and the tests have passed, you can no longer edit or make updates to the quality order. But in some cases, you may need to reopen a quality order after it has been completed.

To reopen a quality order:

1. Go to **Inventory management >  Periodic tasks > Quality management > Quality orders**.
1. Open the validated quality order or select it on the grid
1. On the Action Pane, select **Reopen quality order**.

### Create a certificate of analysis for a quality order

A certificate of analysis (CoA), which is sometimes referred to as a certificate of compliance (CoC), is a document that is generated by an organization's quality assurance team that validates a product meets specific regulations or requirements. These documents may be required by your customers or other regulatory establishments in your geo-political location or based on your industry and the type of products you handle, purchase, produce, or sell.

Dynamics 365 Supply Chain Management allows you to generate a CoA from a quality order. The report will include the results of any tests on the quality order where the **Certificate of analysis report** option is set to *Yes*. This field can be set by default based on the test that you define in the **Tests** page, or you can override the value on specific tests for a specific quality order.

To generate the certificate of analysis for a quality order, do the following:

1. Go to **Inventory management >  Periodic tasks > Quality management > Quality orders**
1. Select the quality order that you want to create a CoA for.
1. On the Action Pane, select **Inquiries > Certificate of analysis**.
1. The **Certificate of analysis** page opens. On the Action Pane, select **New**.
1. Optionally, select a **Contact** that the certificate will be addressed to.
1. On the Action Pane, select **Print**.
1. The **Certificate of analysis** dialog box opens. Use these settings to set up your print and then select **OK** to print to a printer, screen, file, or email.
1. Close the pages.

### Block or unblock inventory for a quality order

When a quality order is generated automatically from a quality association, the item sampling assigned to the quality association can be configured to block the full inventory quantity of the reference that is being tested. For more information about item samplings, see [Quality management item sampling](quality-item-sampling.md).

If you aren't using full blocking, or if you are creating a quality order manually, the system automatically creates an inventory blocking record for the quantity of the item that is being tested on the quality order. This creates a record on the **Inventory blocking** page with the **Inventory blocking type** set to *Quality order*.

To view and edit the inventory blocking for a quality order selected on the **Inventory blocking** page, select **Inquiries > Inventory blocking** in the Action Pane. For more information, see [Inventory blocking](inventory-blocking.md).

### Inquire into details about a quality order

Use the following buttons on the Action Pane of the **Quality orders** page to view more information about or related to a quality order:

- **Inquiries > Work details**: Opens a new page where you can view warehouse work related to the quality order.
- **Inquiries > Non conformances**: Opens a new page where you can view any non conformances that are related to the quality order.
- **Inventory**: This menu provides a list of options that are common across all inventory transactions to view or update details such as **Transactions**, **On-hand**, **Reservations**, and **Marking**.

### Create cases related to quality orders

Create cases related to quality orders to track details about issues and work towards a resolution. You can then use the workflow features of case management to route a case through a pre-defined business process to obtain additional approvals or get more information about a specific issue. You can also use the knowledge articles feature to create a knowledge base of resolutions to common issues.

## Case management examples for quality management

**Example 1**: You work for a manufacturing company that must follow strict regulations related to the production of regulated products such as food. Quality orders are used to record and track details about the quality of the items throughout the production process. When a quality order fails certain tests, it may be an indication of a problem with the equipment and cases are used to follow a business process and escalate the issue to the correct engineers to ensure that the root cause is determined. A knowledge base is kept on common issues related to quality orders and equipment issues to make the process easier to follow.

**Example 2**: You work for a distribution company that ships products that can be customized for various countries and regions. Some customers have strict specifications that must be followed and met, or else fees and returns or chargebacks may be incurred. You use quality orders to track the details of each specific test and results that match the customers requirements. Cases are used to review and approve the details for the CoA before the document is generated and attached with other shipping paperwork.

## Additional resources

- [Quality management processes](quality-management-processes.md)
- [Quality test](quality-tests.md)
- [Quality test groups](quality-test-groups.md)
- [Quality associations](quality-associations.md)
- [Quality management processes](quality-management-processes.md)
- [Enable quality and nonconformance management](enable-quality-management.md)
- [Quality management for warehouse processes](quality-management-for-warehouses-processes.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]