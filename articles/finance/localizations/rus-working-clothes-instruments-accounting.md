---
# required metadata
title: Working clothes/special rigging accounting (Russia)
description: This topic provides information about how to maintain working clothes and special rigging for Russia.
author: ShylaThompson
ms.date: 10/04/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form:  HcmWorkerAdvHolderTableListPage_RU, HcmWorkerAdvHolderTable_RU 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Working clothes/special rigging accounting (Russia)

[!include [banner](../includes/banner.md)]

## About working clothes and special rigging accounting

An organization must account for each working clothes or special rigging asset that is issued to an employee. For each of these assets, the organization must create a working clothes or special rigging issue record.

You can create queries to show all assets that are on hand for employees, and you can print the **Working clothes issue sheet (No. MB-7)** report. You can also cancel the working clothes or special rigging issue, or return it to inventory. Finally, you can calculate the net book value and the residual wear or usage period.

Working clothes and special rigging assets are regulated by their useful life. This period starts when the item is written off from a warehouse and issued to an employee. It ends after a specified period of use. The useful life of each item is specified in months.

All the data that is related to an item is linked. This information includes the identity of the employee, the useful life of the item, the date when the item is issued to the employee, and the end date that is calculated based on the rating of the item.

When the end of the item's useful life approaches, the item is written off, so that it's no longer assigned to the employee.

The cost of working clothes and special rigging assets must be amortized during their life cycle. If the life cycle is longer than 12 months (the legally defined period length), the linear method of depreciation is used. If the life cycle is shorter than 12 months, the cost is written off when the item is issued to the employee.

The **Working clothes** and **Special rigging** pages resemble the **Fixed assets** page that is used to account for all working clothes and special rigging that are issued.

The following sections describe the setup that you must complete to account for working clothes and special rigging assets.

## Set up types of issue and usage rates

Use the **Types of issue and usage rates** page to define the types of issue and usage rates that determine which working clothes and special rigging are issued to employees.

1. Go to **Fixed assets (Russia)** \> **Setup** \> **Working clothes/Special riggings/NVFA** \> **Type of rate**.
2. In the **Type of rate** field, enter the identification code for the rate type.
3. In the **Description** field, enter a short description of the rate type.
4. Select the **Over-rate** check box to indicate that quantity control that is based on the defined rate isn't required for item issues for the specified rate type.

    > [!NOTE]
    > If this check box is selected, the rate type is used only to specify the wear or usage period of an asset.

## Set up issue and usage rates for items

Use the **Issue and usage rates** page to define the usage rates for types of rates that determine which working clothes and special rigging items that are issued to employees.

1. Go to **Fixed assets (Russia)** \> **Setup** \> **Working clothes/Special riggings/NVFA** \> **Issue and usage rates**.
2. In the **Type of rate** field, select the identification code for the issue rate.
3. In the **Item group** field, select the item group that the issue and usage rates apply to.
4. In the **Item** field, select the code for the item that the issue and usage rates apply to.
5. In the **Relation type (department)** field, select the departments that the issue and usage rates apply to:

    - **All** – The issue and usage rates apply to all departments.
    - **Table** – The issue and usage rates apply to only a selected department.

6. If you selected **Table** in the **Relation type (department)** field, in the **Department** field, select the employee's department.
7. In the **Relation type (title)** field, select the job titles that the issue and usage rates apply to:

    - **All** – The issue and usage rates apply to all job titles.
    - **Table** – The issue and usage rates apply to only a selected job title.

8. If you selected **Table** in the **Relation type (title)** field, in the **Title** field, select the employee's job title.
9. In the **Relation type (type of works)** field, select the types of work that the issue and usage rates apply to:

    - **All** – The issue and usage rates apply to all types of work.
    - **Table** – The issue and usage rates apply to only a selected type of work.

10. If you selected **Table** in the **Relation type (type of works)** field, in the **Type of works** field, select the type of work that the employee does.
11. In the **Rate** field, enter the maximum quantity of the item that can be issued to the employee.
12. In the **Lifetime** field, enter the useful life of the item.

## Set up an item relation for working clothes and special rigging items

Use this procedure to relate an item or an item group to a fixed asset group. You can use the following pages to set up an item relation with a fixed asset group:

- **Conditions for FA group definition** – Set up a period when the item relation is valid, and set up the maximum and minimum cost limits and the service life period for the item.
- **Item relation with FA group** – Map the item to a fixed asset group.
- **Copy item relations with FA group** – Copy the conditions for the item relation from an existing item relation.

1. Go to **Fixed assets (Russia)** \> **Setup** \> **Working clothes/Special riggings/NVFA** \> **Identification of FA group**.
2. Select **New** to create a condition.
3. In the **Start date** field, select the date when the item relation becomes effective.
4. In the **End date** field, select the date when the item relation expires.
5. In the **Cost from** field, enter the minimum limit for the cost price of the item.
6. In the **Cost to** field, enter the maximum limit for the cost price of the item.
7. In the **Service life from** field, enter the minimum service life for the item.
8. In the **Service life till** field, enter the maximum service life for the item.
9. Select **Compliance**.
10. In the **Item relation** field, select the item relation with a fixed asset group:

    - **Table** – Map a selected item to a fixed asset group.
    - **Group** – Map a selected item group to a fixed asset group.
    - **All** – Map all items to a fixed asset group.

11. If you selected **Table** or **Group** in the **Item relation** field, in the **Item** field, select the item or the item group.
12. In the **FA group** field, select the fixed asset group.
13. Close the page.
14. Select **Copy** to open the **Copy item relations with FA group** dialog box. You can also copy the conditions for the item relation from an existing item relation.
15. In the **Start date** field, select the start date of the period that item relations are copied for.
16. Select **OK** to copy the item relations with fixed asset groups.

## Set up types of work

Use the **Types of works** page to define the types of work that employees do. This information helps you determine the wear or usage period for each working clothes item, or the useful product output or mileage for each special rigging item.

1. Go to **Organization administration** \> **Setup** \> **Types of works**.
2. In the **Type of works** field, enter an identification code for the type of work.
3. In the **Name** field, enter the name of the type of work.

## Set up worker details for working clothes and special rigging items

Use this procedure to specify the type of work that is done by an employee or worker that a working clothes or special rigging item is issued to.

1. Go to **Human resources** \> **Common** \> **Workers** \> **Workers**.
2. Select a worker, and then, on the **Action Pane**, select **Edit**.
3. In the **Title** field, select the official title of the worker.

## Manually register special rigging items

Use this procedure to manually register and manage special rigging items.

1. Go to **Fixed assets (Russia)** \> **Common** \> **Special rigging**.
2. Select **New** to create a new special rigging item, or double-click an existing special rigging item.
3. In the **FA group** field, select a fixed asset group for the special rigging item.
4. In the **Acquisition cost** field, enter the acquisition amount for the asset.
5. In the **Note** field, enter any additional information for the asset.
6. In the **Type of rate** field, select the type of issue rate for the asset.
7. In the **Resource** field, select the resource or resource group that is assigned to the asset.
8. Select **Componentry** \> **Componentry**.
9. Select **Add** to create a line.
10. In the **Item number** field, select a fixed asset item or component.
11. Select **Warehouse** \> **Dimensions display** to enable the **Batch number** and **Serial number** dimensions for the item.
12. In the **Batch number** field, select a batch number for the item.
13. In the **Serial number** field, select a serial number for the item.
14. In the **Initial quantity** field, enter the initial quantity of the item that is used.

## Manually register working clothes items

Use this procedure to manually register and manage working clothes items.

1. Select **Fixed assets (Russia)** \> **Common** \> **Working clothes**.
2. Select **New** to create a new working clothes item, or double-click an existing working clothes item.
3. In the **FA group** field, select a fixed asset group for the working clothes item.
4. In the **Acquisition cost** field, enter the acquisition amount for the asset.
5. In the **Note** field, enter any additional information for the asset.
6. In the **Type of rate** field, select the type of issue rate for the asset.
7. In the **Resource** field, select the resource or resource group that is assigned to the asset.
8. Select **Componentry** \> **Componentry**.
9. Select **Add** to create a line.
10. In the **Item number** field, select a fixed asset item or component.
11. Select **Warehouse** \> **Dimensions display** to enable the **Batch number** and **Serial number** dimensions for the item.
12. In the **Batch number** field, select a batch number for the item.
13. In the **Serial number** field, select a serial number for the item.
14. In the **Initial quantity** field, enter the initial quantity of the item that is used.

## Create a working clothes or special rigging issue journal 

Use the **Working clothes/Special rigging/NVFA issue** page to issue an item from the warehouse to an employee. Working clothes items, special rigging items, and not valuable fixed assets (NVFAs) are separate assets. When an issue journal is posted, separate cards are created on the **Working clothes**, **Special rigging**, and **Not valuable FAs** pages.

When new working clothes or special rigging items are issued, the following actions occur:

- A working clothes or special rigging card is created for each journal line, and the lines are updated on the **Working clothes** or **Special rigging** page.
- A fixed asset number is generated for the asset, based on the number sequence that is specified on the **Fixed assets parameters** page.
- The quantity of the working clothes or special rigging item equals the item quantity that is specified on the journal line. On the **Componentry** page, the quantity of the corresponding item is updated to **1** for each asset that is created.
- The value models and depreciation group are also updated on the cards. If you select the **Service life by rate** check box on the **FA value models** page, the wear or usage period is determined based on the depreciation group. If the **Service life by rate** check box is cleared, the wear or usage period is taken from the issued journal line. The cost is the same for all value models and is selected from the cost price of the item line.
- The status of the asset is updated to **Scheduled**. Additionally, the acquisition date is updated with the date of the journal transaction, and the acquisition amount is updated with the cost price that is posted for the item line.

When used working clothes or special rigging items are issued, if the serial number of the card for the issued item has already been filled in for the inventory transaction that corresponds to the posted journal line, the following actions occur:

- The issue journal that was created earlier is searched and copied by using the Serial number inventory dimension.
- The cost price is selected from the item cost price for the base value model.
- The useful life is updated for the working clothes or special rigging item.
- The residual wear or usage period is calculated by subtracting the past lifetime from the lifetime that is defined by the usage   rate.

> [!NOTE]
> For an issue or reissue transaction, when the journal is posted, fixed asset journals are automatically created and posted. These fixed asset journals contain transactions for putting the asset into operation, depreciation transactions, and writing-off transactions.

1. Go to **Fixed assets (Russia)** \> **Journals** \> **Working clothes/Special rigging/NVFA issue**.
2. Create a journal.
3. In the **Date** field, select the transaction date.
4. In the **Acquisition** field, select the fixed asset journal that is used for acquisition transactions.
5. In the **Depreciation** field, select the fixed asset journal that is used for depreciation transactions.
6. In the **Warehouse** field, select the warehouse for the transaction.
7. In the **Person in charge** field, select the identification code of the employee that the asset is issued to.
8. In the **Location** field, select the location of the asset.
9. Select **Lines**.
10. Create a journal line.
11. In the **Item** field, select the item code.
12. In the **Quantity** field, enter the item quantity.
13. In the **Type of rate** field, select the type of issue rate for the item.
14. In the **Resource** field, select the resource or resource group that is assigned to the item.

    > [!NOTE]
    > The **Lifetime** field is updated with the useful life of the item for the selected combination of the following details: item number, type of rate in the priority unit of the organization unit, job title of the employee, and type of work that the employee does.

15. On the **Product dimensions** tab, in the **Warehouse** field, select the warehouse where the item is located.
16. In the **Inventory profile** field, select the inventory profile for the item.
17. In the **Batch number** field, select the batch number of the item.
18. In the **Serial number** field, select the serial number of the item.
19. Close the page.
20. On the **Working clothes/Special rigging/NVFA issue journal** page, select **Validate** to validate the journal.
21. Select **FA journals** \> **FA journal (putting into operation)** to put the asset into operation.

    –or–

    Select **FA journals** \> **FA journal (depreciation)** to depreciate the asset.

20. Select **Close** to post the journal.

After you close a working clothes/special rigging/NVFA issue journal, you can print the **Working clothes issue sheet (No. MB-7)** report. To print this report, select **Print**\> **Working clothes issue sheet (No. MB-7)**.

To reverse the issue of the working clothes or special rigging item, on the **Working clothes/Special rigging/NVFA issue journal** page, select **Cancel issue**.

## Return working clothes or special rigging items to a warehouse 

1. Go to **Fixed assets (Russia)** \> **Common** \> **Working clothes**.

    –or–

    Go to **Fixed assets (Russia)** \> **Common** \> **Special rigging**.

2. Double-click an existing working clothes or special rigging item.
2. Select **Componentry** \> **Componentry**.
3. Select the fixed asset item or component that is required, and then select **Add to remains**.
4. In the **Quantity** field, enter the remaining quantity of the item.
5. Select **OK** to add the working clothes or special rigging item to item remainders. The lines that are marked in the upper pane of the **Componentry** page are moved to the lower pane.
6. In the lower pane, select **Calculating prices** to calculate the balance value, depreciation, and depreciated cost for each item that is returned. The calculations are based on the price calculation method that is selected.
7. Close the page.
8. Go to **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
9. Create a fixed asset journal.
10. In the **Name** field, select a journal name.
11. Select **Lines**.
12. Select **New** to open the **Add to journal** dialog box.
13. In the **Transaction date** field, select the transaction date.
14. In the **Transaction type** field, select **Disposal (dismantlement)**.
15. In the **FA inventory number** field, select the inventory number of the fixed asset.
16. Select **OK**. The value model lines for the asset record are created in the journal.
17. Select **Validate** \> **Validate** to validate the journal.
18. Select **Post** \> **Post** to post the journal.

## Additional resources

- [Not valuable fixed assets (NVFAs) (Russia)](rus-not-valuable-assets.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
