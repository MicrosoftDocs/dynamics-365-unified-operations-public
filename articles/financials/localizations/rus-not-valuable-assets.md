---
# required metadata

title: Not valuable fixed assets (NVFAs) for Russia
description: This topic provides information about maintaining Not valuable fixed assets (NVFAs) for Russia.
author: ShylaThompson
manager: AnnBe
ms.date: 11/06/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Not valuable fixed assets (NVFAs) for Russia

[!include [banner](../includes/banner.md)]

You can also track and account for low-value, high-wear items that are used in the workplace as a special type of fixed asset. Not valuable fixed assets (NVFAs) are items with a cost that is less than the specified cost limit. The full cost of NVFAs should be written off for depreciation in the first month of use.

If the purchase price of a fixed asset is less than the value that is specified in the **Max cost of the NVFA** field in the **Fixed asset parameters** form, the item is considered to be an NVFA. You cannot specify a fixed asset inventory number for this item in the **Purchase order** form. You cannot register the NVFA directly in the **Not valuable FAs** form until the purchase order process is completed.

After you purchase and register the NVFAs, you can perform the following tasks:

  - Divide fixed assets and NVFAs by price when you post purchase orders.

  - Automate the placement of NVFAs into operation and into subsequent depreciation transactions.

  - Print the MB-2, MB-4, and MB-8 reports.

An organization must account for each working clothes item or special rigging asset that is issued to an employee, and create a Working clothes or Special rigging issue card. You can create queries to display all assets that are on-hand for employees and print the **Working clothes issue sheet (No. MB-7)**. You can cancel or return the Working clothes or Special rigging issue card to the warehouse, and calculate the net book value and residual wearing period.

Working clothes and special rigging assets are regulated by their useful life cycle. This period starts when the item is written off from a warehouse and issued to an employee, and ends after a stipulated period of use. The useful lifetime is specified in months for each item. All of the data that pertains to an item is linked. This includes the identity of the employee, the useful life of the item, the date when the item is issued to the employee, and the calculated end date based on the rating of the item. When the end of the useful life approaches, the item is written off, so that it is no longer assigned to the employee.

During their life cycle, the cost of these types of assets must be amortized. If the life cycle is longer than 12 months, which is the legally defined rate, the linear method of depreciation is used. If it is less than 12 months, the cost is written off when the item is issued to the employee.

The **Working clothes** and **Special rigging** pages are similar to the **Fixed assets** page, which accounts for all issued working clothes and special rigging.

## Register an NVFA using a purchase order 

Use this procedure to register a not valuable fixed asset (NVFA) by using a purchase order.

1.  Click **Procurement and sourcing** \> **Common** \> **Purchase orders** \> **All purchase orders**. On the **Action Pane**, click **New** \> **Purchase order**.

2.  In the **Vendor account** field, select the vendor account that you require, and then click **OK**.
3.  Create a new purchase order line.
4.  In the **Item number** field, select an item number. The item must be a fixed asset item and must have an NVFA posting profile.
5.  In the **Quantity** field, enter the quantity of the item that is ordered.
6.  In the **Unit price** field, enter the purchase price for an item unit.
7.  In the **Net amount** field, enter the amount. This amount includes any discounts that are applied.
8.  Post the vendor invoice. 
    
    > [!NOTE]
    > The cost price of the item cannot be more than the limit that is specified in the **Fixed asset parameters** page. The posting profile that is displayed for the item must differ from the posting profile that is selected in the **Fixed asset parameters** page.

## Set up number sequences for NVFAs, working clothes, and special rigging accounting 

Use the **Fixed asset parameters** form to set up number sequences for working clothes, special rigging, not valuable fixed assets (NVFAs), and the related issue journals.

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Parameters**.
2.  Click **Number sequences**.
3.  In the **Number sequence code** field, select a number sequence code for the following reference types: **Special rigging inventory number**, **Working clothes number**, **NVFA inventory number**, and **Working clothes/Special rigging/NVFA issue journal**.

## Set up fixed asset parameters for NVFAs 

Use this procedure to set up fixed asset parameters for not valuable fixed assets (NVFAs).

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Parameters**.
2.  In the **Base value model** field, select the default base value model.
3.  In the **Max cost of the NVFA** field, enter the maximum limit for the cost of the NVFA.
4.  In the **NVFA inventory profile** field, select the inventory profile for the NVFA.
5.  Click **Number sequences**.
6.  In the **Number sequence code** field, select the number sequence code for the **NVFA inventory number** and **Working clothes/Special rigging/NVFA issue journal number** reference types.

## Set up parameters for the NVFA statement of writing-off (No. MB-8) 

Use this procedure to set up parameters for not valuable fixed assets (NVFAs) by using the NVFA statement of writing-off (No. MB-8).

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Parameters**.
2.  Click **Document**.
3.  In the **Document location** field, select the folder where the statement is saved.
4.  Click **Document types**.
5.  In the **Number sequence code** field, select the number sequence code for the **NVFA Act on writing-off No. MB-8)** document type.

## Set up officials for the NVFA statement of writing-off (No. MB-8) 

Use this procedure to set up the members and chairman of the commission that is responsible for the NVFA Statement of writing off (No. MB-8).

1.  Click **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.
2.  On the **Fixed assets** tab, click **NVFA Statement of writing-off (No. MB-8)**.
3.  Click **Add** to create a new record.
4.  In the **Position** field, select **Member** or **Chairman** to indicate whether the selected employee is a commission member or the chairman. You can only select one employee as the chairman.
5.  In the **Name** field, select the name of the employee.

## Set up a document location for the NVFA accounting card (No. MB-2) 

Use the **Fixed asset parameters** form to set up the document location for the not valuable fixed asset (NVFA) accounting card (No. MB-2).

1.  Click **Fixed assets** \> **Setup** \> **Fixed assets parameters**.
2.  Click **Document**.
3.  In the **Document location** field, select the folder where the accounting card is saved.

## Set up parameters for the NVFA statement of disposal (No. MB-4) 

Companies are required to generate a unified NVFA Statement of disposal (No. MB-4) to document the disposal of work clothes, special rigging, and not valuable fixed assets (NVFAs). You can generate and print the NVFA Statement of disposal (No. MB-4) from the **FA journal** form. You can also generate the statement from the **Working clothes**, **Special rigging**, and **Not valuable FAs** forms. Data in the fixed asset journal is grouped by the department name. Data is also grouped by the general ledger account that corresponds to the transactions that occurred when the working clothes, special rigging, and NVFAs are put into operation.

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Parameters**.
2.  Click **Document**.
3.  In the **Document location** field, select the folder where the statement is saved.
4.  Click **Document types**.
5.  In the **Number sequence code** field, select the number sequence code for the **NVFA Act on disposal (No. MB-4)** document type.

## Set up inventory dimensions for NVFAs 

Use this procedure to set up inventory dimensions for not valuable fixed assets (NVFAs), working clothes, and special rigging items.

1.  Click **Product information management** \> **Setup** \> **Dimension groups** \> **Tracking dimension groups**.
2.  Create a new dimension group.
3.  Select the **Active** check box for the **Batch number** dimension to enable batch accounting for NVFAs, working clothes, and special rigging items. Items that have different prices are accounted for in different batches.
4.  Select the **Primary stocking** and **Financial inventory** check boxes for the **Batch number** dimension.
5.  Select the **Active** check box for the **Serial number** dimension. This dimension is used when the asset is put into operation.
6.  Select the **Blank receipt allowed** and **Blank issue allowed** check boxes for the **Serial number** dimension. When these check boxes are selected, you can perform inventory operations without specifying a serial number.

## Set up item details for NVFAs 

Use this procedure to set up items as not valuable fixed assets (NVFAs).

1.  Click **Product information management** \> **Common** \> **Released products**.
2.  Create a new item, or double-click an existing item record.
3.  Click **Set up** \> **Dimension groups** to set up storage and tracking dimension groups for the item.
4.  In the **Item model group** field, select the item model group.
5.  In the **FA group** field, select a fixed asset (FA) group for the item.

## Register an NVFA using the Not valuable FAs page 

Use this procedure to register a not valuable fixed asset (NVFA) by using the **Not valuable FAs** form. You can track and account for low-value, high-wear items that are used in the workplace as not valuable fixed assets (NVFAs). NVFAs are items with a cost that is less than the specified cost limit. The full cost of NVFAs should be written off for depreciation during the first month of use. Use this form to create and maintain NVFAs.

1.  Click **Fixed assets (Russia)** \> **Common** \> **Not valuable FAs**. Click **Fixed asset** to create a new NVFA, or double-click an existing NVFA.
2.  In the **FA group** field, select a fixed asset (FA) group for the NVFA.
3.  In the **Acquisition cost** field, enter the acquisition amount for the FA.
4.  In the **Note** field, enter any additional information for the asset.
5.  In the **Type of rate** field, select the type of issue rate for the asset.
6.  In the **Resource** field, select the resource or resource group that is assigned to the asset.
7.  Click **Componentry** \> **Componentry**.
8.  Click **Add** to create a new line. In the **Item number** field, select an FA item or component.
9.  Click **Warehouse** \> **Dimensions display** to enable the **Batch number** and **Serial number** dimensions for the item.
10. In the **Batch number** field, select a batch number for the item.
11. In the **Serial number** field, select a serial number for the item.
12. In the **Initial quantity** field, enter the initial quantity of the item that is used.

## Generate a write-off transaction and print the NVFA statement of disposal (No. MB-4) from the fixed asset journal 

You can generate and print the **NVFA Statement of disposal (No. MB-4)** report from the fixed asset journal after you enter transactions of the **Disposal (sale)** and **Writing-off** types. For transactions that have a status of **Written off** or **Written off (sale)**, the report can also be printed from the **Working clothes**, **Special rigging**, and **Not valuable FAs** forms. This report is generated by each department that uses working clothes, special rigging, and not valuable fixed assets (NVFAs).

> [!NOTE]
> You can generate the report from the **Working clothes**, **Special rigging**, and **Not valuable FAs** forms only after you generate the report from the fixed asset journal.

1.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2.  Create a new journal.
3.  In the **Name** field, select the journal name.
4.  Click **Lines** to open the **Journal voucher** form.
5.  Press CTRL+N to open the **Add to journal** form.
6.  In the **Transaction date** field, select the transaction date.
7.  In the **Transaction type** field, select **Writing off** or **Disposal (sale)** as the transaction type.
8.  In the **FA inventory number** field, select the inventory number for the fixed asset.
9.  In the **Value model** field, select the value model for the fixed asset.
10. In the **Reason code** field, select a reason code for the transaction.
11. In the **Reason comment** field, enter a comment or a description of the transaction.
12. Click **OK**. The write-off lines for all value models that are registered in the fixed assets account are created in the journal.
13. For group operations, click **Group operations** \> **Writing off** to create write-off transactions.
   
    > [!NOTE]
    > <P>You can also select <STRONG>Disposal</STRONG>.</P>

14. In the **Disposal date** field, select the date of the disposal transaction.
15. Click **Select** to open the **Inquiry** form and specify the criteria for the report.
16. Click **OK** to close the **Inquiry** form.
17. In the **Writing-off** form, click **OK**. Write-off transactions are created in the journal for all value models.
18. Click **Validate** \> **Validate** to validate the write-off transactions.
19. Click **Post** \> **Post** to post the transaction.
20. Close the page.
21. In the **FA journal** page, click **Print** \> **NVFA Statement of disposal (No. MB-4)** to open the **NVFA Statement of disposal (No. MB-4)** page.
    
    > [!NOTE]
    > <P>The <STRONG>Print</STRONG> button is available only for journals that have been posted. The written-off transaction that is created in the <STRONG>Journal voucher</STRONG> form is displayed on the <STRONG>Overview</STRONG> tab. This transaction has a document number that is generated based on the number sequence that is set up in the <STRONG>Fixed asset parameters</STRONG> form.</P>

22. In the **Comment** field, enter the reason for disposal.
23. On the **Rows** tab, you can view the document number, fixed asset number, and the value model code.
24. Click **OK** to generate the **NVFA Statement of disposal (No. MB-4)** report.

## Generate a write-off transaction and print the NVFA statement of writing off (No. MB-8) from the fixed asset journal 

Use this procedure to print the not valuable fixed asset (NVFA) Statement of writing off (No. MB-8) from the fixed asset (FA) journal after you enter disposal or write-off transactions. The report can also be printed from the **Working clothes**, **Special rigging**, or **Not valuable FAs** form for transactions that have a status of **Written off** or **Written off (dismantlement)**.

1.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2.  Create a new journal.
3.  In the **Name** field, select a journal name.
4.  Click **Lines**.
5.  Click **New** to open the **Add to journal** form.
6.  In the **Transaction date** field, select the transaction date.
7.  In the **Transaction type** field, select **Writing-off** or **Disposal (sale)**.
8.  In the **FA inventory number** field, select the inventory number of the fixed asset.
9.  Click **OK**. The value model lines for the asset record are created in the journal.
10. Click **Group operations** \> **Writing-off** to create write-off transactions.
    
    –or–
    
    Click **Group operations** \> **Disposal (sale)** to create disposal transactions.

11. In the **Disposal date** field, select the date of the disposal transaction.
12. Click **Select**, and then specify the selection criteria that are used to create transactions.
13. Click **OK**, and then click **OK** again to create disposal or write-off transactions.
14. In the **Journal voucher** form, click **Validate** \> **Validate** to validate the journal.
15. Click **Post** \> **Post** to post the journal.
16. Click **Print** \> **NVFA Statement of writing-off (No. MB-8)** to open the **NVFA Statement of writing-off (No. MB-8)** form.
17. In the **Order number** field, enter the order number that the disposal transaction is posted under.
18. In the **Resolution date** field, select the order date.
19. On the **Rows** tab, you can verify the document number, the fixed asset number, and the value model code.
20. On the **Officials** tab, you can view details about the officials who are assigned in the **Officials** form. You can also modify the employee details, if modification is required.
21. Click **OK** to generate the NVFA Statement of writing off (No. MB-8).

## Generate the NVFA accounting card (No. MB-2) for NVFAs, special rigging, and working clothes 

Use the **NVFA accounting card (No. MB-2)** report to generate the accounting card for a group of working clothes, special rigging, or not valuable fixed assets (NVFAs). The accounting card is printed for each combination of the person who is in charge of the asset and the selected location of the asset. The report number that is generated is a combination of the department code and the employee identification code of the recipient.

1.  Click **Fixed assets (Russia)** \> **Reports** \> **NVFA accounting card (No. MB-2)**.
2.  In the **Report date** field, select the transaction date for the accounting card.
3.  In the **Person in charge** field, select the employee who is in charge of the asset.
4.  In the **Location** field, select the location of the asset.
5.  Select the **Show only active** check box to display only the NVFAs that have a status of **Show objects in exploitation only.** on the transaction date.
6.  Click **OK** to generate the accounting card.

## Generate the NVFA statement of disposal (No. MB-4) from the Working clothes, Special rigging, or Not valuable FAs forms 

Use the **Working clothes**, **Special rigging**, and **Not valuable FAs** forms to print the NVFA Statement of disposal (No. MB-4). This report is generated by each department that uses working clothes, special rigging, and not valuable fixed assets (NVFAs).

1.  Click **Fixed assets (Russia)** \> **Common** \> **Working clothes**.
    
    –or–
    
    Click **Fixed assets (Russia)** \> **Common** \> **Special rigging**.
    
    –or–
    
    Click **Fixed assets (Russia)** \> **Common** \> **Not valuable FAs**.

2.  Double-click an asset that has the status **Written off** or **Written off (sale)**.

3.  Click **Documents** \> **NVFA Statement of disposal (No. MB-4)**.

4.  In the **Rows** field, enter the reason for asset disposal.

5.  Click **OK** to generate the statement of disposal.

## Generate the NVFA statement of writing-off (No. MB-8) from the Working clothes, Special rigging, or Not valuable FAs forms 

Use the **Working clothes**, **Special rigging**, and **Not valuable FAs** forms to print the NVFA Statement of disposal (No. MB-4). This report is generated by each department that uses working clothes, special rigging, and not valuable fixed assets (NVFAs).

1.  Click **Fixed assets (Russia)** \> **Common** \> **Working clothes**.
    
    –or–
    
    Click **Fixed assets (Russia)** \> **Common** \> **Special rigging**.
    
    –or–
    
    Click **Fixed assets (Russia)** \> **Common** \> **Not valuable FAs**.

2.  Double-click an asset that has a status of **Written off** or **Written off (sale)**.

3.  Click **Documents** \>**NVFA Statement of writing-off (No. MB-8)**.

4.  In the **Order number** field, enter the order number that the disposal transaction is posted under.

5.  In the **Resolution date** field, select the order date.

6.  Click the **Officials** tab. The details of the assigned officials are displayed. You can modify the employee details if changes are required.

7.  Click **OK** to generate the NVFA statement of writing-off (No. MB-8).
