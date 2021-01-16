---
# required metadata

title: Migrate Prospect to cash data from Data Integrator to dual-write
description: This topic describes how to migrate Prospect to Cash data from Data Integrator to dual-write.
author: RamaKrishnamoorthy
manager: AnnBe
ms.date: 01/04/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form:
# ROBOTS:
audience: Application User, IT Pro
# ms.devlang:
ms.reviewer: rhaertle
# ms.tgt_pltfrm:
ms.custom:
ms.assetid:
ms.search.region: global
ms.search.industry:
ms.author: ramasri
ms.dyn365.ops.version:
ms.search.validFrom: 2021-01-04

---

# Migrate Prospect to cash data from Data Integrator to dual-write

[!include [banner](../../includes/banner.md)]

To migrate your Prospect to cash data from Data Integrator to dual-write, follow these steps.

1. Run the Prospect to cash Data Integrator jobs to do one final full synchronization. In this way, you ensure that both systems (Finance and Operations apps and customer engagement apps) have all the data.
2. To help prevent potential data loss, export the Prospect to cash data from Microsoft Dynamics 365 Sales to an Excel file or a comma-separated values (CSV) file. Export data from the following entities:

    - [Account](#account-table)
    - [Contact](#contact-table)
    - [Invoice](#invoice-table)
    - Invoice products
    - [Order](#order-table)
    - [Order products](#order-products-table)
    - [Products](#products-table)
    - [Quote](#quote-and-quote-product-tables)
    - [Quote products](#quote-and-quote-product-tables)

3. Uninstall the Prospect to cash solution from the Sales environment. This step removes the columns and corresponding data that the Prospect to cash solution introduced.
4. Install the dual-write solution.
5. Create a dual-write connection between the Finance and Operations app and the customer engagement app for one or more legal entities.
6. Enable dual-write table maps, and run the initial synchronization for the required reference data. (For more information, see [Considerations for initial synchronization](initial-sync-guidance.md).) Examples of required data include customer groups, payment terms, and payment schedules. Don't enable the dual-write maps for tables that require initialization, such as the account, quote, quote line, order, and order line tables.
7. In the customer engagement app, go to **Advanced Settings \> System Settings \> Data Management \> Duplicate detection rules**, and disable all the rules.
8. Initialize the tables that are listed in step 2. For instructions, see the remaining sections of this topic.
9. Open the Finance and Operations app, and enable the table maps, such as the account, quote, quote line, order, and order line table maps. Then run the initial synchronization. (For more information, see [Considerations for initial synchronization](initial-sync-guidance.md).) This process will sync additional information from the Finance and Operations app, such as processing status, shipping and billing addresses, sites, and warehouses.

## Account table

1. In the **Company** column, enter the company name, such as **USMF**.
2. In the **Relationship Type** column, enter **Customer** as a static value. You might not want to classify every account record as a customer in your business logic.
3. In the **Customer Group ID** column, enter the customer group number from the Finance and Operations app. The default value from the Prospect to cash solution is **10**.
4. If you're using the Prospect to cash solution without any customization of **Account Number**, enter an **Account Number** value in the **Party Number** column. If there are customizations, and you don't know the party number, pull this information from the Finance and Operations app.

## Contact table

1. In the **Company** column, enter the company name, such as **USMF**.
2. Set the following columns, based on the **IsActiveCustomer** value in the CSV file:

    - If **IsActiveCustomer** is set to **Yes** in the CSV file, set the **Sellable** column to **Yes**. In the **Customer Group ID** column, enter the customer group number from the Finance and Operations app. The default value from the Prospect to cash solution is **10**.
    - If **IsActiveCustomer** is set to **No** in the CSV file, set the **Sellable** column to **No**, and set the **Contact For** column to **Customer**.

3. If you're using the Prospect to cash solution without any customization of **Contact Number**, set the following columns:

    - Migrate the contact number from the CSV file (**msdynce\_contactnumber**) to the contact number in the **Contact** table (**msdyn\_contactnumber**).
    - Use values from the **Contact Number** table in the **Party Number** column.
    - Use values from the **Contact Number** table in the **Account Number/Contact Person ID** column.

## Invoice table

Because data from the **Invoice** table is designed to flow one way, from the Finance and Operations app to the customer engagement app, initialization isn't required. Run the initial synchronization to migrate all the required data from the Finance and Operations app to the customer engagement app. For more information, see [Considerations for initial synchronization](initial-sync-guidance.md).

## Order table

1. In the **Company** column, enter the company name, such as **USMF**.
2. Copy the value of the **Order ID** column in the CSV file to the **Sales Order Number** column.
3. Copy the value of the **Customer** column in the CSV file to the **Invoice customer number** column.
4. Copy the value of the **Ship To Country/Region** column in the CSV file to the **Ship To Country/Region** column. Examples of this value include **US** and **United States**.
5. Set the **Requested Receipt Date** column. If you aren't using a receipt date, use the **Requested Delivery Date**, **Date Fulfilled**, and **Date Submitted** columns in the CSV file. An example of this value is **2020-03-27T00:00:00Z**.
6. Set the **Language** column. An example of this value is **en-us**.
7. Set the **Order Type** column by using the **Item-based** column.

## Order products table

- In the **Company** column, enter the company name, such as **USMF**.

## Products table

Because data from the **Products** table is designed to flow one way, from the Finance and Operations app to the customer engagement app, initialization isn't required. Run the initial synchronization to migrate all the required data from the Finance and Operations app to the customer engagement app. For more information, see [Considerations for initial synchronization](initial-sync-guidance.md).

## Quote and Quote product tables

For the **Quote** table, follow the instructions in the [Order table](#order-table) section earlier in this topic. For the **Quote product** table, follow the instructions in the [Order products table](#order-products-table) section.
