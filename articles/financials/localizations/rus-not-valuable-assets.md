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

# Not valuable fixed assets (NVFAs) accounting for Russia

[!include [banner](../includes/banner.md)]

You can track and account for low-value, high-wear items that are used in the workplace as a special type of fixed asset, which named **Not valuable fixed assets** (NVFAs). NVFAs are items with a cost that is less than the specified cost limit. The full cost of NVFAs should be written off for depreciation in the first month of use.
In the process of Fixed asset purchasing the system divides fixed assets and NVFAs by price according to the **Max cost of the NVFA** parameter value (see [Set up fixed asset parameters for NVFAs](rus-fa-nv-assets/articles/financials/localizations/rus-not-valuable-assets.md#Set-up-fixed-asset-parameters-for-NVFAs)). 
After you purchase and register the NVFAs, you can perform the following tasks:

  - To automate the placement of NVFAs into operation and into subsequent depreciation transactions.

  - To print the MB-2, MB-4, and MB-8 reports.



## Set up fixed asset parameters for NVFAs 

Use this procedure to set up fixed asset parameters for not valuable fixed assets (NVFAs).

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Parameters**.
2.  In the **Base value model** field, select the default base value model.
3.  In the **Max cost of the NVFA** field, enter the maximum limit for the cost of the NVFA.
4.  In the **NVFA inventory profile** field, select the inventory profile for the NVFA.
5.  Click **Number sequences**.
6.  In the **Number sequence code** field, select the number sequence code for the **NVFA inventory number** and **NVFA issue journal number** reference types.
7.  Click **Document** and then click **Document types**.
8.  In the **Number sequence code** field, select the number sequence code for the **NVFA Act on disposal (No. MB-4)** and **NVFA Act on writing-off No. MB-8)** document types.

## Set up FA groups for NVFA

1.  Click **Fixed assets (Russia)** \> **Setup** \> **FA groups**
2.  Create a new record on the **FA GROUPS** page list and fill in the fields. Select **NVFA** in the **Type of group** field.


## Set up identification of FA groups for NVFAs 

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Working clothes/ Special riggings/ NVFA** \> **Identification of FA groups**
2.  Create a new record on the **CONDITION FOR FA GROUP IDENTIFICATION** page list and fill in the fields.
3. Click **Compliance** and specify item relation with FA group.

> [!NOTE]
    > The system uses this setting for filling  the **FA group** and **lifetime** fields on the **Working clothes/ Special riggings/ NVFA issue journal lines** page (see [Generate NVFA records, putting into operation and depreciation transactions for NVFAs](Generate-NVFA-records,-putting-into-operation-and-depreciation-transactions-for-NVFAs))   

## Set up inventory dimensions for NVFAs 

Use this procedure to set up inventory dimensions for not valuable fixed assets (NVFAs), working clothes, and special rigging items.

1.  Click **Product information management** \> **Setup** \> **Dimensions and variant groups** \> **Tracking dimension groups**.
2.  Create a new dimension group.
3.  Select the **Active** check box for the **Batch number** dimension to enable batch accounting for NVFAs. Items that have different prices are accounted for in different batches.
4.  Select the **Primary stocking** and **Financial inventory** check boxes for the **Batch number** dimension.
5.  Select the **Active** check box for the **Serial number** dimension. This dimension is used when the asset is put into operation.
6.  Select the **Blank receipt allowed** and **Blank issue allowed** check boxes for the **Serial number** dimension. When these check boxes are selected, you can perform inventory operations without specifying a serial number.
7.  Select **Active** and **Primary stocking** check boxes for the **Inventory profile** dimension to enable enventory profile accounting for NVFAs.  



## Set up items as not valuable fixed assets (NVFAs).

1.  Click **Product information management** \> **Products** \> **Released products**.
2.  Create a new item, or double-click an existing item record.
3.  Click **Set up** \> **Dimension groups** to set up storage and tracking dimension groups for the item.
4.  In the **Item model group** field, select the item model group.
5.  In the **FA group** field, select a fixed asset (FA) group with **NVFA** type of group for the item.


## Set up officials for the NVFA statement of writing-off (No. MB-8) 

Use this procedure to set up the members and chairman of the commission that is responsible for the NVFA Statement of writing off (No. MB-8).

1.  Click **Organization administration** \> **Setup** \> **Contacts** \> **Officials**.
2.  On the **Fixed assets** tab, click **NVFA Statement of writing-off (No. MB-8)**.
3.  Click **Add** to create a new record.
4.  In the **Position** field, select **Member** or **Chairman** to indicate whether the selected employee is a commission member or the chairman. You can only select one employee as the chairman.
5.  In the **Name** field, select the name of the employee.



## Register an NVFA using a purchase order 

Use this procedure to register a not valuable fixed asset (NVFA) by using a purchase order.

1.  Click **Accounts payable** \> **Common** \> **Purchase orders** \> **All purchase orders**. On the **Action Pane**, click **New** \> **Purchase order**.

2.  In the **Vendor account** field, select the vendor account that you require, and then click **OK**.
3.  Create a new purchase order line.
4.  In the **Item number** field, select an item number.  
5.  In the **Quantity** field, enter the quantity of the item that is ordered.
6.  In the **Unit price** field, enter the purchase price for an item unit. If the purchase price of a fixed asset is less than the value that is specified in the **Max cost of the NVFA** field in the **Fixed asset parameters** (excluding sales tax value), the item is considered to be an NVFA and the **Inventory profile** field (**Line details** \> **Product** tab) is filled in automatically by the value, specified in th **Fixed asset parameters**. 
7. Post the vendor invoice. 
    
    > [!NOTE]
    >  If the system defines the item in the purchase line as NVFA, you should not specify a fixed asset inventory number for this line in the **Purchase order**. 

## Generate NVFA records, putting into operation and depreciation transactions for NVFAs
Use this procedure for automatic creation of NVFA records on the **Not valuable FAs** page list (**Fixed assets (Russia)** \> **Common** \> **Not valuable FAs**) and FA journals for NVFA putting into operation and depreciation.
1. Click **Fixed asset (Russia)** \> **Journals** \> **Working clothes/ Special riggings / NVFAs issue**.
2. Click **New** to create a new journal and fill in the fields.
3. Click **Lines** and then **New** to create a new record.
4. Fill in the **Item** and **Quantity** fields. The values in the **Person in charge** and **Location** fields are filled in from the journal. The **Lifetime** and **FA group** fields are filled in automatically from the **CONDITION FOR FA GROUP IDENTIFICATION**
5. Check and fill in the fields on the **Product dimensions** tab.
6. Close **Working clothes/ Special rigging/ NVFA issue journal lines** page.
7. Click **Close** on the **Working clothes/ Special rigging/ NVFA issue journal** page. The system selects the **Posted** check box and creates FA journals for Putting NVFAs into operation and for depreciation. 
8. Click **FA journals** \> **FA journal (putting into operation)** and **FA journals** \> **FA journal (depreciation)** to validate and post FA journals.
> [!NOTE]
> The system creates records in the **Not valuable FAs** page list after posting FA journal (putting into operation).


## Register an NVFA using the Not valuable FAs page 

Use this procedure to register a not valuable fixed asset (NVFA) by using the **Not valuable FAs** page. 

1.  Click **Fixed assets (Russia)** \> **Common** \> **Not valuable FAs**. Click **Fixed asset** to create a new NVFA.
2.  In the **FA group** field, select a fixed asset (FA) group for the NVFA.
3.  In the **Acquisition cost** field, enter the acquisition amount for the FA.
4.  In the **Note** field, enter any additional information for the asset.
5.  In the **Resource** field, select the resource or resource group that is assigned to the asset.
6.  Click **FIXED ASSET** \>**Componentry** \> **Componentry**.
7.  Click **Add** to create a new line. In the **Item number** field, select an item.
8.  Click **Warehouse** \> **Dimensions display** to enable the **Batch number** and **Serial number** dimensions for the item.
9. In the **Batch number** field, select a batch number for the item.
10. In the **Serial number** field, select a serial number for the item.
11. In the **Initial quantity** field, enter the initial quantity of the item that is used.

## Generate a disposal transaction and print the NVFA statement of disposal (No. MB-4) from the fixed asset journal 

You can generate and print the **NVFA Statement of disposal (No. MB-4)** report from the fixed asset journal after you enter transactions of tdisposal or writing-off transactions. For transactions that have a status of **Written off** or **Written off (sale)**, the report can also be printed on the **Working clothes**, **Special rigging**, and **Not valuable FAs** pages. This report is generated by each department that uses working clothes, special rigging, and not valuable fixed assets (NVFAs).

> [!NOTE]
> You can generate the report from the **Working clothes**, **Special rigging**, and **Not valuable FAs** pages only after you generate the report from the fixed asset journal.

1.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2.  Create a new journal.
3.  In the **Name** field, select the journal name.
4.  Click **Lines** to open the **Journal voucher** page list.
5.  Press **New** to open the **Add to journal** page.
6.  In the **Transaction date** field, select the transaction date.
7.  In the **Transaction type** field, select **Disposal (sale)** as the transaction type.
8.  In the **FA inventory number** field, select the inventory number for the fixed asset.
9.  In the **Value model** field, select the value model for the fixed asset.
10. In the **Reason code** field, select a reason code for the transaction.
11. In the **Reason comment** field, enter a comment or a description of the transaction.
12. Click **OK**. The write-off lines for all value models that are registered in the fixed assets account are created in the journal.
  –or–
   Click **Group operations** \> **Disposal (sale)** to create disposal transactions.
    
14. In the **Disposal date** field, select the date of the disposal transaction.
15. Expand **Records to include** tab and click **Filter**. Then specify the selection criteria that are used to create transactions.
16. Click **OK**, then click **OK** again to create disposal or write-off transactions.
17. Click **Validate** \> **Validate** to validate the write-off transactions.
18. Click **Post** \> **Post** to post the transaction.
19. Close the page.
20. On the **FA journal** page, click **Print** \> **NVFA Statement of disposal (No. MB-4)** to open the **NVFA Statement of disposal (No. MB-4)** page.
    
    > [!NOTE]
    > <P>The <STRONG>Print</STRONG> button is available only for journals that have been posted. The written-off transaction that is created on the <STRONG>Journal voucher</STRONG> page is displayed on the <STRONG>Overview</STRONG> tab. This transaction has a document number that is generated based on the number sequence that is set up in the <STRONG>Fixed asset parameters</STRONG> form.</P>

22. In the **Comment** field, enter the reason for disposal.
23. On the **Rows** tab, you can view the document number, fixed asset number, and the value model code.
24. Click **Print** to generate the **NVFA Statement of disposal (No. MB-4)** report.

## Generate a write-off transaction and print the  NVFA statement of writing off (No. MB-8) from the fixed asset journal 

Use this procedure to print the not valuable fixed asset (NVFA) Statement of writing off (No. MB-8) from the fixed asset (FA) journal after you enter write-off or disposal transactions. The report can also be printed from the **Working clothes**, **Special rigging**, or **Not valuable FAs** page list for transactions that have a status of **Written off** or **Written off (dismantlement)**.

1.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2.  Create a new journal.
3.  In the **Name** field, select a journal name.
4.  Click **Lines**.
5.  Click **New** to open the **Add to journal** form.
6.  In the **Transaction date** field, select the transaction date.
7.  In the **Transaction type** field, select **Writing-off**.
8.  In the **FA inventory number** field, select the inventory number of the fixed asset.
9.  Click **OK**. The value model lines for the asset record are created in the journal.
10. Click **Group operations** \> **Writing-off** to create write-off transactions.
    
    –or–
    
    Click **Group operations** \> **Writting-off** to create writting-off transactions.

11. In the **Disposal date** field, select the date of the writting-off transaction.
12. Expand **Records to include** tab and click **Filter**. Then specify the selection criteria that are used to create transactions.
13. Click **OK**, and then click **OK** again to create disposal or write-off transactions.
14. In the **Journal voucher** page, click **Validate** \> **Validate** to validate the journal.
15. Click **Post** \> **Post** to post the journal.
16. Click **Print** \> **NVFA Statement of writing-off (No. MB-8)**.
17. On the **Overview** tab, in the **Order number** field, enter the order number that the write-off transaction is posted under, and in the **Resolution date** field, select the order date.
18. On the **Rows** tab, you can verify the document number, the fixed asset number, and the value model code.
19. On the **Officials** tab, you can view details about the officials, who are assigned in the **Officials**. You can also modify the employee details, if modification is required.
20. Click **Print** to generate the NVFA Statement of writing off (No. MB-8).

## Generate the NVFA accounting card (No. MB-2) for NVFAs, special rigging, and working clothes 

Use the **NVFA accounting card (No. MB-2)** report to generate the accounting card for a group of working clothes, special rigging, or not valuable fixed assets (NVFAs). The accounting card is printed for each combination of the person who is in charge of the asset and the selected location of the asset. The report number that is generated is a combination of the department code and the employee identification code of the recipient.

1.  Click **Fixed assets (Russia)** \> **Reports** \> **NVFA accounting card (No. MB-2)**.
2.  In the **Report date** field, select the transaction date for the accounting card.
3.  In the **Person in charge** field, select the employee who is in charge of the asset.
4.  In the **Location** field, select the location of the asset.
5.  Select the **Show only active** check box to show objects in exploitation only on the transaction date.
6.  Click **OK** to generate the accounting card.

## Generate the NVFA statement of disposal (No. MB-4) from the Working clothes, Special rigging, or Not valuable FAs page list 

Use the **Working clothes**, **Special rigging**, or **Not valuable FAs** page list to print the NVFA Statement of disposal (No. MB-4). This report is generated by each department that uses working clothes, special rigging, and not valuable fixed assets (NVFAs).

1.  Click **Fixed assets (Russia)** \> **Common** \> **Working clothes**.
    
    –or–
    
    Click **Fixed assets (Russia)** \> **Common** \> **Special rigging**.
    
    –or–
    
    Click **Fixed assets (Russia)** \> **Common** \> **Not valuable FAs**.

2.  Highlight the fixed asset that has the status **Written off** or **Written off (sale)**.

3.  Click **Documents** \> **NVFA Statement of disposal (No. MB-4)**.

4.  In the **Rows** field, enter the reason for asset disposal.

5.  Click **Print** to generate the statement of disposal.

## Generate the NVFA statement of writing-off (No. MB-8) from the Working clothes, Special rigging, or Not valuable FAs page list 

Use the **Working clothes**, **Special rigging**, or **Not valuable FAs** page list to print the NVFA Statement of writting-off (No. MB-4). This report is generated by each department that uses working clothes, special rigging, and not valuable fixed assets (NVFAs).

1.  Click **Fixed assets (Russia)** \> **Common** \> **Working clothes**.
    
    –or–
    
    Click **Fixed assets (Russia)** \> **Common** \> **Special rigging**.
    
    –or–
    
    Click **Fixed assets (Russia)** \> **Common** \> **Not valuable FAs**.

2.  Highlight the fixed asset that has a status of **Written off** or **Written off (sale)**.

3.  Click **Documents** \>**NVFA Statement of writing-off (No. MB-8)**.

4.  In the **Order number** field, enter the order number that the disposal transaction is posted under.

5.  In the **Resolution date** field, select the order date.

6.  Click the **Officials** tab. The details of the assigned officials are displayed. You can modify the employee details if changes are required.

7.  Click **Print** to generate the NVFA statement of writing-off (No. MB-8).
