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

