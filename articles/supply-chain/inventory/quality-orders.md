---
# required metadata

title: Quality orders
description: This article describes how to manually or automatically create quality orders, and how to work with them to perform inspections and record test results in Microsoft Dynamics 365 Supply Chain Management.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventQualityOrderTable
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Quality orders

[!include [banner](../includes/banner.md)]

This article describes how to manually or automatically create quality orders, and how to work with them to perform inspections and record test results in Microsoft Dynamics 365 Supply Chain Management.

## Automatically created quality orders

You can configure the system so that it automatically creates quality orders, based on item sampling rules. For more information, see [Quality management item sampling](quality-item-sampling.md).

## <a name="manual-quality-orders"></a>Manually create quality orders

To manually create a quality order, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Quality management \> Quality orders**.
1. Select **New**.
1. In the **Quality orders** dialog box, in the **Reference type** field, select the inventory reference that your quality order will be related to. For a description of the reference types that are available for selection, see the [Quality order reference types](#ref-types) section later in this article.

    > [!NOTE]
    > Inventory that is related to the selected reference must be available. If no inventory is available for the combination of the reference type, quantity, and inventory dimensions that you select, you will receive an error message.

1. Follow one of these steps, depending on the value that you selected in the **Reference type** field:

    - If you selected **Inventory**, no additional reference information is required.
    - If you selected **Sales** or **Purchase**, specify the following information:

        - **Account selection** – Reference the customer or vendor number.
        - **Reference number** – Reference the sales order or purchase order number.
        - **Reference lot** – Reference the specific sales order line or purchase order line.

    - If you selected **Production**, **Quarantine**, or **Co-product production**, in the **Reference number** field, reference the production order, batch order, or quarantine order number.
    - If you selected **Route operation**, specify the following information:

        - **Reference number** – Reference the production order or batch order number.
        - **Oper. no.** – Reference the specific route operation number.
        - **Operation** – Reference the specific route operation.
        - **Resource** – Reference the specific resource that must be used with the route operation.

1. In the **Test group** field, select the group of tests that must be performed.
1. In the **Quantity** field, enter the quantity of items that must be tested.
1. In the **Inventory dimensions** section, enter any additional inventory dimensions that are required for the selected item.
1. Select **OK**.

After a quality order is created, you can begin to inspect the inventory and record the test results. For more information about how to record and validate test results, see [Inspect the quality of goods](tasks/inspect-quality-goods.md).

## <a name="ref-types"></a>Quality order reference types

Quality orders are used to track the details about inspections and test results for specific inventory in your warehouse. A quality order must include a reference that represents the source of the inventory that is being tested. Quality orders can be related to the following reference types:

- **Inventory** – This reference type indicates that you're inspecting inventory that is on hand. Inspections of this type are typically random or unplanned, and are done when a warehouse worker identifies a problem.
- **Sales** – This reference type indicates that you're inspecting inventory that is related to a specific sales order. Inspections of this type are typically related to customer specifications or the generation of a certificate of analysis (CoA) that must be provided to a customer as part of a shipment. (A CoA is sometimes also referred to as a certificate of compliance \[CoC\].)
- **Purchase** – This reference type indicates that you're inspecting inventory that is related to a purchase order. Inspections of this type are often used to inspect incoming goods before they are put into inventory or consumed in production processes.
- **Production** – This reference type indicates that you're inspecting inventory that is related to a production order. Inspections of this type are often used to inspect finished goods before they are put into inventory.
- **Quarantine** – This reference type indicates that you're inspecting inventory that is related to a quarantine order. Quarantine orders are a special type of order that tracks inventory in a segregated warehouse or a segregated area in your warehouse. Inspections of this type are often used to inspect goods that a customer has returned or that have been put into quarantine for further analysis. Quarantine orders can be generated from quality orders. Alternatively, they can be generated from other sources, and then quality orders can be related to the quarantine orders.
- **Route operation** – This reference type indicates that you're inspecting inventory that is related to a specific step of the route for a production order. Inspections of this type are typically used to analyze the work in process (WIP) of a product before it moves to the next step in the production process.
- **Co-product production** – This reference type indicates that you're inspecting inventory that is related to a co-product of a production order. Inspections of this type are typically used to inspect the co-product of a batch order before the co-product is added to inventory.

## View and create quality orders from various parts of the system

Quality orders can be manually created. Alternatively, they can be automatically created based on the quality associations that you define. For more information about how to create and manage the automatic creation of quality orders, see [Quality associations](quality-associations.md).

You can use the quality order page to manually create a new quality order or view the status of a quality order that is related to another record. There are several ways to access the quality order page.

### From the Quality orders page

To manually create quality orders and view all existing quality orders, go to **Inventory management \> Periodic tasks \> Quality management \> Quality orders**. The remaining sections of this article provide more information about how to work with the **Quality orders** page.

### From sales orders

To work with quality orders that are related to your sales orders, go to **Sales and marketing \> Sales orders \> All sales orders**, and then follow any of these steps:

- Open a sales order, or select it in the grid. Then, on the Action Pane, on the **Pick and pack** tab, in the **Quality management** group, select **Quality orders** to open the **Quality orders** page. There, you can view, create, or update quality orders that are related to the sales order.
- Open a sales order, and then, on the **Header** tab, select the **General** FastTab. The **Quality order status** field shows the overall status of all quality orders that are related to the sales order.
- Open a sales order, and then, on the **Lines** tab, select the **Sales order lines** FastTab. The **Quality order status** column shows the status of each line of the sales order.

### From purchase orders

To work with quality orders that are related to your purchase orders, go to **Procurement and sources \> Purchase orders \> All purchase orders**, and then follow any of these steps:

- Open a purchase order, or select it in the grid. Then, on the Action Pane, on the **Receive** tab, in the **Quality management** group, select **Quality orders** to open the **Quality orders** page. There, you can view, create, or update quality orders that are related to the purchase order.
- Open a purchase order, and then, on the **Header** tab, select the **General** FastTab. The **Quality order status** field shows the overall status of all quality orders that are related to the purchase order.
- Open a purchase order, and then, on the **Lines** tab, select the **Purchase order lines** FastTab. The **Quality order status** column shows the status of each line of the purchase order.

### From production orders

To work with quality orders that are related to your production orders, go to **Production control \> Production orders \> All production orders**, and then follow any of these steps:

- Open a production order, or select it in the grid. Then, on the Action Pane, on the **View** tab, in the **Manage quality** group, select **Quality orders** to open the **Quality orders** page. There, you can view, create, or update quality orders that are related to the production order.
- Open a production order, or select it in the grid. Then, on the Action Pane, on the **Production order** tab, in the **Production details** group, select **Route** to open the **Production route** page. To view the quality orders that are related to a route operation, follow one of these steps:

    - Select the target route operation in the grid. Then, on the Action Pane, select **Inquiries \> Quality orders**.
    - Select the value in the **Oper. No.** field for the target route operation to open its **Production route** details page. On the **General** FastTab, the **Quality order status** field shows the status for the quality orders that are related to the route operation.

- Open a production order, and select the **General** FastTab. The **Quality order status** field shows the status of the quality orders that are related to the production order.

### From quarantine orders

To work with quality orders that are related to your quarantine orders, go to **Inventory management \> Periodic tasks \> Quality management \> Quarantine orders**, and then follow any of these steps:

- Review the values in the **Quality order status** column. In this way, you can learn the overall status of all quality orders that are related to each quarantine order in grid.
- Select a quarantine order in the grid, and then, on the Action Pane, select **Quality orders** to view, create, or update quality orders that are related to the quarantine order.

## Advanced actions for quality orders

You can take several actions on quality orders to manage the status, generate documents, and inquire about additional details.

### Reopen a quality order

By default, you can no longer edit or update a quality order after it has been validated and the tests have been passed. However, in some cases, you might have to reopen a quality order after it has been completed.

To reopen a quality order, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Quality management \> Quality orders**.
1. Open the validated quality order, or select it in the grid.
1. On the Action Pane, select **Reopen quality order**.

### Create a certificate of analysis for a quality order

A CoA is a report that is generated by an organization's quality assurance team. It validates that a product meets specific regulations or requirements. Your customers or regulatory establishments in your geopolitical location might require CoAs. They might also be required based on your industry and the type of products that you handle, purchase, produce, or sell.

Supply Chain Management lets you generate a CoA from a quality order. The report will include the results of any tests on the quality order where the **Certificate of analysis report** option is set to *Yes*. This option can be set by default, based on the test that you define on the **Tests** page. However, you can override the setting on specific tests for a specific quality order.

To generate a CoA for a quality order, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Quality management \> Quality orders**.
1. Select the quality order that you want to create a CoA for.
1. On the Action Pane, select **Inquiries \> Certificate of analysis**.
1. On the **Certificate of analysis** page, on the Action Pane, select **New**.
1. Optional: In the **Contact** field, select the contact person that the certificate should be addressed to.
1. On the Action Pane, select **Print**.
1. In the **Certificate of analysis** dialog box, define how the report should be printed. Then select **OK** to print the report to a printer, to the screen, to a file, or to email.
1. Close the pages.

### Block or unblock inventory for a quality order

When a quality order is automatically generated from a quality association, the item sampling that is assigned to the quality association can be configured to block the full inventory quantity of the reference that is being tested. For more information about item samplings, see [Quality management item sampling](quality-item-sampling.md).

If you aren't using full blocking, or if you're manually creating a quality order, the system automatically creates an inventory blocking record for the quantity of the item that is being tested on the quality order. In the record that is created on the **Inventory blocking** page, the **Inventory blocking type** field is set to *Quality order*.

To view and edit the inventory blocking for a quality order that is selected on the **Inventory blocking** page, select **Inquiries \> Inventory blocking** on the Action Pane. For more information, see [Inventory blocking](inventory-blocking.md).

### Inquire about the details of a quality order

Use the following buttons on the Action Pane of the **Quality orders** page to view more information about or related to a quality order:

- **Inquiries \> Work details** – Open a page where you can view warehouse work that is related to the quality order.
- **Inquiries \> Non conformances** – Open a page where you can view any nonconformances that are related to the quality order.
- **Inventory** – The commands on this menu are common across all inventory transactions. You can use them view or update details such as transactions, on-hand inventory, reservations, and marking.

### Create cases related to quality orders

You can create cases that are related to quality orders. In this way, you can track details about issues and work toward a resolution. You can then use the workflow features of case management to route a case through a predefined business process to obtain additional approvals or get more information about a specific issue. You can also use the knowledge articles feature to create a knowledge base of resolutions for common issues.

## Case management examples for quality management

### Example 1

You work for a manufacturing company that must follow strict regulations that are related to the production of regulated products such as food. Quality orders are used to record and track details about the quality of items throughout the production process. If a quality order fails specific tests, there might be a problem with the equipment. Cases are used to follow a business process and escalate the issue to the correct engineers so that the root cause can be determined. To make business processes easier to follow, the company keeps a knowledge base of common issues that are related to quality orders and equipment issues.

### Example 2

You work for a distribution company that ships products that can be customized for various countries and regions. Some customers have strict specifications that must be followed. Otherwise, fees and returns or chargebacks might be incurred. You use quality orders to track the details about each test and results that match customer requirements. Cases are used to review and approve the details for the CoA before the document is generated and attached together with other shipping paperwork.

## Additional resources

- [Quality management processes](quality-management-processes.md)
- [Quality test](quality-tests.md)
- [Quality test groups](quality-test-groups.md)
- [Quality associations](quality-associations.md)
- [Quality management processes](quality-management-processes.md)
- [Enable quality and nonconformance management](enable-quality-management.md)
- [Quality management for warehouse processes](quality-management-for-warehouses-processes.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
