---
title: Migrate Prospect to cash data from Data Integrator to dual-write
description: Learn how to migrate Prospect to Cash data from Data Integrator to dual-write, a step-by-step list of how to migrate this data.
author: RamaKrishnamoorthy
ms.author: ramasri
ms.topic: article
ms.date: 02/01/2022
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: global
ms.search.validFrom: 2020-01-26
---

# Migrate Prospect to cash data from Data Integrator to dual-write

[!include [banner](../../includes/banner.md)]

The Prospect to cash solution available for Data Integrator is not compatible with dual-write. The reason for this is the msdynce_AccountNumber index on the account table that came as part of the Prospect to cash solution. If this index exists, you cannot create the same customer account number in two different legal entities. You can either choose to start fresh with dual-write by migrating the Prospect to cash data from Data Integrator to dual-write or you can install the last "dorman" version of the Prospect to cash solution. This article covers both of these approaches.

## Install the last "dorman" version of the Data Integrator Prospect to cash solution

**P2C Version 15.0.0.2** is considered the last "dorman" version of the data integrator Prospect to cash solution. You can download it from [FastTrack for Dynamics 365](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/Dual-write/P2C).

You need to install it manually. After installation, everything remains exactly the same, except the msdynce_AccountNumber index is removed.

## Steps to migrate Prospect to cash data from Data Integrator to dual-write

To migrate your Prospect to cash data from Data Integrator to dual-write, follow these steps.

1. Run the Prospect to cash Data Integrator jobs to do one final full synchronization. In this way, you ensure that both systems (finance and operations apps and customer engagement apps) have all the data.
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
5. Create a dual-write connection between the finance and operations app and the customer engagement app for one or more legal entities.
6. Enable dual-write table maps, and run the initial synchronization for the required reference data. (For more information, see [Considerations for initial synchronization](initial-sync-guidance.md).) Examples of required data include customer groups, payment terms, and payment schedules. Don't enable the dual-write maps for tables that require initialization, such as the account, quote, quote line, order, and order line tables.
7. In the customer engagement app, go to **Advanced Settings \> System Settings \> Data Management \> Duplicate detection rules**, and disable all the rules.
8. Initialize the tables that are listed in step 2. For instructions, see the remaining sections of this article.
9. Open the finance and operations app, and enable the table maps, such as the account, quote, quote line, order, and order line table maps. Then run the initial synchronization. (For more information, see [Considerations for initial synchronization](initial-sync-guidance.md).) This process will sync additional information from the finance and operations app, such as processing status, shipping and billing addresses, sites, and warehouses.

## Account table

1. In the **Company** column, enter the company name, such as **USMF**.
2. In the **Relationship Type** column, enter **Customer** as a static value. You might not want to classify every account record as a customer in your business logic.
3. In the **Customer Group ID** column, enter the customer group number from the finance and operations app. The default value from the Prospect to cash solution is **10**.
4. If you're using the Prospect to cash solution without any customization of **Account Number**, enter an **Account Number** value in the **Party Number** column. If there are customizations, and you don't know the party number, pull this information from the finance and operations app.

## Contact table

1. In the **Company** column, enter the company name, such as **USMF**.
2. Set the following columns, based on the **IsActiveCustomer** value in the CSV file:

    - If **IsActiveCustomer** is set to **Yes** in the CSV file, set the **Sellable** column to **Yes**. In the **Customer Group ID** column, enter the customer group number from the finance and operations app. The default value from the Prospect to cash solution is **10**.
    - If **IsActiveCustomer** is set to **No** in the CSV file, set the **Sellable** column to **No**, and set the **Contact For** column to **Customer**.

3. If you're using the Prospect to cash solution without any customization of **Contact Number**, set the following columns:

    - Migrate the contact number from the CSV file (**msdynce\_contactnumber**) to the contact number in the **Contact** table (**msdyn\_contactnumber**).
    - Use values from the **Contact Number** table in the **Party Number** column.
    - Use values from the **Contact Number** table in the **Account Number/Contact Person ID** column.

## Invoice table

Because data from the **Invoice** table is designed to flow one way, from the finance and operations app to the customer engagement app, initialization isn't required. Run the initial synchronization to migrate all the required data from the finance and operations app to the customer engagement app. For more information, see [Considerations for initial synchronization](initial-sync-guidance.md).

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

Because data from the **Products** table is designed to flow one way, from the finance and operations app to the customer engagement app, initialization isn't required. Run the initial synchronization to migrate all the required data from the finance and operations app to the customer engagement app. For more information, see [Considerations for initial synchronization](initial-sync-guidance.md).

## Quote and Quote product tables

For the **Quote** table, follow the instructions in the [Order table](#order-table) section earlier in this article. For the **Quote product** table, follow the instructions in the [Order products table](#order-products-table) section.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

