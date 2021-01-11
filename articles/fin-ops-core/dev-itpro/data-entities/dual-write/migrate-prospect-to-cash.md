---
# required metadata

title: Migrate Prospect to cash data from Data Integrator to dual-write
description: This topic describes how to migrate the Prospect to Cash data from Data Integrator to dual-write.
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

To migrate your Prospect to cash data from Data Integrator to dual-write, follow these steps:

1. Run Prospect to cash Data Integrator jobs for one final full synchronization so that both systems (Finance and Operations apps and customer engagement apps) have all the data.

2. To avoid potential data loss, export the Prospect to cash data from the Dynamics 365 Sales to an Excel or .csv file. Export data from the following entities:

    - [Account](#account-table)
    - [Contact](#contact-table)
    - [Invoice](#invoice-table)
    - Invoice products
    - [Order](#order-table)
    - [Order products](#order-products-table)
    - [Products](#products-table)
    - [Quote](#quote-and-quote-product-tables)
    - [Quote products](#quote-and-quote-product-tables)

3. Uninstall the Prospect to cash solution from the Sales environment. This step removes the columns and corresponding data introduced by the Prospect to cash solution.

4. Install the dual-write solution.

5. Create a dual-write connection between the Finance and Operations app and the customer engagement app for one or more legal entities.

6. Enable dual-write table maps, and run the initial sync for the required reference data. Examples of required data are customer group, payment terms, and payment schedule. For tables that require initialization, for example, account, quote, quote line, order, and order line, do not enable the dual-write maps.

7. In the customer engagement app, go to **Advanced Settings > System Settings > Data Management >  Duplicate detection rules** and disable all the rules.

8. Initialization the tables listed in Step 2, according to the following sections.

9. Open the Finance and Operations app and enable the table maps, for example, account, quote, quote line, order, and order line. Run the initial synchronization. This process will sync additional information from the Finance and Operations app, for example, processing status, shipping and billing addresses, sites, and warehouses.

## Account table

1. Enter the company name in the**Company** column, for example, **USMF**.
2. In the **Relationship Type** column, enter **Customer** as a static value. You may not want to classify every account record as a customer in your business logic.
3. Enter the customer group number from the Finance and Operations app in the **Customer Group ID** column. The Prospect to cash solution defaults **10**.
4. If you are using the Prospect to cash solution without any customization of **Account Number**, then enter an **Account Number** value in the **Party Number** column. If there are customizations and you don't know the party number, then pull this information from the Finance and Operations app.

## Contact table

1. Enter the company name in the**Company** column, for example, **USMF**.

2. Based on the **IsActiveCustomer** value found on the .csv file, populate the following columns in the **Contact** table.

    - If **IsActiveCustomer** is **Yes**, then set **Sellable** to **Yes**. Enter the customer group number from the Finance and Operations app in **Customer Group ID** column. The Prospect to cash solution defaults **10**.
    - If **IsActiveCustomer** is **No**, then set **Sellable** to **NO** and set **Contact For** to **Customer**.

3. If you are using the Prospect to cash solution as is without any customization on **Contact Number**, then set these columns:

    - Migrate the contact number from the .csv file (**msdynce_contactnumber**) to the contact number on the **Contact** table (**msdyn_contactnumber**).
    - Use values from the **Contact Number** table in the **Party Number** column.
    - Use values from the **Contact Number** table in the **Account Number/Contact Person ID** column.

## Invoice table

Because data from the **Invoice** table is designed to flow one way, from the Finance and Operations app to the customer engagement app, initialization isn't required. Run the initial sync to migrate all the required data from the Finance and Operations app to the customer engagement app.

## Order table

1. Enter the company name in the**Company** column, for example, **USMF**.
2. Copy the **Order ID** column value from the .csv file and to populate the  **Sales Order Number** column.
3. Copy the  **Customer** column value from the .csv file to populate the  **Invoice customer number** column.
4. Copy the **Ship To Country/Region** value from .csv file to the **Ship To Country/Region** column. Examples include **US** and **United States**.
5. Set the **Requested Receipt Date** column. If you are not using a receipt date, then use the **Requested Delivery Date**, **Date Fulfilled**, **Date Submitted** columns from the .csv file. An example is **2020-03-27T00:00:00Z**.
6. Set the **Language** column. An example is **en-us**.
7. Set the **Order Type** using the **Item-based** column.

## Order products table

1. Enter the company name in the**Company** column, for example, **USMF**.

## Products table

Because data from the **Products** table is designed to flow one way, from the Finance and Operations app to the customer engagement app, initialization isn't required. Run the initial sync to migrate all the required data from the Finance and Operations app to the customer engagement app.

## Quote and Quote product tables

Follow the instructions for the [Order table](#order-table) and [Order products table](#order-products-table).
