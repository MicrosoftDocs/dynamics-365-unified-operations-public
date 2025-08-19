---
title: Goods in transit from vendor
description: Learn how to work with the Counting act for goods in transit (INV-6) report for Russia in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/22/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2019-06-28
---

# Goods in transit from vendor (Russia)

[!include [banner](../../includes/banner.md)]

This article explains how to work with the Counting act for goods in transit (INV-6) report for Russia in Microsoft Dynamics 365 Finance.

The item counting process (INV-6) is used to identify the quantity and value of inventory items that are in transit when inventory is counted.

The item counting process is done in the context of nomenclatures, shipping documents, and vendors.

## Set up an inventory profile for a transferable item

To reflect the goods and materials that are in transit, you can set the kind of inventory for the **Basic** kind of activity. The **Kind of inventory** field can have the following values:

- Common
- Purchased items in route

To set up an inventory profile for a transferable item, follow these steps.

1. In Dynamics 365 Finance, go to **Inventory management** \> **Setup** \> **Dimensions** \> **Inventory profiles**.
1. Select **New** to create an inventory profile for an item.
1. In the **Inventory profile** field, enter the name of the inventory profile.
1. In the **Name** field, enter a description of the inventory profile.
1. On the **Setup** FastTab, in the **Kind of activity** field, select **Basic**.
1. Set the **Don't match option** to **Yes** to prevent on-hand inventory that uses this inventory profile from being automatically matched with a compatible inventory profile.
1. In the **Kind of inventory** field, select **Purchased items in route**. The **Initialize dimension** and **Control dimension in purchase order** options are automatically set to **Yes**.

    > [!NOTE]
    > The **Kind of inventory** field is available only if you select **Basic** in the **Kind of activity** field.

1. On the **Matching priority** FastTab, select **Up** or **Down** to change the order of the inventory profile.
1. Select **Save**, and close the page.

  ![Inventory profiles page.](../media/goods-in-transit-vendor-01.png)
 
## Set up a number sequence for the Counting act (INV-6) report

To set up a number sequence for the Counting act (INV-6) report, follow these steps.

1. In Dynamics 365 Finance, go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters**.
1. On the **Number sequences** tab, in the **Number sequence code** field, select a number sequence for the **Counting act (INV-6)** reference.
1. Select **Save**, and close the page.

## Set up an inventory journal name for the Counting act (INV-6) report

To set up an inventory journal name for the Counting act (INV-6) report, follow these steps.

1. In Dynamics 365 Finance, go to **Inventory management** \> **Setup** \> **Journal names** \> **Inventory**.
1. Create a journal name.
1. In the **Name** field, enter the inventory journal name.
1. In the **Description** field, enter a description.
1. In the **Journal type** field, select **Counting**.
1. On the **Reports** FastTab, in the **Available** field, select **Counting act (INV-6)**, and then select the left arrow button to move the report to the **Selected** field.

    > [!NOTE]
    > If the **Available** field is blank, select **Update** on the Action Pane to update the list of available reports.

1. Select **Save**, and close the page.

   ![Inventory journal names page.](../media/goods-in-transit-vendor-2.png)
 
## Add officials to the Counting act (INV-6) report

You can specify the company officials who are involved in the item counting process for the **Counting act (INV-6)** report.

To add officials to the Counting act (INV-6) report, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.
1. On the **Inventory** tab, select the **Counting act (INV-6)** option.
1. Select **New** to create an official for the **Counting act (INV-6)** report.
1. In the **Position** field, select the designation of the official.
1. In the **Name** field, enter the name of the official.
1. In the **Job title** field, select the job title of the official.

    > [!NOTE]
    > By default, the job title is copied from the selected employee's record.
 
    ![Officials page.](../media/goods-in-transit-vendor-03.png)
 
1. Select **Save**, and close the page.

### Create an inventory tracking dimension group for the Counting act (INV-6) report

To create an inventory tracking dimension group for the Counting act (INV-6) report, follow these steps.

1. In Dynamics 365 Finance, go to **Product information management** \> **Setup** \> **Dimension and variant groups** \> **Tracking dimension groups**.
1. Select **New** to create a dimension group.
1. In the **Name** field, enter the name of the dimension group.
1. In the **Description** field, enter a description.
1. On the **Tracking dimensions** FastTab, on the **Inventory profile** line, select the **Active**, **Primary stocking**, **Physical inventory**, **Financial inventory**, **Coverage plan by dimension**, and **Transfer** checkboxes.
1. On the **Owner** line, select the **Active**, **Physical inventory**, **Financial inventory**, and **Transfer** checkboxes.

    > [!NOTE]
    > To make the report reflect the details of shipping and payment documents, on the **Batch number** line, select the **Active** and **Physical inventory** checkboxes.

   ![Tracking dimension groups page.](../media/goods-in-transit-vendor-04.png)
 
1. Select **Save**.

## Create a purchase agreement

To create a purchase agreement, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Purchase orders** \> **Purchase agreements**.
1. Select **New** to open the **Create purchase agreement** dialog.
1. On the **Vendor** FastTab, in the **Vendor account** field, select the vendor account.
1. In the **Purchase agreement classification** field, select **Blanket purchase agreement**.
1. On the **General** FastTab, in the **Document** section, in the **Purchase agreement** field, enter the ID of the purchase agreement.
1. Specify other details, and then select **OK**.
1. On the **Purchase agreements** page, switch to the **Header** view, and then, on the **Financial** FastTab, in the **Inventory profile** section, set the following fields:
    - In the **Kind of activity** field, select **Basic**.
    - In the **Inventory profile** field, select the inventory profile that you created earlier.
 
    ![Purchase agreements page.](../media/goods-in-transit-vendor-05.png)
 
1. On the Action Pane, on the **Purchase agreement** tab, in the **Generate** group, select **Confirmation** to update the status of the purchase agreement to **Effective**.

## Add an inventory owner to the Counting act (INV-6) report

To add an inventory owner to the Counting act (INV-6) report, follow these steps.

1. In Dynamics 365 Finance, go to **Inventory management** \> **Setup** \> **Dimensions** \> **Inventory owners**.
1. Select **New** to add an inventory owner.
1. In the **Owner** field, enter the owner code.
1. In the **Account type** field, select **Vendor**.
1. In the **Account** field, select the principal code. The **Name** field is filled in automatically.
1. In the **Agreement ID** field, select the purchase agreement that you created earlier. In this way, you associate the new owner with the agreement.

    ![Inventory owners page.](../media/goods-in-transit-vendor-06.png)

1. Select **Save**.

## Register goods and materials that are in transit

To register goods and materials that are in transit, follow these steps.

1. Create a new purchase order. In the **Purchase agreement** field, select the purchase agreement that you created earlier, and then, on the purchase order line, in the **Item number** field, select the item number.

    > [!NOTE]
    > The **Tracking dimension** field for the item should be set to the inventory profile that you created earlier.

1. On the **Line details** FastTab, on the **Product** tab, in the **Tracking dimension** section, validate that the **Inventory profile** field is set to the inventory profile that you created earlier.
1. In the **Owner** field, select the record that you created earlier.

    ![Purchase order page page.](../media/goods-in-transit-vendor-07.png)

1. Post the invoice in the usual way.

## Generate a Counting act (INV-6) report

You can use the **Print of counting act (INV-6)** dialog to generate a **Counting act (INV-6)** report as a Microsoft Excel file. You must generate this report to track items that are transferred between warehouses and to create a counting list of the items in the transfer that have been purchased. The counting list can contain on-hand inventory holdings.

To generate a Counting act (INV-6) report, follow these steps.

1. In Dynamics 365 Finance, go to **Inventory management** \> **Journal entries** \> **Item counting** \> **Counting**.
1. Select **New** to open the **Dimensions display** dialog.
1. On the **Overview** FastTab, validate that the **Name** field is set to the inventory journal name that you created earlier.
1. In the **Store inventory** section, set the **Site** and **Warehouse** fields.
1. On the **Counting by** FastTab, validate that the **Inventory profile** and **Owner** options are set to **Yes**.

    > [!NOTE]
    > You can also set the **Batch number** and **Warehouse** options to **Yes**, if those dimensions are applicable.
 
    ![Dimensions display dialog.](../media/goods-in-transit-vendor-08.png)
 
1. Select **OK** to create an inventory counting journal for the items in the transfer.
1. On the **Counting** page, in the **Journal lines** FastTab, create a line, and select the item number that you created earlier.
1. On the **Line details** FastTab, on the **Inventory dimensions** tab, in the **Inventory profile** and **Owner** fields, select the records that you created earlier. The **On-hand** field on the journal line is automatically updated.
1. On the **Journal lines** FastTab, select **Functions** \> **Create counting list** to create a counting list. For each line, the **Counted** field is updated with the value that is specified in the **On-hand** field.

    ![Counting page.](../media/goods-in-transit-vendor-09.png)

10.	On the Action Pane, select **Print** \> **Counting act (INV-6)** to open the **Print of counting act (INV-6)** dialog.
11.	In the **Date of act completion** field, select the date when the counting process is scheduled to be completed.
12.	In the **Start date** and **End date** fields, select the start and end dates of the inventory counting period.
13.	In the **Order number** field, enter the order number that you're generating the **Counting act INV-6** report for.
14.	In the **Resolution date** field, select the transaction date of the order that you're generating the **Counting act INV-6** report for.

    > [!NOTE]
    > The values in the **Journal**, **Dimension number**, and **Kind of inventory** fields are based on the inventory counting transactions. To change the values of these fields, select **Filter**. For example, you can modify these values to generate the report for a different journal or a different dimension.

    ![Print of counting act (INV-6).](../media/goods-in-transit-vendor-10.png)
 
15.	Select **OK** to generate the **Counting act (INV-6)** report.

    ![Printed Counting act (INV-6) report.](../media/goods-in-transit-vendor-11.png)
 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
