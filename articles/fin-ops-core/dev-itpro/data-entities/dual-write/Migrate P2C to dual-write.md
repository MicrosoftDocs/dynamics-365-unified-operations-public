---
# required metadata

title: Steps to migrate Prospect to cash data from Data Integrator to dual-write
description: This topic describes how to migrate the Prospect to Cash data from Data Integrator app to dual-write.
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

## Steps to migrate Prospect to cash data from Data Integrator to dual-write

[!include [banner](../../includes/banner.md)]

If you are looking for guidance to migrate your Prospect to Cash business functionality data from Data Integrator to dual-write, please use the following steps. 
 
Step 1: Run Prospect to Cash Data Integrator jobs for one final full sync so that the 2 systems (Finance and Operations apps and Customer Engagement apps) have all the data. 

Step 2: To avoid potential data loss, we suggest you to export the Prospect to Cash data from the Sales application as an excel or .csv file. Ideally you will be exporting data from the following entities.
-	Account
-	Products
-	Quote
-	Quote products
-	Order
-	Order products
-	Invoice 
-	Invoice products

Step 3: Un-install Prospect to Cash solution from the Sales machine. This step removes the fields and corresponding data introduced by the Prospect to Cash solution. 

Step 4: Install dual-write solution.

Step 5: Establish dual-write connection between Finance and Operations apps and Customer Engagement apps for one or more legal entities.

Step 6: Enable dual-write entity maps along with initial sync for the required reference data like customer group, payment terms, payment schedule etc. For entities that require bootstrapping like account, quote, quote line, order and order line, please do not enable the dual-write maps.

Step 7: In Customer Engagement apps, go to "Advanced Settings > System Settings > Data Management >  Duplicate detection rules" and disable all the rules. 

Step 8: Bootstrap the entities mentioned in Step 2 with the following data and import. 
 
## Account entity:
-	Fill the "Company" column with required company name. Say USMF.
-	On the "Relationship Type" column fill "Customer" as the static value. Note: You may have not want to classify every account record as a customer due to business reasons. 
-	Fill the "Customer Group Id" column with required customer group # from Finance and Operations apps. Out of the box, the Prospect to Cash solution defaults it to "10". But you may want to classify it correctly.
-	If you are using the Prospect to Cash solution without any customization on "Account Number", then fill the "Party Number" column with "Account Number" values. If there are any customizations and not sure about the  party number, then pull this information from Finance and Operations apps.
 
## Contact entity:
-	Fill the "Company" column with required company name. Say USMF.
-	Based on the "IsActiveCustomer" value found on the CSV file, please populate the following attributes on the Contact entity.
-	If "IsActiveCustomer"=Yes, then set "Sellable"=Yes. Also, fill the "Customer Group Id" column with required customer group # from Finance and Operations apps. Out of the box, the Prospect to Cash solution defaults it to "10". But you may want to classify it correctly.
-	If "IsActiveCustomer"=No, then set "Sellable"=No and "Contact For"="Customer".
-	If you are using the Prospect to Cash solution as is without any customization on "Contact Number", then 
-	We need to migrate the contact number from the CSV file (aka msdynce_contactnumber)) to Contact number on the contact entity (aka msdyn_contactnumber)
-	Fill the "Party Number" column with "Contact Number" values.
-	Fill the "Account Number/Contact Person ID" with "Contact Number" values.
 
## Products entity:
Since products are designed to flow one-way only i.e., Finance and Operations apps -> Customer Engagement apps, bootstrapping is not required. Do initial sync to bring all the required data from Finance and Operations apps to Customer Engagement apps.
 
## Order entity:
-	Fill the "Company" column with required company name. Say USMF.
-	Copy the "Order Id" column values from the CSV file and to populate it as "Sales Order Number" field.
-	Copy the "Customer" column values from the CSV file to populate the "Invoice customer number" field.
-	Copy the "Ship To Country/Region" value from CSV file to "Ship To Country/Region". Say for example "US" or "United States".
-	Make sure to fill the "Requested Receipt Date". If you were not using any, then you need to make it based on "Requested Delivery Date" or "Date Fulfilled" or "Date Submitted" found on the CSV file. Say for example, "2020-03-27T00:00:00Z",
-	Make sure to set the "Language". Say for example "en-us".
-	Make sure to set "Order Type" as "Item-based".
 
## Order product entity:
-	Fill the "Company" column with required company name. Say USMF.
 
## Invoice entity:
Since invoice records are designed to flow one-way only i.e., Finance and Operations apps -> Customer Engagement apps, bootstrapping is not required. Do initial sync to bring all the required data from Finance and Operations apps to Customer Engagement apps.
 
Quote and Quote product should be same as Order.
 
Step 9: Come to Finance and Operations apps and enable the entity maps like account, quote, quote line, order and order line. Make sure you run the initial sync. This will bring additional information from Finance and Operations apps like the processing status, shipping and billing addresses, sites and warehouse etc.  

