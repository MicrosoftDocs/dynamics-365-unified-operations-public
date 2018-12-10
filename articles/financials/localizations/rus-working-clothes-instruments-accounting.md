---
# required metadata
title: FA - Specific accounting for working clothes/Special riggings
description: 
author: ShylaThompson
manager: AnnBe
ms.date: 10/04/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata
ms.search.form:  HcmWorkerAdvHolderTableListPage_RU, HcmWorkerAdvHolderTable_RU 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# FA - Specific accounting for working clothes/Special riggings
[!include [banner](../includes/banner.md)]

## About working clothes, and special rigging accounting
An organization must account for each working clothes item or special rigging asset that is issued to an employee, and create a Working clothes or Special rigging issue record. You can create queries to display all assets that are on-hand for employees and print the Working clothes issue sheet (No. MB-7). You can cancel or return the Working clothes or Special rigging issue to the inventory, and calculate the net book value and residual wearing period.

Working clothes and special rigging assets are regulated by their useful life cycle. This period starts when the item is written off from a warehouse and issued to an employee, and ends after a stipulated period of use. The useful lifetime is specified in months for each item. All of the data that pertains to an item is linked. This includes the identity of the employee, the useful life of the item, the date when the item is issued to the employee, and the calculated end date based on the rating of the item. When the end of the useful life approaches, the item is written off, so that it is no longer assigned to the employee.

During their life cycle, the cost of these types of assets must be amortized. If the life cycle is longer than 12 months, which is the legally defined rate, the linear method of depreciation is used. If it is less than 12 months, the cost is written off when the item is issued to the employee.

The Working clothes and Special rigging forms are similar to the Fixed assets page, which accounts for all issued working clothes and special rigging.

It is necessary to execute the following settings for accounting working clothes item or special rigging assets.

## Set up types of issue and usage rates

Use the **Types of issue and usage rates** page to define the types of issue and usage rates that determine which working clothes and special rigging are issued to employees.

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Working clothes/Special riggings/NVFA** \> **Type of rate**.

2.  In the **Type of rate** field, enter the identification code for the rate type.

3.  In the **Description** field, enter a short description for the rate type.

4.  Select the **Over-rate** check box to indicate that quantity control of the item issue by the defined rate is not required for the specified rate type.
    
    > [!NOTE]
    > <P>If this check box is selected, the rate type is used only to specify the wear or usage period of an asset.</P>
    
## Set up issue and usage rates for items

Use the **Issue and usage rates** page to define the types of issue and usage rates that determine the working clothes and special rigging items that are issued to employees.

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Working clothes/Special riggings/NVFA** \> **Issue and usage rates**.

2.  In the **Type of rate** field, select the identification code for the issue rate.

3.  In the **Item group** field, select the item group that the issue and usage rates apply to.

4.  In the **Item** field, select the code of the item that the issue and usage rates apply to.

5.  In the **Relation type (department)** field, select the departments that the issue and usage rates apply to, from the following options:
    
      - **All** – The issue and usage rates apply to all departments.
    
      - **Table** – The issue and usage rates apply to only a selected department.

6.  In the **Department** field, select the department of the employee.

7.  In the **Relation type (title)** field, select the job titles that the issue and usage rates apply to, from the following options:
    
      - **All** – The issue and usage rates apply to all job titles.
    
      - **Table** – The issue and usage rates apply to only a selected job title.

8.  In the **Title** field, select the job title of the employee.

9.  In the **Relation type (type of works)** field, select the types of work that the issue and usage rates apply to, from the following options:
    
      - **All** – The issue and usage rates apply to all types of work.
    
      - **Table** – The issue and usage rates apply to only a selected type of work.

10. In the **Type of works** field, select the type of work that the employee performs.

11. In the **Rate** field, enter the maximum quantity of the item that can be issued to the employee.

12. In the **Lifetime** field, enter the useful period of the item.

## Set up the item relation to working clothes and special rigging

Use this procedure to relate an item or an item group to a fixed asset (FA) group. You can use the following pagess to set up an item relation with a fixed asset group:

  - **Conditions for FA group definition** – Set up a period when the item relation is valid, and set up the maximum and minimum cost limits and the service life period for the item.

  - **Item relation with FA group** – Map the item to a fixed asset group.

  - **Copy item relations with FA group** – Copy the conditions for the item relation from an existing item relation.

<!-- end list -->

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Working clothes/Special riggings/NVFA** \> **Identification of FA group**.

2.  Click **New** to create a new condition.

3.  In the **Start date** field, select the starting date from which the item relation is effective.

4.  In the **End date** field, select the date until which the item relation is effective.

5.  In the **Cost from** field, enter the minimum limit for the cost price of the item.

6.  In the **Cost to** field, enter the maximum limit for the cost price of the item.

7.  In the **Service life from** field, enter the minimum service life for the item.

8.  In the **Service life till** field, enter the maximum service life for the item.

9.  Click **Compliance**.

10. In the **Item relation** field, select the item relation that has a fixed asset group, from the following options:
    
      - **Table** – Map a selected item to the fixed asset group.
    
      - **Group** – Map a selected item group to the fixed asset group.
    
      - **All** – Map all items to the fixed asset group.

11. In the **Item** field, select the item or the item group.

12. In the **FA group** field, select the fixed asset group.

13. Close the form.

14. Click **Copy** to open the **Copy item relations with FA group** form. You can also copy the conditions for the item relation from an existing item relation.

15. In the **Start date** field, select the starting date of the period for which item relations are copied.

16. Click **OK** to copy the item relations with fixed asset groups.

## Set up types of work

Use the **Types of works** page to define the types of work that employees perform. This information helps you determine the wear or usage period for each working clothes item, or the useful product output or mileage for each special rigging item.

1.  Click **Organization administration** \> **Setup** \> **Types of works**.

2.  In the **Type of works** field, enter an identification code for the type of work.

3.  In the **Name** field, enter the name of the type of work.

## Set up worker details for working clothes and special rigging
Use this procedure to indicate the type of work that is performed by an employee or worker to whom a working clothes item or special rigging item is issued.

1.  Click **Human resources** \> **Common** \> **Workers** \> **Workers**. Select a worker. On the **Action Pane**, click **Edit**.

2.  In the **Title** field, select the official title of the worker.

## Register special rigging manually

Use this procedure to manually register and manage special rigging items.

1.  Click **Fixed assets (Russia)** \> **Common** \> **Special rigging**. Click **Special rigging** to create a new special rigging item, or double-click an existing special rigging item.

2.  In the **FA group** field, select a fixed asset (FA) group for the special rigging item.

3.  In the **Acquisition cost** field, enter the acquisition amount for the asset.

4.  In the **Note** field, enter any additional information for the asset.

5.  In the **Type of rate** field, select the type of issue rate for the asset.

6.  In the **Resource** field, select the resource or resource group that is assigned to the asset.

7.  Click **Componentry** \> **Componentry**.

8.  Click **Add** to create a new line. In the **Item number** field, select an FA item or component.

9.  Click **Warehouse** \> **Dimensions display** to enable the **Batch number** and **Serial number** dimensions for the item.

10. In the **Batch number** field, select a batch number for the item.

11. In the **Serial number** field, select a serial number for the item.

12. In the **Initial quantity** field, enter the initial quantity of the item that is used.

## Register working clothes manually

Use this procedure to manually register and manage working clothes.

1.  Click **Fixed assets (Russia)** \> **Common** \> **Working clothes**. Click **Working clothes** to create a new working clothes item, or double-click an existing working clothes item.

2.  In the **FA group** field, select a fixed asset (FA) group for the working clothes item.

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

## Create a working clothes or special rigging issue journal 

Use the **Working clothes/Special rigging/NVFA issue** form to issue an item from the warehouse to an employee. Working clothes, special rigging items, and not valuable fixed assets (NVFAs) are separate assets. When an issue journal is posted, separate cards are created in the **Working clothes**, **Special rigging**, and **Not valuable FAs** pages.

When new working clothes or special rigging items are issued, the following actions occur:

  - A working clothes or special rigging card is created for each journal line, and the lines are updated in the **Working clothes** or **Special rigging** page.

  - The fixed asset (FA) number for the asset is generated based on the number sequence that is specified in the **Fixed asset parameters** page.

  - The quantity of the working clothes or special rigging item is equal to the item quantity that is specified on the journal line. In the **Componentry** form, the quantity of the corresponding item is updated to 1 for each asset that is created.

  - The value models and depreciation group are also updated in the cards. If you select the **Service life by rate** check box in the **FA value models** form, the wearing period, or usage, is determined based on the depreciation groups. If the **Service life by rate** check box is cleared, the wearing period is selected from the issued journal line. The cost is the same for all value models and is selected from the cost price of this item line.

  - The status of the asset is updated to **Scheduled**. Additionally, the acquisition date is updated with the date of the journal transaction, and the acquisition amount is updated with the cost price that is posted for the item line.

When a used working clothes or special rigging card is issued, if the serial number of the card for the issued item has already been filled in the inventory transaction that corresponds to the posted journal line, the following actions occur:

  - The issue journal that was created earlier is searched and copied by using the serial number inventory dimension.

  - The cost price is selected from the item cost price for the base value model.

  - The useful life is updated for the working clothes or special rigging item.

  - The residual wearing or usage period is calculated by subtracting the past lifetime from the lifetime by rate.

> [!NOTE]
> For an issue or reissue transaction, when the journal is posted, fixed asset journals are created and posted automatically. These fixed asset journals contain transactions for putting the asset into operation, depreciation transactions, and write-off transactions.


1.  Click **Fixed assets (Russia)** \> **Journals** \> **Working clothes/Special rigging/NVFA issue**.

2.  Create a new journal. In the **Date** field, select the transaction date.

3.  In the **Acquisition** field, select the fixed asset journal that is used for acquisition transactions.

4.  In the **Depreciation** field, select the fixed asset journal that is used for depreciation transactions.

5.  In the **Warehouse** field, select the warehouse for the transaction.

6.  In the **Person in charge** field, select the identification code of the employee to whom the asset is issued.

7.  In the **Location** field, select the location of the asset.

8.  Click **Lines**.

9.  Create a new journal line. In the **Item** field, select the item code.

10. In the **Quantity** field, enter the item quantity.

11. In the **Type of rate** field, select the type of issue rate for the item.

12. In the **Resource** field, select the resource or resource group that is assigned to the item.
    
    > [!NOTE]
    > The **Lifetime** field is updated with the useful life of the item for the selected combination of the following: item number, type of rate in the priority unit of the organization unit, job title, and type of work of the employee.

13. On the **Product dimensions** tab, in the **Warehouse** field, select the warehouse where the item is located.

14. In the **Inventory profile** field, select the inventory profile for the item.

15. In the **Batch number** field, select the batch number of the item.

16. In the **Serial number** field, select the serial number of the item.

17. Close the page.

18. In the **Working clothes/Special rigging/NVFA issue journal** form, click **Validate** to validate the journal.

19. Click **FA journals** \> **FA journal (putting into operation)** to put the asset into operation.
    
    –or–
    
    Click **FA journals** \> **FA journal (depreciation)** to depreciate the asset.

20. Click **Close** to post the journal.

To reverse the issue of the working clothes or special rigging item, in the **Working clothes/Special rigging/NVFA issue journal** page, click **Cancel issue**.

## Return working clothes or special rigging to the warehouse 

Use this procedure to return a working clothes item or special rigging item to a warehouse.

1.  Click **Fixed assets (Russia)** \> **Common** \> **Working clothes**. Double-click an existing working clothes item.
    
    –or–
    
    Click **Fixed assets (Russia)** \> **Common** \> **Special rigging**. Double-click an existing special rigging item.

2.  Click **Componentry** \> **Componentry**.

3.  Select the fixed asset item or component that is required, and then click **Add to remains**.

4.  In the **Quantity** field, enter the remaining quantity of the item.

5.  Click **OK** to add the working clothes item or special rigging item to item remainders. The lines that are marked in the upper pane of the **Componentry** form are moved to the lower pane.

6.  In the lower pane, click **Calculating prices** to calculate the balance value, depreciation, and depreciated cost for each item that is returned. The calculations are based on the price calculation method that is selected.

7.  Close the page.

8.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.

9.  Create a new fixed asset (FA) journal.

10. In the **Name** field, select a journal name.

11. Click **Lines**.

12. Click **New** to open the **Add to journal** page.

13. In the **Transaction date** field, select the transaction date.

14. In the **Transaction type** field, select **Disposal (dismantlement)**.

15. In the **FA inventory number** field, select the inventory number of the fixed asset.

16. Click **OK**. The value model lines for the asset record are created in the journal.

17. Click **Validate** \> **Validate** to validate the journal.

18. Click **Post** \> **Post** to post the journal.
