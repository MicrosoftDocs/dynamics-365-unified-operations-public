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
Use this procedure to relate an item or an item group to a fixed asset (FA) group. You can use the following forms to set up an item relation with a fixed asset group:

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

## Set up types of issue and usage rates
Use the **Types of issue and usage rates** form to define the types of issue and usage rates that determine which working clothes and special rigging are issued to employees.

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Working clothes/Special riggings/NVFA** \> **Type of rate**.

2.  In the **Type of rate** field, enter the identification code for the rate type.

3.  In the **Description** field, enter a short description for the rate type.

4.  Select the **Over-rate** check box to indicate that quantity control of the item issue by the defined rate is not required for the specified rate type.
    
    > [!NOTE]
    > <P>If this check box is selected, the rate type is used only to specify the wear or usage period of an asset.</P>


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

