---
# required metadata

title: Not valuable fixed assets (NVFAs) (Russia)
description: This topic provides information about how to maintain not valuable fixed assets (NVFAs) for Russia.
author: ShylaThompson
ms.date: 11/06/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom
ms.search.region: Russia
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Not valuable fixed assets (NVFAs) (Russia)

[!include [banner](../includes/banner.md)]

Low-value, high-wear items that are used in the workplace can be tracked and accounted for as special types of fixed assets that are known as *not valuable fixed assets* (NVFAs). NVFAs are items that have a cost that is less than the specified cost limit. The full cost of NVFAs should be written off for depreciation in the first month of use.

When you purchase fixed assets, regular fixed assets and NVFAs are divided based on the purchase price (cost). The value that you set for the **Max cost of the NVFA** field when you [set up Fixed assets parameters for NVFAs](#set-up-fixed-assets-parameters-for-nvfas) determines the cost that distinguishes regular fixed assets and NVFAs.

After you purchase and register NVFAs, you can perform the following tasks:

- Automate the process of putting NVFAs into operation and adding them to subsequent depreciation transactions.
- Print the MB-2, MB-4, and MB-8 reports.

## Set up Fixed assets parameters for NVFAs 

1. Go to **Fixed assets (Russia)** \> **Setup** \> **Fixed assets parameters**.
2. In the **Base value model** field, select the default base value model.
3. In the **Max cost of the NVFA** field, enter the maximum limit for the cost of the NVFA.
4. In the **NVFA inventory profile** field, select the inventory profile for the NVFA.
5. On the **Number sequences** tab, in the **Number sequence code** field, select the number sequence code for the **NVFA inventory number** and **NVFA issue journal number** reference types.
6. On the **Document** tab, on the **Document types** FastTab, in the **Number sequence code** field, select the number sequence code for the **NVFA Act on disposal (No. MB-4)** and **NVFA Act on writing-off No. MB-8)** document types.

## Set up fixed asset groups for NVFA

1. Go to **Fixed assets (Russia)** \> **Setup** \> **FA groups**.
2. On the **FA groups** page, create a record, and fill in the fields. In the **Type of group** field, select **NVFA**.

## Set up the identification of fixed asset groups for NVFAs

1. Go to **Fixed assets (Russia)** \> **Setup** \> **Working clothes/Special riggings/NVFA** \> **Identification of FA groups**.
2. On the **Condition for FA group identification** page, create a record, and fill in the fields.
3. Select **Compliance**, and specify how the item is related to a fixed asset group.

    > [!NOTE]
    > The system uses this setting to fill in the **FA group** and **Lifetime** fields on the **Working clothes/Special riggings/NVFA issue journal lines** page. For more information, see [Generate NVFA records, putting into operation transactions, and depreciation transactions for NVFAs](#generate-nvfa-records-putting-into-operation-transactions-and-depreciation-transactions-for-nvfas).

## Set up inventory dimensions for NVFAs

Use this procedure to set up inventory dimensions for NVFAs, working clothes, and special rigging items.

1. Go to **Product information management** \> **Setup** \> **Dimensions and variant groups** \> **Tracking dimension groups**.
2. Create a dimension group.
3. For the **Batch number** dimension, select the **Active** check box to enable batch accounting for NVFAs. Items that have different prices are accounted for in different batches.
4. Also select the **Primary stocking** and **Financial inventory** check boxes for the **Batch number** dimension.
5. For the **Serial number** dimension, select the **Active** check box. This dimension is used when the asset is put into operation.
6. Also select the **Blank receipt allowed** and **Blank issue allowed** check boxes for the **Serial number** dimension. When these check boxes are selected, you can perform inventory operations without having to specify a serial number.
7. For the **Inventory profile** dimension, select the **Active** and **Primary stocking** check boxes to enable inventory profile accounting for NVFAs.

## Set up items as NVFAs

1. Go to **Product information management** \> **Products** \> **Released products**.
2. Create a new item, or double-click an existing item to open the item record.
3. Select **Set up** \> **Dimension groups** to set up storage and tracking dimension groups for the item.
4. In the **Item model group** field, select the item model group.
5. In the **FA group** field, select a fixed asset group that has the **NVFA** group type for the item.

## Set up officials for the NVFA Statement of writing-off (No. MB-8)

Use this procedure to set up the members and chairperson of the commission that is responsible for the NVFA Statement of writing off (No. MB-8).

1. Go to **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.
2. On the **Fixed assets** tab, select **NVFA Statement of writing-off (No. MB-8)**.
3. Select **Add** to create a record.
4. In the **Position** field, select **Member** or **Chairman** to indicate whether the selected employee is a commission member or the chairman. You can select only one employee as the chairman.
5. In the **Name** field, select the name of the employee.

## Register an NVFA by using a purchase order

1. Go to **Accounts payable** \> **Common** \> **Purchase orders** \> **All purchase orders**.
2. On the **Action Pane**, select **New** \> **Purchase order**.
3. In the **Vendor account** field, select the vendor account that you require, and then select **OK**.
4. Create a purchase order line.
5. In the **Item number** field, select an item number.
6. In the **Quantity** field, enter the quantity of the item that is being ordered.
7. In the **Unit price** field, enter the purchase price for an item unit. If the purchase price of a fixed asset is less than the value that is specified in the **Max cost of the NVFA** field on the **Fixed assets parameters** page, excluding the sales tax value, the item is considered an NVFA. In this case, the **Inventory profile** field on the **Product** tab of the **Line details** FastTab is automatically set to the value that is entered on the **Fixed assets parameters** page.
8. Post the vendor invoice.

> [!NOTE]
> If the system defines the item on the purchase line as an NVFA, you should not specify a fixed asset inventory number for that line in the purchase order.

## Generate NVFA records, putting into operation transactions, and depreciation transactions for NVFAs

Use this procedure to automatically create NVFA records on the **Not valuable FAs** page (**Fixed assets (Russia)** \> **Common** \> **Not valuable FAs**), and to automatically create fixed asset journals for NVFA putting into operation and depreciation.

1. Go to **Fixed asset (Russia)** \> **Journals** \> **Working clothes/Special riggings/NVFAs issue**.
2. Select **New** to create a journal, and fill in the fields.
3. Select **Lines**, and then select **New** to create a record.
4. Fill in the **Item** and **Quantity** fields. The values in the **Person in charge** and **Location** fields are filled in from the journal. The **Lifetime** and **FA group** fields are filled in automatically from the **Condition for FA group identification** page.
5. Verify and fill in the fields on the **Product dimensions** tab.
6. Close the **Working clothes/Special rigging/NVFA issue journal lines** page.
7. Select **Close** on the **Working clothes/Special rigging/NVFA issue journal** page. The system selects the **Posted** check box and creates fixed asset journals for NVFA putting into operation and depreciation. 
8. Select **FA journals** \> **FA journal (putting into operation)** and **FA journals** \> **FA journal (depreciation)** to validate and post fixed asset journals.

> [!NOTE]
> The system creates records on the **Not valuable FAs** page after the fixed asset journal for NVFA putting into operation is posted.

## Register an NVFA by using the Not valuable FAs page 

1. Go to **Fixed assets (Russia)** \> **Common** \> **Not valuable FAs**.
2. Select **Fixed asset** to create an NVFA.
3. In the **FA group** field, select a fixed asset group for the NVFA.
4. In the **Acquisition cost** field, enter the acquisition amount for the fixed asset.
5. In the **Note** field, enter any additional information for the asset.
6. In the **Resource** field, select the resource or resource group that is assigned to the asset.
7. Select **Fixed asset** \> **Componentry** \> **Componentry**.
8. Select **Add** to create a line. In the **Item number** field, select an item.
9. Select **Warehouse** \> **Dimensions display** to enable the **Batch number** and **Serial number** dimensions for the item.
10. In the **Batch number** field, select a batch number for the item.
11. In the **Serial number** field, select a serial number for the item.
12. In the **Initial quantity** field, enter the initial quantity of the item that is used.

## Generate a disposal transaction and print the NVFA Statement of disposal (No. MB-4) from the fixed asset journal 

Use this procedure to generate and print the **NVFA Statement of disposal (No. MB-4)** report from the fixed asset journal after you enter disposal or writing-off transactions. For transactions that have a status of **Written off** or **Written off (sale)**, the report can also be printed from the **Working clothes**, **Special rigging**, or **Not valuable FAs** page. This report is generated by each department that uses working clothes, special rigging, and NVFAs.

> [!NOTE]
> You can generate the report from the **Working clothes**, **Special rigging**, and **Not valuable FAs** pages only after you generate the report from the fixed asset journal.

1. Go to **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2. Create a journal.
3. In the **Name** field, select the journal name.
4. Select **Lines** to open the **Journal voucher** page.
5. Select **New** to open the **Add to journal** dialog box.
6. In the **Transaction date** field, select the transaction date.
7. In the **Transaction type** field, select **Disposal (sale)**.
8. In the **FA inventory number** field, select the inventory number for the fixed asset.
9. In the **Value model** field, select the value model for the fixed asset.
10. In the **Reason code** field, select a reason code for the transaction.
11. In the **Reason comment** field, enter a comment or a description of the transaction.
12. Select **OK**. The write-off lines for all value models that are registered in the fixed assets account are created in the journal.
    –or–

Select **Group operations** \> **Disposal (sale)** after step 4 to create disposal transactions     .

5. In the **Disposal date** field, select the date of the disposal transaction.
6. On the **Records to include** tab, select **Filter**. Then specify the selection criteria that are used to create transactions.
7. Select **OK**, and then select **OK** again to create disposal or write-off transactions.
8. Select **Validate** \> **Validate** to validate the write-off transactions.
9. Select **Post** \> **Post** to post the transaction.
10. Close the page.
11. On the **FA journal** page, select **Print** \> **NVFA Statement of disposal (No. MB-4)** to open the **NVFA Statement of disposal (No. MB-4)** page.

    > [!NOTE]
    > The **Print** button is available only for journals that have been posted. The written-off transaction that is created on the **Journal voucher** page appears on the **Overview** tab. This transaction has a document number. The document number is generated based on the number sequence that is set up on the **Fixed assets parameters** page.

22. In the **Comment** field, enter the reason for disposal.
23. On the **Rows** tab, you can view the document number, fixed asset number, and value model code.
24. Select **Print** to generate the **NVFA Statement of disposal (No. MB-4)** report.

## Generate a writing-off transaction and print the NVFA Statement of writing off (No. MB-8) from the fixed asset journal

Use this procedure to generate and print the **NVFA Statement of writing off (No. MB-8)** report from the fixed asset journal after you enter writing-off or disposal transactions. For transactions that have a status of **Written off** or **Written off (dismantlement)**, the report can also be printed from the **Working clothes**, **Special rigging**, or **Not valuable FAs** page.

1. Go to **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2. Create a journal.
3. In the **Name** field, select a journal name.
4. Select **Lines**.
5. Select **New** to open the **Add to journal** dialog box.
6. In the **Transaction date** field, select the transaction date.
7. In the **Transaction type** field, select **Writing-off**.
8. In the **FA inventory number** field, select the inventory number of the fixed asset.
9. Select **OK**. The value model lines for the asset record are created in the journal.
    –or–
Select **Group operations** \> **Writing-off** after step 4 to create writing-off transactions.

5. In the **Disposal date** field, select the date of the writing-off transaction.
6. On the **Records to include** tab, select **Filter**. Then specify the selection criteria that are used to create transactions.
7. Select **OK**, and then select **OK** again to create disposal or writing-off transactions.
8. On the **Journal voucher** page, select **Validate** \> **Validate** to validate the journal.
9. Select **Post** \> **Post** to post the journal.
9. Select **Print** \> **NVFA Statement of writing-off (No. MB-8)**.
10. On the **Overview** tab, in the **Order number** field, enter the order number that the writing-off transaction should be posted under. In the **Resolution date** field, select the order date.
11. On the **Rows** tab, you can verify the document number, fixed asset number, and value model code.
12. On the **Officials** tab, you can view details about the officials who were assigned on the **Officials** page. You can also modify the employee details, if modification is required.
13. Select **Print** to generate the **NVFA Statement of writing off (No. MB-8)** report.

## Additional resources

- [Working clothes/special rigging accounting (Russia)](rus-working-clothes-instruments-accounting.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]