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

## Migrate Prospect to cash data from Data Integrator to dual-write

[!include [banner](../../includes/banner.md)]

To migrate your Prospect to cash data from Data Integrator to dual-write, follow these steps:

1. Run Prospect to cash Data Integrator jobs for one final full synchronization so that both systems (Finance and Operations apps and customer engagement apps) have all the data.

2. To avoid potential data loss, export the Prospect to cash data from the Dynamics 365 Sales to an Excel or .csv file. Export data from the following entities:

    - [Account](#account-table)
    - [Products](#products-table)
    - [Quote]
    - [Quote products]
    - [Order](#order-table)
    - [Order products](#order-products-table)
    - [Invoice](#invoice-table)
    - [Invoice products]

3. Uninstall the Prospect to cash solution from the Sales environment. This step removes the columns and corresponding data introduced by the Prospect to cash solution.

4. Install the dual-write solution.

5. Create a dual-write connection between the Finance and Operations app and the customer engagement app for one or more legal entities.

6. Enable dual-write table maps, and run the initial sync for the required reference data. Examples of required data are customer group, payment terms, and payment schedule. For tables that require bootstrapping, for example, account, quote, quote line, order, and order line, do not enable the dual-write maps.

7. In the customer engagement app, go to **Advanced Settings > System Settings > Data Management >  Duplicate detection rules** and disable all the rules.

8. Bootstrap the tables listed in Step 2, according to the following sections.

## Account table

1. Fill the **Company** column with required company name, for example, **USMF**.
2. On the "Relationship Type" column fill "Customer" as the static value. Note: You may have not want to classify every account record as a customer due to business reasons.
3. Fill the "Customer Group Id" column with required customer group # from Finance and Operations apps. Out of the box, the Prospect to Cash solution defaults it to "10". But you may want to classify it correctly.
4. If you are using the Prospect to Cash solution without any customization on "Account Number", then fill the "Party Number" column with "Account Number" values. If there are any customizations and not sure about the  party number, then pull this information from Finance and Operations apps.

## Contact table

1. Fill the "Company" column with required company name. Say USMF.
2. Based on the "IsActiveCustomer" value found on the CSV file, please populate the following attributes on the Contact entity.
3. If "IsActiveCustomer"=Yes, then set "Sellable"=Yes. Also, fill the "Customer Group Id" column with required customer group # from Finance and Operations apps. Out of the box, the Prospect to Cash solution defaults it to "10". But you may want to classify it correctly.
4. If "IsActiveCustomer"=No, then set "Sellable"=No and "Contact For"="Customer".
5. If you are using the Prospect to Cash solution as is without any customization on "Contact Number", then
6. We need to migrate the contact number from the CSV file (aka msdynce_contactnumber)) to Contact number on the contact entity (aka msdyn_contactnumber)
7. Fill the "Party Number" column with "Contact Number" values.
8. Fill the "Account Number/Contact Person ID" with "Contact Number" values.

## Products table

Since products are designed to flow one-way only i.e., Finance and Operations apps -> Customer Engagement apps, bootstrapping is not required. Do initial sync to bring all the required data from Finance and Operations apps to Customer Engagement apps.

## Order table

1. Fill the "Company" column with required company name. Say USMF.
2. Copy the "Order Id" column values from the CSV file and to populate it as "Sales Order Number" field.
3. Copy the "Customer" column values from the CSV file to populate the "Invoice customer number" field.
4. Copy the "Ship To Country/Region" value from CSV file to "Ship To Country/Region". Say for example "US" or "United States".
5. Make sure to fill the "Requested Receipt Date". If you were not using any, then you need to make it based on "Requested Delivery Date" or "Date Fulfilled" or "Date Submitted" found on the CSV file. Say for example, "2020-03-27T00:00:00Z",
6. Make sure to set the "Language". Say for example "en-us".
7. Make sure to set "Order Type" as "Item-based".

## Order products table

- Fill the "Company" column with required company name. Say USMF.

## Invoice table

Since invoice records are designed to flow one-way only i.e., Finance and Operations apps -> Customer Engagement apps, bootstrapping is not required. Do initial sync to bring all the required data from Finance and Operations apps to Customer Engagement apps.

Quote and Quote product should be same as Order.

Step 9: Come to Finance and Operations apps and enable the entity maps like account, quote, quote line, order and order line. Make sure you run the initial sync. This will bring additional information from Finance and Operations apps like the processing status, shipping and billing addresses, sites and warehouse etc.

